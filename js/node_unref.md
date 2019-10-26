<header class="l-site-header">

<div class="masthead">[Ben Nadel](/index.cfm "Ben Nadel on User Experience (UX), JavaScript, ColdFusion, Node.js, Life, and Love.")

<div class="tagline">On User Experience (UX) Design, JavaScript, ColdFusion, Node.js, Life, and Love.</div>

</div>

<nav class="active-blog">[Navigation:](#primary-navigation)

*   [Home](/blog/recent-blog-entries.htm "Ben Nadel's Blog On Obsessively Thorough Web Application Development.")
*   [Projects](/projects/overview.htm "Ben Nadel's open source web development projects.")
*   [About Me](/about/about-ben-nadel.htm "Learn more about Ben Nadel, Co-founder of InVision App, Inc.")
*   [Contact](/contact/contact-ben-nadel.htm "Contact Ben Nadel for any web development consutling.")
*   [People](/people/who-rock-my-world.htm "The amazing people who rock Ben Nadel's world on the daily!")
*   [InVision](/invision/co-founder.htm "Ben Nadel is the co-founder of InVision App, Inc.")
*   [RSS](/index.cfm?event=blog.rss "The BenNadel.com RSS feed.")

</nav>

<figure>![Ben Nadel at cf.Objective() 2009 (Minneapolis, MN) with: Terrence Ryan](/images/header/photos/terrence_ryan.jpg)

<figcaption>Ben Nadel at cf.Objective() 2009 (Minneapolis, MN) with: <span class="person">[Terrence Ryan](http://www.terrenceryan.com/) ( [@tpryan](https://twitter.com/tpryan) )</span></figcaption>

</figure>

</header>

<div id="site-content" class="l-site-body">

<div class="l-site-content content">

<article id="blog-post" data-id="3301" data-gist-id="998aa3f30e50e88b5311f49dad3e0831">

<header class="m-post-header">

# Calling Timeout.unref() With setTimeout() Does Not Appear To Be A Best Practice In Node.js

<div class="meta">By [Ben Nadel](https://plus.google.com/108976367067760160494?rel=author "Author: Ben Nadel on Google+") on <time datetime="2017-07-12">July 12, 2017</time></div>

<div class="tags">Tags: [Javascript / DHTML](/blog/tags/6-javascript-dhtml-blog-entries.htm)</div>

</header>

When I was [building my Node.js Circuit Breaker](/blog/3299-building-a-circuit-breaker-for-node-js.htm), I spent a lot of time looking at existing Circuit Breaker implementations to see how different people approached the problem. And, as I was digging through source code, I consistently came across something that I had never seen before: developers were calling .unref() on the timeout object returned by setTimeout(). Since this was showing up in a number of Circuit Breaker implementations, I assumed it was a "best practice" but, I didn't understand it. So, I started looking into the .unref() functionality. And, from what I can tell, there doesn't appear to be any reason to consider this a "best practice". In fact, there's reason to think that this is a bad practice.

<table border="0" cellpadding="0" cellspacing="0" class="imageborder" width="100%">

<tbody>

<tr>

<td rowspan="3" width="50%">  
</td>

<td class="nw">   
</td>

<td class="n">   
</td>

<td class="ne">   
</td>

<td rowspan="3" width="50%">  
</td>

</tr>

<tr>

<td class="w">   
</td>

<td class="c"><iframe src="//player.vimeo.com/video/225239928?color=ff0179" width="700" height="394" frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen=""></iframe></td>

<td class="e">   
</td>

</tr>

<tr>

<td class="sw">   
</td>

<td class="s">   
</td>

<td class="se">   
</td>

</tr>

</tbody>

</table>

If you've never seen the .unref() method before - as I had not - it's a way to tell Node.js not to hold the current process open if the given timer is the only thing left to execute on the event-loop queue. To see this in action, we can set up a trivial example that does nothing but initiate a setTimeout() call and then .unref() it:

<div class="code" data-gist-filename="test.js">

*   console.log( "App started." );

*   var timer = setTimeout(
*   function timeoutCallback() {

*   console.log( "Timer callback." );

*   },
*   1000
*   );

*   // At this point, the timer is the only action that would hold the node-process open. By
*   // unref-ing it, the process will exit prior to the timeout callback execution and we
*   // should never see the second console.log() statement.
*   timer.unref();

</div>

As you can see, our setTimeout() will log a message to the console. But, we immediately .unref() the timeout object after it has been created. This tells Node.js to exit out of the process (in this demo) if the timeout is the only pending operation. And, since it is, we get the following terminal output:

<table border="0" cellpadding="0" cellspacing="0" class="imageborder" width="100%">

<tbody>

<tr>

<td rowspan="3" width="50%">  
</td>

<td class="nw">   
</td>

<td class="n">   
</td>

<td class="ne">   
</td>

<td rowspan="3" width="50%">  
</td>

</tr>

<tr>

<td class="w">   
</td>

<td class="c"> ![Using Timeout.unref() with setTimeout().](/resources/uploads/2017/set-timeout-unref-test.png)</td>

<td class="e">   
</td>

</tr>

<tr>

<td class="sw">   
</td>

<td class="s">   
</td>

<td class="se">   
</td>

</tr>

</tbody>

</table>

As you can see, we never see the logging statement performed from within the setTimeout() callback since it is never executed. Once we .unref() the timer, Node.js no longer needs to hold the process open (waiting for the timer to execute), and it quietly exits.

If you're unfamiliar with the concept of Circuit Breakers, they are essentially proxies to brittle resources that will "fail fast" (ie, prevent communication) if the given resource appears to be unhealthy. This is very much like the physical Circuit Breaker that you have in your home's electrical system. In a Circuit Breaker context, this .unref() call was being used in conjunction with the setTimeout() timer that will reject a long-running command passing through the Circuit Breaker. Across the various implementations that I investigated, the approach looked like some variation of the following:

<div class="code" data-gist-filename="breaker.js">

*   // Require the application modules.
*   var api = require( "./api" );

*   // ----------------------------------------------------------------------------------- //
*   // ----------------------------------------------------------------------------------- //

*   var TEN_SECONDS = ( 10 * 1000 );

*   function runWithTimeout( command, timeout = TEN_SECONDS ) {

*   // Since we can't cancel a command once it has been executed, we have to
*   // conditionally turn a command into either a resolved or a rejected promise. In
*   // this case, we'll use a timer to generate a rejected promise prior to command
*   // completion if the command takes too long to return.
*   var promise = new Promise(
*   function( resolve, reject ) {

*   // Setup our rejection timer to preemptively kill hanging commands.
*   var timer = setTimeout(
*   function rejectHangingCommand() {

*   reject( new Error( "Command took too long (and was timed-out)." ) );

*   },
*   timeout
*   );

*   // ************************************************************** //
*   // ************************************************************** //
*   // CAUTION: This is the line that seemingly makes no sense (to me).
*   // I cannot figure out what purpose it actually serves.
*   timer.unref();
*   // ************************************************************** //
*   // ************************************************************** //

*   // Catch any synchronous execution errors.
*   try {

*   var commandPromise = Promise.resolve( command() );

*   } catch ( error ) {

*   var commandPromise = Promise.reject( error );
*   }

*   // Once the command returns, we need to use the result to fulfill the
*   // contextual Promise. However, the command may return before OR after the
*   // timeout has already rejected the contextual Promise. As such, the
*   // following operations may actually be No-Op instructions.
*   commandPromise.then(
*   function handleResolve( result ) {

*   clearTimeout( timer );
*   resolve( result );

*   },
*   function handleReject( error ) {

*   clearTimeout( timer );
*   reject( error );

*   }
*   );

*   }
*   );

*   return( promise );

*   }

*   // ----------------------------------------------------------------------------------- //
*   // ----------------------------------------------------------------------------------- //

*   // Run the command with a 1-Second timeout. Since our command will take 5-Seconds to
*   // execute, we know that the command-runner's timer will terminate the request early.
*   var promise = runWithTimeout(
*   function command() {

*   return( api.echoAfterTimeout( "[data payload]", 5000 ) );

*   },
*   1000
*   );

*   promise.then(
*   function handleResolve( result ) {

*   console.log( "Success:", result );

*   },
*   function handleReject( error ) {

*   console.log( "Error:", error );

*   }
*   );

</div>

As you can see, right after we initiate the rejectHangingCommand() timer, we're calling .unref() on it. This is the line of code that makes no sense to me (and is the entire point of this post). That said, when we try to run a 5-second command through a 1-second execution, we get the following output:

<table border="0" cellpadding="0" cellspacing="0" class="imageborder" width="100%">

<tbody>

<tr>

<td rowspan="3" width="50%">  
</td>

<td class="nw">   
</td>

<td class="n">   
</td>

<td class="ne">   
</td>

<td rowspan="3" width="50%">  
</td>

</tr>

<tr>

<td class="w">   
</td>

<td class="c"> ![Using Timeout.unref() with a Circuit Breaker doesn't appear to make any sense.](/resources/uploads/2017/set-timeout-unref-breaker.png)</td>

<td class="e">   
</td>

</tr>

<tr>

<td class="sw">   
</td>

<td class="s">   
</td>

<td class="se">   
</td>

</tr>

</tbody>

</table>

As you can see, our 5-second API request is being preemptively timed-out by our 1-second setTimeout() call.

So, what purpose is the .unref() method playing in our Circuit Breaker?

Well, first, let's look at the Node.js document on Timers. If we look at [the .unref() explanation](https://nodejs.org/api/timers.html#timers_timeout_unref), there is a clear warning that calling .unref() should be consumed with caution:

**Note**: Calling timeout.unref() creates an internal timer that will wake the Node.js event loop. Creating too many of these can adversely impact performance of the Node.js application.

So, immediately, the Node.js documentation warns us that we should take caution when using the timeout.unref() feature. Which means that we-developers better have a really good reason for using .unref() in our Circuit Breaker code (or other such inspired code). But, I'm struggling to think of a good reason. In fact, I can only thing of reasons that .unref() seems silly.

For starters, the underlying Promise may still hold the process open. If you look back at the previous terminal output, you can see the 1-Second timeout; but, you can also see that the underlying API call still returns after 5-Seconds. As such, a long-running command will hold the process open longer than its sibling timeout.

Of course, if the command is resolved prior to the 1-Second timeout, we clear the pending timer both for Resolution and Rejection outcomes. As such, the timer will never hold the process open longer that the command execution itself, whether it's long-running or short-lived.

Now, let's say for the sake of argument that something deep down inside the command goes "wrong" and an uncaught exception is thrown or an unhandled Promise rejection occurs. In that case, it is common - [for reasons that still elude me](/blog/3253-as-a-node-js-novice-i-don-t-understand-why-uncaught-exceptions-are-so-dangerous.htm) - for a Node.js application to the log the error and terminate the running process. In such cases, it doesn't matter if there are pending timers - an explicit call to exit the process will take precedent.

Which brings up the greater context of the application itself. Circuit Breakers make sense inside applications. They operate based on metrics that are collected over time. So, it really only makes sense to use them inside long-running contexts. As such, a Circuit Breaker will generally be used in conjunction with something like an Express.js or Koa application that will be holding the process open regardless of what the Circuit Breaker is doing with its internal timers.

Of course, you may be in a clustered Express.js application and need to disconnect a Worker thread from the Master cluster. If we assume that something somewhere goes wrong and a Circuit Breaker timer is somehow left running, does it really matter? In a few seconds, the timer will execute its callback and the Worker thread will be allowed to die.

_**NOTE**: I don't really know all that much about clustering and disconnecting Worker threads. As such, the preceding paragraph may not be entirely accurate._

Now, I'm not saying that Timeout.unref() has no place in a Node.js application. I can certainly understand a situation in which a long-running timeout or an internval on a message queue consumer (for example) shouldn't hold a process open. But, this feels more like the exception than the rule. I may very well be missing something; but, I can't think of any reason why .unref() would be meaningful in most contexts (especially Circuit Breakers). And, considering the warning in the Node.js documentation, calling .unref() may have a detrimental affect on the application performance.

<div class="m-tweet-this">[<span class="label">Tweet This</span> <span class="message">Great article by @BenNadel - Calling Timeout.unref() With setTimeout() Does Not Appear To Be A Best Practice In Node.js</span>](https://twitter.com/intent/tweet?text=Great%20article%20by%20%40BenNadel%20%2D%20Calling%20Timeout%2Eunref%28%29%20With%20setTimeout%28%29%20Does%20Not%20Appear%20To%20Be%20A%20Best%20Practice%20In%20Node%2Ejs%20http%3A%2F%2Fbjam%2Ein%2F3301) <span class="thanks">Woot woot — **you rock the party that rocks the body!**</span></div>

<aside class="m-related-posts">

### Enjoyed This? You Might Also Enjoy Reading:

*   [Building A Circuit Breaker For Node.js](/blog/3299-building-a-circuit-breaker-for-node-js.htm)
*   [You Can Continue To Process An Express.js Request After The Client Response Has Been Sent](/blog/3275-you-can-continue-to-process-an-express-js-request-after-the-client-response-has-been-sent.htm)
*   [As A Node.js Novice, I Don't Understand Why Uncaught Exceptions Are So Dangerous](/blog/3253-as-a-node-js-novice-i-don-t-understand-why-uncaught-exceptions-are-so-dangerous.htm)
*   [Logging And Debugging Unhandled Promise Rejections In Node.js v1.4.1 And Later](/blog/3238-logging-and-debugging-unhandled-promise-rejections-in-node-js-v1-4-1-and-later.htm)

</aside>

<section class="m-comments">

## Reader Comments

<div class="comments-disabled">

<div class="reason"><span>Oh my chickens, this post is old!</span></div>

<div class="follow-up">[_Hit me up on Twitter_ if you want to discuss it further.](https://twitter.com/BenNadel "Ben Nadel's Twitter Account")</div>

</div>

</section>

</article>

</div>

<div class="l-site-aside">

<div class="m-invision-ad">[UX Prototyping Made Beautiful - Create Interactive Wireframes & High Fidelity Prototypes](https://www.invisionapp.com?source=bennadel.com&ad=large "UX Prototyping Made Beautiful - Create Interactive Wireframes & High Fidelity Prototypes")</div>

<div class="m-epicenter-ad">[We Design & Build Apps. We build intelligent user experiences that bring your ideas to life.](https://www.epicenterconsulting.com/coldfusion?utm_source=bennadel.com "Epicenter is a web application development company that combines industry-leading web application design expertise with proven business acumen to transform the way our clients do business.")</div>

</div>

</div>

<footer class="l-site-footer"><small><span class="copyright">Ben Nadel © 2019\. All content is the property of Ben Nadel and BenNadel.com.</span> [Back to Top](#body)</small>

<section class="epilogue">

<div class="mini-resume">

<div class="avatar">![Ben Nadel's avatar.](/images/global/ben-nadel-avatar.jpg "Ben Nadel is co-founder of InVision App, Inc. and a passionate web-applications developer.")</div>

<div class="title">About Ben Nadel</div>

<div class="bio">I am the co-founder and lead engineer at InVision App, Inc — the world's leading prototyping, collaboration & workflow platform. I also rock out in JavaScript and ColdFusion 24x7 and I dream about promise resolving asynchronously.</div>

<div class="social-media">[GitHub](https://github.com/BenNadel "Follow Ben Nadel on GitHub.")  |  [Twitter](https://www.twitter.com/BenNadel "Follow Ben Nadel on Twitter.")  |  [LinkedIn](https://www.linkedin.com/in/BenNadel "Follow Ben Nadel on LinkedIn.")  |  [Google+](https://plus.google.com/108976367067760160494?rel=author "Follow Ben Nadel on Google Plus.")  |  [Facebook](https://www.facebook.com/BenNadel "Follow Ben Nadel on Facebook.")</div>

</div>

</section>

</footer>

<script type="text/javascript">(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m) })(window,document,'script','//www.google-analytics.com/analytics.js','ga'); ga('create', 'UA-477521-1', 'auto'); ga('send', 'pageview');</script>
