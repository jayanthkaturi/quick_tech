 Intra-Query Parallel Deadlock | Krishnakumar's SQL Server Blog                            /\* <!\[CDATA\[ \*/ function addLoadEvent(func) { var oldonload = window.onload; if (typeof window.onload != 'function') { window.onload = func; } else { window.onload = function () { oldonload(); func(); } } } /\* \]\]> \*/   window.\_wpemojiSettings = {"baseUrl":"https:\\/\\/s0.wp.com\\/wp-content\\/mu-plugins\\/wpcom-smileys\\/twemoji\\/2\\/72x72\\/","ext":".png","svgUrl":"https:\\/\\/s0.wp.com\\/wp-content\\/mu-plugins\\/wpcom-smileys\\/twemoji\\/2\\/svg\\/","svgExt":".svg","source":{"concatemoji":"https:\\/\\/s1.wp.com\\/wp-includes\\/js\\/wp-emoji-release.min.js?m=1572020829h&ver=5.3-beta2-46380"}}; !function(e,a,t){var r,n,o,i,p=a.createElement("canvas"),s=p.getContext&&p.getContext("2d");function c(e,t){var a=String.fromCharCode;s.clearRect(0,0,p.width,p.height),s.fillText(a.apply(this,e),0,0);var r=p.toDataURL();return s.clearRect(0,0,p.width,p.height),s.fillText(a.apply(this,t),0,0),r===p.toDataURL()}function l(e){if(!s||!s.fillText)return!1;switch(s.textBaseline="top",s.font="600 32px Arial",e){case"flag":return!c(\[127987,65039,8205,9895,65039\],\[127987,65039,8203,9895,65039\])&&(!c(\[55356,56826,55356,56819\],\[55356,56826,8203,55356,56819\])&&!c(\[55356,57332,56128,56423,56128,56418,56128,56421,56128,56430,56128,56423,56128,56447\],\[55356,57332,8203,56128,56423,8203,56128,56418,8203,56128,56421,8203,56128,56430,8203,56128,56423,8203,56128,56447\]));case"emoji":return!c(\[55357,56424,55356,57342,8205,55358,56605,8205,55357,56424,55356,57340\],\[55357,56424,55356,57342,8203,55358,56605,8203,55357,56424,55356,57340\])}return!1}function d(e){var t=a.createElement("script");t.src=e,t.defer=t.type="text/javascript",a.getElementsByTagName("head")\[0\].appendChild(t)}for(i=Array("flag","emoji"),t.supports={everything:!0,everythingExceptFlag:!0},o=0;o<i.length;o++)t.supports\[i\[o\]\]=l(i\[o\]),t.supports.everything=t.supports.everything&&t.supports\[i\[o\]\],"flag"!==i\[o\]&&(t.supports.everythingExceptFlag=t.supports.everythingExceptFlag&&t.supports\[i\[o\]\]);t.supports.everythingExceptFlag=t.supports.everythingExceptFlag&&!t.supports.flag,t.DOMReady=!1,t.readyCallback=function(){t.DOMReady=!0},t.supports.everything||(n=function(){t.readyCallback()},a.addEventListener?(a.addEventListener("DOMContentLoaded",n,!1),e.addEventListener("load",n,!1)):(e.attachEvent("onload",n),a.attachEvent("onreadystatechange",function(){"complete"===a.readyState&&t.readyCallback()})),(r=t.source||{}).concatemoji?d(r.concatemoji):r.wpemoji&&r.twemoji&&(d(r.twemoji),d(r.wpemoji)))}(window,document,window.\_wpemojiSettings);   img.wp-smiley, img.emoji { display: inline !important; border: none !important; box-shadow: none !important; height: 1em !important; width: 1em !important; margin: 0 .07em !important; vertical-align: -0.1em !important; background: none !important; padding: 0 !important; }      var related\_posts\_js\_options = {"post\_heading":"h4"};                                      .recentcomments a { display: inline !important; padding: 0 !important; margin: 0 !important; } table.recentcommentsavatartop img.avatar, table.recentcommentsavatarend img.avatar { border: 0px; margin: 0; } table.recentcommentsavatartop a, table.recentcommentsavatarend a { border: 0px !important; background-color: transparent !important; } td.recentcommentsavatarend, td.recentcommentsavatartop { padding: 0px 0px 1px 0px; margin: 0px; } td.recentcommentstextend { border: none !important; padding: 0px 0px 2px 10px; } .rtl td.recentcommentstextend { padding: 0px 10px 2px 0px; } td.recentcommentstexttop { border: none; padding: 0px 0px 0px 10px; } .rtl td.recentcommentstexttop { padding: 0px 10px 0px 0px; }    function \_\_ATA\_CC() {var v = document.cookie.match('(^|;) ?personalized-ads-consent=(\[^;\]\*)(;|$)');return v ? 1 : 0;} var \_\_ATA\_PP = { pt: 1, ht: 0, tn: 'pilcrow', amp: false, siteid: 8982, blogid: 51987203, consent: \_\_ATA\_CC() }; var \_\_ATA = \_\_ATA || {}; \_\_ATA.cmd = \_\_ATA.cmd || \[\]; \_\_ATA.criteo = \_\_ATA.criteo || {}; \_\_ATA.criteo.cmd = \_\_ATA.criteo.cmd || \[\];  (function(){function g(a,c){a:{for(var b=a.length,d="string"==typeof a?a.split(""):a,e=0;e<b;e++)if(e in d&&c.call(void 0,d\[e\],e,a)){c=e;break a}c=-1}return 0>c?null:"string"==typeof a?a.charAt(c):a\[c\]};function h(a,c,b){b=null!=b?"="+encodeURIComponent(String(b)):"";if(c+=b){b=a.indexOf("#");0>b&&(b=a.length);var d=a.indexOf("?");if(0>d||d>b){d=b;var e=""}else e=a.substring(d+1,b);a=\[a.substr(0,d),e,a.substr(b)\];b=a\[1\];a\[1\]=c?b?b+"&"+c:c:b;a=a\[0\]+(a\[1\]?"?"+a\[1\]:"")+a\[2\]}return a};var k=0;function l(a,c){var b=document.createElement("script");b.src=a;b.onload=function(){c&&c(void 0)};b.onerror=function(){c("error")};a=document.getElementsByTagName("head");var d;a&&0!==a.length?d=a\[0\]:d=document.documentElement;d.appendChild(b)}function m(a){return"string"==typeof a&&0<a.length} function p(a,c,b){c=void 0===c?"":c;b=void 0===b?".":b;var d=\[\];Object.keys(a).forEach(function(e){var f=a\[e\],n=typeof f;"object"==n&&null!=f||"function"==n?d.push(p(f,c+e+b)):null!==f&&void 0!==f&&(e=encodeURIComponent(c+e),d.push(e+"="+encodeURIComponent(f)))});return d.filter(m).join("&")}function q(){return window.\_\_ATA||{}}function r(a,c){a||(q().config=c.c,l(c.url))}var t=Math.floor(1E13\*Math.random());q().rid=t; var u=q().pageParams,v="//"+(q().serverDomain||"s.pubmine.com")+"/conf",w=window.top===window,x;try{var y=JSON.parse(document.getElementById("oil-configuration").innerText);if("boolean"!==typeof y.gdpr\_applies)throw Error("Config doesn't contain gdpr\_applies");x=y.gdpr\_applies?1:0}catch(a){x=null} var z=x,A=window.\_\_ATA\_PP||u||null,B=w?document.referrer?document.referrer:null:null,C=w?null:document.referrer?document.referrer:null,D=function(){var a=void 0===a?document.cookie:a;return(a=g(a.split("; "),function(c){return-1!=c.indexOf("\_\_ATA\_tuuid=")}))?a.split("=")\[1\]:""}(),E=p({gdpr:z,pp:A,rid:t,src:B,ref:C,tuuid:D?D:null,vp:window.innerWidth+"x"+window.innerHeight},"","."); (function(a){var c;k++;var b="callback\_\_"+Date.now().toString(36)+"\_"+k.toString(36);a=h(a,void 0===c?"cb":c,b);window\[b\]=function(d){r(void 0,d)};l(a,function(d){d&&r(d)})})(v+"?"+E);}).call(this);  window.google\_analytics\_uacct = "UA-52447-2"; var \_gaq = \_gaq || \[\]; \_gaq.push(\['\_setAccount', 'UA-52447-2'\]); \_gaq.push(\['\_gat.\_anonymizeIp'\]); \_gaq.push(\['\_setDomainName', 'wordpress.com'\]); \_gaq.push(\['\_initData'\]); \_gaq.push(\['\_trackPageview'\]); (function() { var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true; ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js'; (document.getElementsByTagName('head')\[0\] || document.getElementsByTagName('body')\[0\]).appendChild(ga); })(); 

[Krishnakumar's SQL Server Blog](https://krishnakumarsql.wordpress.com/ "Krishnakumar's SQL Server Blog")

[Skip to content](#content "Skip to content")

*   [Home](https://krishnakumarsql.wordpress.com/)
*   [About](https://krishnakumarsql.wordpress.com/about/)

 [![](https://krishnakumarsql.files.wordpress.com/2013/11/cropped-20131006_175620.jpg)](https://krishnakumarsql.wordpress.com/) 

[← Introducing SQL Server Extended Events](https://krishnakumarsql.wordpress.com/2014/11/25/sql-server-extended-events/)

November 25, 2014 · 6:41 PM

[↓ Jump to Comments](https://krishnakumarsql.wordpress.com/2014/11/25/intra-query-parallel-deadlock/#comments)

[Intra-Query Parallel Deadlock](https://krishnakumarsql.wordpress.com/2014/11/25/intra-query-parallel-deadlock/)
================================================================================================================

A deadlock happens when two tasks permanently block each other when one task is trying to get a resource to lock but the resource is already locked by the other task. SQL Server will chose one of the task (session) that has lower rollback cost, as a deadlock victim and rollback that transaction. The error message may look like this.

Msg 1205, Level 13, State 45, Line 5

Transaction (Process ID 52) was deadlocked on lock resources with

another process and has been chosen as the deadlock victim.

Rerun the transaction.

The deadlock may usually happen when queries in two sessions fight for resources each other in a cyclic manner. In this post I’m not going in deep on deadlock analysis or fixing. The post describes a special case of deadlock called ‘Intra-Query Parallel Deadlock’ that I encountered very recently.

Intra-Query Parallel deadlock happens on parallel query plan executions. One of our clients reported a frequent deadlock occurrence on a procedure. I ran scripts to query deadlock graph and the graph below looks different from usual deadlock graph.

(For clarity I’ve omitted some of the nodes and reformatted)

victim-list

victimProcess id=”process5554c8″/>

victim-list

process-list

process id=”process5554c8″

process id=”process4c434c8″

process id=”process55fdc8″

inputbuf

Proc \[Database Id = 7 Object Id = 532912970\]

resource-list

pagelock pageid=”5259244″ objectname=”” mode=”U”

owner-list

owner id=”process55fdc8″ mode=”U”

waiter-list

waiter id=”process5554c8″ mode=”U” requestType=”wait”

pagelock pageid=”5258622″ objectname=”” mode=”U” owner-list

owner id=”process5554c8″ mode=”U”

waiter-list

waiter id=”process4c434c8″ mode=”U” requestType=”wait”

pagelock

exchangeEvent id=”Pipe1b6aa3a50″ WaitType=”e\_waitPipeGetRow” nodeId=”5″

waiter-list

waiter id=”process55fdc8″

The exchangeEvent node (marked in red above) is the key discussion point here. When a parallel query operator scans the data using multiple concurrent threads, an **_exchange operator_** is used to “glue” the rows at the end of execution of threads. The parallelism operator in the below plan is an exchange operator.

[![Parallel Plan](https://krishnakumarsql.files.wordpress.com/2014/11/parallel-plan.png?w=721&h=203)](https://krishnakumarsql.files.wordpress.com/2014/11/parallel-plan.png)

(You can read the a detailed discussion on Parallelism operator or exchange operator [here](http://blogs.msdn.com/b/craigfr/archive/2006/10/25/the-parallelism-operator-aka-exchange.aspx "The Parallelism Operator (aka Exchange)"))

In some rare scenarios the Parallelism operator cause deadlock to the input threads. From Craig Freedman’s presentation here([http://blogs.msdn.com/b/craigfr/archive/2007/04/17/parallel-query-execution-presentation.aspx](http://blogs.msdn.com/b/craigfr/archive/2007/04/17/parallel-query-execution-presentation.aspx)), the scenarios are

1.  Two merging exchanges separated by order preserving operators
2.  A merge join with merging exchanges on both inputs
3.  Merging exchange above index seek with multiple ranges

Ultimately the query will deadlock due to the execution of the query itself!

The e\_waitPipeGetRow is the wait type inside the exchange event. You can read more on this [here](http://sqlblog.com/blogs/sqlos_team/archive/2010/12/29/better-documentation-for-tasks-waiting-on-resources.aspx "Better documentation for tasks waiting on resources"). Apart from exchangeEvent sometimes you can see threadpool also.

SQL Server will raise an error saying;

Server: Msg 8650, Level 13, State 1, Line 1 Intra-query parallelism caused your server command (process ID #51) to deadlock. Rerun the query without intra-query parallelism by using the query hint option (maxdop 1)

As the message suggests, setting MAXDOP 1 (maximum degree-of-parallelism to 1), may solve the issue by using a single execution thread (a serial plan). However setting MAXDOP is not a good solution in all scenarios. Rewriting the query or defining proper indexes may avoid the parallel plan. As suggested by Microsoft, sometimes installing service packs may fix this issue.

The problem database server was SQL Server 2008 R2. I created an index and this lead to a serial plan and prevent the intra-query parallel deadlock!

Ultimately the problem sorted out and everyone was happy. This was a good learning experience for me.

Here are some resources you can read and enjoy!

[Today’s Annoyingly-Unwieldy Term: “Intra-Query Parallel Thread Deadlocks”](http://blogs.msdn.com/b/bartd/archive/2008/09/24/today-s-annoyingly-unwieldy-term-intra-query-parallel-thread-deadlocks.aspx "Today's Annoyingly-Unwieldy Term: "Intra-Query Parallel Thread Deadlocks"")

[Degrees of Parallelism and a Degree of Uncertainty](http://blogs.technet.com/b/mat_stephen/archive/2005/02/08/369120.aspx "Degrees of Parallelism and a Degree of Uncertainty")

[Handling Deadlocks in SQL Server](https://www.simple-talk.com/sql/database-administration/handling-deadlocks-in-sql-server/ "Handling Deadlocks in SQL Server")

[Understanding and Using Parallelism in SQL Server](https://www.simple-talk.com/sql/learn-sql-server/understanding-and-using-parallelism-in-sql-server/ "Understanding and Using Parallelism in SQL Server")

\_\_ATA.cmd.push(function() { \_\_ATA.initVideoSlot('atatags-370373-5dbc260c4e9f8', { sectionId: '370373', format: 'inread' }); });

Advertisements

\_\_ATA.cmd.push(function() { \_\_ATA.initSlot('atatags-26942-5dbc260c4ea4e', { collapseEmpty: 'before', sectionId: '26942', location: 120, width: 300, height: 250 }); });

\_\_ATA.cmd.push(function() { \_\_ATA.initSlot('atatags-114160-5dbc260c4ea56', { collapseEmpty: 'before', sectionId: '114160', location: 130, width: 300, height: 250 }); });

### Share this:

*   [Twitter](https://krishnakumarsql.wordpress.com/2014/11/25/intra-query-parallel-deadlock/?share=twitter "Click to share on Twitter")
*   [Facebook](https://krishnakumarsql.wordpress.com/2014/11/25/intra-query-parallel-deadlock/?share=facebook "Click to share on Facebook")
*   [LinkedIn](https://krishnakumarsql.wordpress.com/2014/11/25/intra-query-parallel-deadlock/?share=linkedin "Click to share on LinkedIn")

### Like this:

Like Loading...

### _Related_

[Leave a comment](https://krishnakumarsql.wordpress.com/2014/11/25/intra-query-parallel-deadlock/#respond)

Filed under [Administration](https://krishnakumarsql.wordpress.com/category/administration/), [Internals](https://krishnakumarsql.wordpress.com/category/internals/), [Performance](https://krishnakumarsql.wordpress.com/category/performance/)

Tagged as [Deadlock](https://krishnakumarsql.wordpress.com/tag/deadlock/), [intra-query parallel deadlock](https://krishnakumarsql.wordpress.com/tag/intra-query-parallel-deadlock/), [Parallelism](https://krishnakumarsql.wordpress.com/tag/parallelism/)  

[← Introducing SQL Server Extended Events](https://krishnakumarsql.wordpress.com/2014/11/25/sql-server-extended-events/)

### Leave a Reply [Cancel reply](/2014/11/25/intra-query-parallel-deadlock/#respond)

 

Enter your comment here...

Fill in your details below or click an icon to log in:

 [![Gravatar](https://1.gravatar.com/avatar/ad516503a11cd5ca435acc9bb6523536?s=25&d=identicon&forcedefault=y&r=G)](https://gravatar.com/site/signup/) 

Email (required) (Address never made public)

Name (required)

Website

![WordPress.com Logo](https://1.gravatar.com/avatar/ad516503a11cd5ca435acc9bb6523536?s=25&d=identicon&forcedefault=y&r=G)

  

You are commenting using your WordPress.com account. ( [Log Out](javascript:HighlanderComments.doExternalLogout( 'wordpress' );) /  [Change](#) )

![Google photo](https://1.gravatar.com/avatar/ad516503a11cd5ca435acc9bb6523536?s=25&d=identicon&forcedefault=y&r=G)

  

You are commenting using your Google account. ( [Log Out](javascript:HighlanderComments.doExternalLogout( 'googleplus' );) /  [Change](#) )

![Twitter picture](https://1.gravatar.com/avatar/ad516503a11cd5ca435acc9bb6523536?s=25&d=identicon&forcedefault=y&r=G)

  

You are commenting using your Twitter account. ( [Log Out](javascript:HighlanderComments.doExternalLogout( 'twitter' );) /  [Change](#) )

![Facebook photo](https://1.gravatar.com/avatar/ad516503a11cd5ca435acc9bb6523536?s=25&d=identicon&forcedefault=y&r=G)

  

You are commenting using your Facebook account. ( [Log Out](javascript:HighlanderComments.doExternalLogout( 'facebook' );) /  [Change](#) )

[Cancel](javascript:HighlanderComments.cancelExternalWindow();)

Connecting to %s

var highlander\_expando\_javascript = function(){ var input = document.createElement( 'input' ), comment = jQuery( '#comment' ); if ( 'placeholder' in input ) { comment.attr( 'placeholder', jQuery( '.comment-textarea label' ).remove().text() ); } // Expando Mode: start small, then auto-resize on first click + text length jQuery( '#comment-form-identity' ).hide(); jQuery( '#comment-form-subscribe' ).hide(); jQuery( '#commentform .form-submit' ).hide(); comment.css( { 'height':'10px' } ).one( 'focus', function() { var timer = setInterval( HighlanderComments.resizeCallback, 10 ) jQuery( this ).animate( { 'height': HighlanderComments.initialHeight } ).delay( 100 ).queue( function(n) { clearInterval( timer ); HighlanderComments.resizeCallback(); n(); } ); jQuery( '#comment-form-identity' ).slideDown(); jQuery( '#comment-form-subscribe' ).slideDown(); jQuery( '#commentform .form-submit' ).slideDown(); }); } jQuery(document).ready( highlander\_expando\_javascript );

 Notify me of new comments via email.

 Notify me of new posts via email.

  

*   November 2014
    
    M
    
    T
    
    W
    
    T
    
    F
    
    S
    
    S
    
    [« Oct](https://krishnakumarsql.wordpress.com/2014/10/)
    
     
    
     
    
     
    
    1
    
    2
    
    3
    
    4
    
    5
    
    6
    
    7
    
    8
    
    9
    
    10
    
    11
    
    12
    
    13
    
    14
    
    15
    
    16
    
    17
    
    18
    
    19
    
    20
    
    21
    
    22
    
    23
    
    24
    
    [25](https://krishnakumarsql.wordpress.com/2014/11/25/)
    
    26
    
    27
    
    28
    
    29
    
    30
    
*   ### [![RSS](https://s-ssl.wordpress.com/wp-includes/images/rss.png?m=1354137473h)](https://social.technet.microsoft.com/Profile/u/activities/feed?displayName=Krishnakumar%20S&outputAs=rss "Syndicate this content") [My Activities in SQL Server Forums](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity "This is a dynamic feed of a user's activities.")
    
    *   [Helped identify a helpful topic Make the database drop down wider? in the Getting started with SQL Server Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Helped identify a helpful topic Make the database drop down wider? in the Getting started with SQL Server Forum.
        
    *   [Contributed a helpful post to the Insufficient result space to convert uniqueidentifier value to char thread in the Transact-SQL Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Contributed a helpful post to the Insufficient result space to convert uniqueidentifier value to char thread in the Transact-SQL Forum.
        
    *   [Answered the question Reg. Objects on two databases- in the Database Design Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Answered the question Reg. Objects on two databases- in the Database Design Forum.
        
    *   [Contributed a proposed answer to the question Reg. Objects on two databases- in the Database Design Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Contributed a proposed answer to the question Reg. Objects on two databases- in the Database Design Forum.
        
    *   [Contributed a helpful post to the Insert data to table with clustered index thread in the Transact-SQL Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Contributed a helpful post to the Insert data to table with clustered index thread in the Transact-SQL Forum.
        
    *   [Quickly answered the question how to write stored procedure using dynamic sql inside it but with good performance? confirmed by the asker in the Transact-SQL Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Quickly answered the question how to write stored procedure using dynamic sql inside it but with good performance? confirmed by the asker in the Transact-SQL Forum.
        
    *   [Replied to a forums thread SQL : Query to Replace null with NEXT non-null values in the Transact-SQL Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Replied to a forums thread SQL : Query to Replace null with NEXT non-null values in the Transact-SQL Forum.
        
    *   [Replied to a forums thread how to write stored procedure using dynamic sql inside it but with good performance? in the Transact-SQL Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Replied to a forums thread how to write stored procedure using dynamic sql inside it but with good performance? in the Transact-SQL Forum.
        
    *   [Answered the question Seed for RAND() function in SQL Server 2005 confirmed by the asker in the Transact-SQL Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Answered the question Seed for RAND() function in SQL Server 2005 confirmed by the asker in the Transact-SQL Forum.
        
    *   [Replied to a forums thread How to see Float value in ssms without exponential values? in the Getting started with SQL Server Forum.](http://social.technet.microsoft.com/Profile/v1/Krishnakumar%20S/activity)
        
        Replied to a forums thread How to see Float value in ssms without exponential values? in the Getting started with SQL Server Forum.
        
*   [![View Krishnakumar S's profile on LinkedIn](https://static.licdn.com/scds/common/u/img/webpromo/btn_viewmy_160x25.png)](http://in.linkedin.com/in/krishnakumars1)
    

Advertisements

\_\_ATA.cmd.push(function() { \_\_ATA.initSlot('atatags-286348-5dbc260c51fcf', { collapseEmpty: 'before', sectionId: '286348', location: 140, width: 160, height: 600 }); });

[Krishnakumar's SQL Server Blog](https://krishnakumarsql.wordpress.com/ "Krishnakumar's SQL Server Blog") · A write-ahead (b)logging on SQL Server

[Create a free website or blog at WordPress.com.](https://wordpress.com/?ref=footer_website)

var WPGroHo = {"my\_hash":""}; //initialize and attach hovercards to all gravatars jQuery( document ).ready( function( $ ) { if (typeof Gravatar === "undefined"){ return; } if ( typeof Gravatar.init !== "function" ) { return; } Gravatar.profile\_cb = function( hash, id ) { WPGroHo.syncProfileData( hash, id ); }; Gravatar.my\_hash = WPGroHo.my\_hash; Gravatar.init( 'body', '#wp-admin-bar-my-account' ); });

var HighlanderComments = {"loggingInText":"Logging In\\u2026","submittingText":"Posting Comment\\u2026","postCommentText":"Post Comment","connectingToText":"Connecting to %s","commentingAsText":"%1$s: You are commenting using your %2$s account.","logoutText":"Log Out","loginText":"Log In","connectURL":"https:\\/\\/krishnakumarsql.wordpress.com\\/public.api\\/connect\\/?action=request","logoutURL":"https:\\/\\/krishnakumarsql.wordpress.com\\/wp-login.php?action=logout&\_wpnonce=43dde387f1","homeURL":"https:\\/\\/krishnakumarsql.wordpress.com\\/","postID":"363","gravDefault":"identicon","enterACommentError":"Please enter a comment","enterEmailError":"Please enter your email address here","invalidEmailError":"Invalid email address","enterAuthorError":"Please enter your name here","gravatarFromEmail":"This picture will show whenever you leave a comment. Click to customize it.","logInToExternalAccount":"Log in to use details from one of these accounts.","change":"Change","changeAccount":"Change Account","comment\_registration":"0","userIsLoggedIn":"","isJetpack":"","text\_direction":"ltr"}; ( function( $ ) { $( document.body ).on( 'post-load', function () { \_\_ATA.insertInlineAds(); } ); } )( jQuery );

Post to

[Cancel](#)      

window.WPCOM\_sharing\_counts = {"https:\\/\\/krishnakumarsql.wordpress.com\\/2014\\/11\\/25\\/intra-query-parallel-deadlock\\/":363};

 Privacy & Cookies: This site uses cookies. By continuing to use this website, you agree to their use.  
To find out more, including how to control cookies, see here: [Cookie Policy](https://automattic.com/cookies)

  var actionbardata = {"siteID":"51987203","siteName":"Krishnakumar's SQL Server Blog","siteURL":"http:\\/\\/krishnakumarsql.wordpress.com","icon":"<img alt='' src='https:\\/\\/s2.wp.com\\/i\\/logo\\/wpcom-gray-white.png' class='avatar avatar-50' height='50' width='50' \\/>","canManageOptions":"","canCustomizeSite":"","isFollowing":"","themeSlug":"pub\\/pilcrow","signupURL":"https:\\/\\/wordpress.com\\/start\\/","loginURL":"https:\\/\\/wordpress.com\\/log-in?redirect\_to=https%3A%2F%2Fkrishnakumarsql.wordpress.com%2F2014%2F11%2F25%2Fintra-query-parallel-deadlock%2F&signup\_flow=account","themeURL":"","xhrURL":"https:\\/\\/krishnakumarsql.wordpress.com\\/wp-admin\\/admin-ajax.php","nonce":"d1a824e025","isSingular":"1","isFolded":"","isLoggedIn":"","isMobile":"","subscribeNonce":"<input type=\\"hidden\\" id=\\"\_wpnonce\\" name=\\"\_wpnonce\\" value=\\"ffe8c16eda\\" \\/>","referer":"https:\\/\\/krishnakumarsql.wordpress.com\\/2014\\/11\\/25\\/intra-query-parallel-deadlock\\/","canFollow":"1","feedID":"10828230","statusMessage":"","customizeLink":"https:\\/\\/krishnakumarsql.wordpress.com\\/wp-admin\\/customize.php?url=https%3A%2F%2Fkrishnakumarsql.wordpress.com%2F2014%2F11%2F25%2Fintra-query-parallel-deadlock%2F","postID":"363","shortlink":"https:\\/\\/wp.me\\/p3w8fh-5R","canEditPost":"","editLink":"https:\\/\\/wordpress.com\\/post\\/krishnakumarsql.wordpress.com\\/363","statsLink":"https:\\/\\/wordpress.com\\/stats\\/post\\/363\\/krishnakumarsql.wordpress.com","i18n":{"view":"View site","follow":"Follow","following":"Following","edit":"Edit","login":"Log in","signup":"Sign up","customize":"Customize","report":"Report this content","themeInfo":"Get theme: Pilcrow","shortlink":"Copy shortlink","copied":"Copied","followedText":"New posts from this site will now appear in your <a href=\\"https:\\/\\/wordpress.com\\/\\">Reader<\\/a>","foldBar":"Collapse this bar","unfoldBar":"Expand this bar","editSubs":"Manage subscriptions","viewReader":"View site in Reader","viewReadPost":"View post in Reader","subscribe":"Sign me up","enterEmail":"Enter your email address","followers":"Join 138 other followers","alreadyUser":"Already have a WordPress.com account? <a href=\\"https:\\/\\/wordpress.com\\/log-in?redirect\_to=https%3A%2F%2Fkrishnakumarsql.wordpress.com%2F2014%2F11%2F25%2Fintra-query-parallel-deadlock%2F&signup\_flow=account\\">Log in now.<\\/a>","stats":"Stats"}};   var jetpackCarouselStrings = {"widths":\[370,700,1000,1200,1400,2000\],"is\_logged\_in":"","lang":"en","ajaxurl":"https:\\/\\/krishnakumarsql.wordpress.com\\/wp-admin\\/admin-ajax.php","nonce":"8fc4b4a281","display\_exif":"1","display\_geo":"1","single\_image\_gallery":"1","single\_image\_gallery\_media\_file":"","background\_color":"black","comment":"Comment","post\_comment":"Post Comment","write\_comment":"Write a Comment...","loading\_comments":"Loading Comments...","download\_original":"View full size <span class=\\"photo-size\\">{0}<span class=\\"photo-size-times\\">\\u00d7<\\/span>{1}<\\/span>","no\_comment\_text":"Please be sure to submit some text with your comment.","no\_comment\_email":"Please provide an email address to comment.","no\_comment\_author":"Please provide your name to comment.","comment\_post\_error":"Sorry, but there was an error posting your comment. Please try again later.","comment\_approved":"Your comment was approved.","comment\_unapproved":"Your comment is in moderation.","camera":"Camera","aperture":"Aperture","shutter\_speed":"Shutter Speed","focal\_length":"Focal Length","copyright":"Copyright","comment\_registration":"0","require\_name\_email":"1","login\_url":"https:\\/\\/krishnakumarsql.wordpress.com\\/wp-login.php?redirect\_to=https%3A%2F%2Fkrishnakumarsql.wordpress.com%2F2014%2F11%2F25%2Fintra-query-parallel-deadlock%2F","blog\_id":"51987203","meta\_data":\["camera","aperture","shutter\_speed","focal\_length","copyright"\],"local\_comments\_commenting\_as":"<fieldset><label for=\\"email\\">Email (Required)<\\/label> <input type=\\"text\\" name=\\"email\\" class=\\"jp-carousel-comment-form-field jp-carousel-comment-form-text-field\\" id=\\"jp-carousel-comment-form-email-field\\" \\/><\\/fieldset><fieldset><label for=\\"author\\">Name (Required)<\\/label> <input type=\\"text\\" name=\\"author\\" class=\\"jp-carousel-comment-form-field jp-carousel-comment-form-text-field\\" id=\\"jp-carousel-comment-form-author-field\\" \\/><\\/fieldset><fieldset><label for=\\"url\\">Website<\\/label> <input type=\\"text\\" name=\\"url\\" class=\\"jp-carousel-comment-form-field jp-carousel-comment-form-text-field\\" id=\\"jp-carousel-comment-form-url-field\\" \\/><\\/fieldset>","reblog":"Reblog","reblogged":"Reblogged","reblog\_add\_thoughts":"Add your thoughts here... (optional)","reblogging":"Reblogging...","post\_reblog":"Post Reblog","stats\_query\_args":"blog=51987203&v=wpcom&tz=5&user\_id=0&subd=krishnakumarsql","is\_public":"1","reblog\_enabled":""};   var sharing\_js\_options = {"lang":"en","counts":"1","is\_stats\_active":"1"};    var windowOpen; jQuery( document.body ).on( 'click', 'a.share-twitter', function() { // If there's another sharing window open, close it. if ( 'undefined' !== typeof windowOpen ) { windowOpen.close(); } windowOpen = window.open( jQuery( this ).attr( 'href' ), 'wpcomtwitter', 'menubar=1,resizable=1,width=600,height=350' ); return false; }); var windowOpen; jQuery( document.body ).on( 'click', 'a.share-facebook', function() { // If there's another sharing window open, close it. if ( 'undefined' !== typeof windowOpen ) { windowOpen.close(); } windowOpen = window.open( jQuery( this ).attr( 'href' ), 'wpcomfacebook', 'menubar=1,resizable=1,width=600,height=400' ); return false; }); var windowOpen; jQuery( document.body ).on( 'click', 'a.share-linkedin', function() { // If there's another sharing window open, close it. if ( 'undefined' !== typeof windowOpen ) { windowOpen.close(); } windowOpen = window.open( jQuery( this ).attr( 'href' ), 'wpcomlinkedin', 'menubar=1,resizable=1,width=580,height=450' ); return false; });   // <!\[CDATA\[ (function() { try{ if ( window.external &&'msIsSiteMode' in window.external) { if (window.external.msIsSiteMode()) { var jl = document.createElement('script'); jl.type='text/javascript'; jl.async=true; jl.src='/wp-content/plugins/ie-sitemode/custom-jumplist.php'; var s = document.getElementsByTagName('script')\[0\]; s.parentNode.insertBefore(jl, s); } } }catch(e){} })(); // \]\]>  

%d bloggers like this:

\_tkq = window.\_tkq || \[\]; \_stq = window.\_stq || \[\]; \_tkq.push(\['storeContext', {'blog\_id':'51987203','blog\_tz':'5','user\_lang':'en','blog\_lang':'en','user\_id':'0'}\]); \_stq.push(\['view', {'blog':'51987203','v':'wpcom','tz':'5','user\_id':'0','post':'363','subd':'krishnakumarsql'}\]); \_stq.push(\['extra', {'crypt':'UE5XaGUuOTlwaD85flAmcm1mcmZsaDhkV11YdTdvUG14Q2VDQTR4LlUsLi82dU1mai9BMlIueS10bVlkVk1DYjdnM0R3ZnJUP0E0dF82T0w0Pzc4OFVSSHB3ajdHbGwxNkRjRy53bzMlaC9CZ3k2ZDVXZHBkbm1OWlJaLDA/WltBVnZySnFxZUFfRTJaa0o/RFZQTGkmUnorVWFXdD9Rd1JOWS9BXVd6WzFNRU1rX2k0WHBtWUN8TW5ySU12anBbVTVPdVZ+fFtqc2xBNFVPYWMzP21vfl9saFk0blc4dzYtS0Z4LTRtOEk9eFlnbVBsXVtUU3k1TEVyJTE4aCx8eWRxSlZ8aC9Bam8zbGxKTyVzZTZjMkRIcXp4OE4tVTlfVT0='}\]); \_stq.push(\[ 'clickTrackerInit', '51987203', '363' \]);

![](https://pixel.wp.com/b.gif?v=noscript)

if ( 'object' === typeof wpcom\_mobile\_user\_agent\_info ) { wpcom\_mobile\_user\_agent\_info.init(); var mobileStatsQueryString = ""; if( false !== wpcom\_mobile\_user\_agent\_info.matchedPlatformName ) mobileStatsQueryString += "&x\_" + 'mobile\_platforms' + '=' + wpcom\_mobile\_user\_agent\_info.matchedPlatformName; if( false !== wpcom\_mobile\_user\_agent\_info.matchedUserAgentName ) mobileStatsQueryString += "&x\_" + 'mobile\_devices' + '=' + wpcom\_mobile\_user\_agent\_info.matchedUserAgentName; if( wpcom\_mobile\_user\_agent\_info.isIPad() ) mobileStatsQueryString += "&x\_" + 'ipad\_views' + '=' + 'views'; if( "" != mobileStatsQueryString ) { new Image().src = document.location.protocol + '//pixel.wp.com/g.gif?v=wpcom-no-pv' + mobileStatsQueryString + '&baba=' + Math.random(); } }
