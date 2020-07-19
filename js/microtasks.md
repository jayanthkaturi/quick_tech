<script>window.fontTest();</script>

<div class="page-wrapper page-wrapper_sidebar_on">

<div class="sitetoolbar sitetoolbar_tutorial"><script>window.langs = [{"code":"am","name":"Armenian"},{"code":"ar","name":"Arabic"},{"code":"az","name":"Azerbaijani"},{"code":"bg","name":"Bulgarian"},{"code":"bn","name":"Bengali"},{"code":"ca","name":"Catalan"},{"code":"cs","name":"Czech"},{"code":"de","name":"German"},{"code":"el","name":"Greek"},{"code":"en","name":"English"},{"code":"es","name":"Spanish"},{"code":"fa","name":"Persian (Farsi)"},{"code":"fr","name":"French"},{"code":"hi","name":"Hindi"},{"code":"hu","name":"Hungarian"},{"code":"id","name":"Indonesian"},{"code":"it","name":"Italian"},{"code":"ja","name":"Japanese"},{"code":"ka","name":"Georgian"},{"code":"km","name":"Central Khmer"},{"code":"ko","name":"Korean"},{"code":"lt","name":"Lithuanian"},{"code":"me","name":"Montenegrin"},{"code":"ml","name":"Malayalam"},{"code":"nl","name":"Dutch"},{"code":"no","name":"Norvegian"},{"code":"pa","name":"Punjabi"},{"code":"pl","name":"Polish"},{"code":"pt","name":"Portuguese"},{"code":"ro","name":"Romanian"},{"code":"ru","name":"Russian"},{"code":"si","name":"Sinhala"},{"code":"sk","name":"Slovak"},{"code":"sq","name":"Albanian"},{"code":"ta","name":"Tamil"},{"code":"te","name":"Telugu"},{"code":"test","name":"Test"},{"code":"th","name":"Thai"},{"code":"tk","name":"Turkmen"},{"code":"tr","name":"Turkish"},{"code":"uk","name":"Ukrainian"},{"code":"uz","name":"Uzbek"},{"code":"vi","name":"Vietnamese"},{"code":"zh-hant","name":"Chinese Traditional"},{"code":"zh","name":"Chinese"}];</script><script>window.lang = "en";</script><script>{let t=navigator.languages||[];t=t.map(t=>t.toLowerCase());let a,o,i=[];for(let a of window.langs)for(let o of t)if(o===a.code||o.startsWith(a.code+"-")){i.push(a);break}if("en"===lang){let t=i.find(t=>"en"!=t.code);t&&"ru"!=t.code&&(a=`\n According to your browser language headers, you know ${t.name}. Please help to <a href="https://github.com/javascript-tutorial/${t.code}.javascript.info#readme">translate the tutorial</a> into your language!\n Thank you!\n `,o="notify-translate-tutorial")}else if("ru"===lang)o="notify-ru-tutorial",a='\n Новая редакция учебника была недавно переведена с английского.<br>Если что-то не так - пожалуйста, поправьте в <a href="https://github.com/javascript-tutorial/ru.javascript.info">PR на GitHub</a> (ссылка на редактирование слева в сайдбаре статьи).\n Спасибо!\n ';else if("tr"==lang)a='The Turkish version is only half-translated yet! Please help us with its translation at <a href="https://github.com/javascript-tutorial/tr.javascript.info">GitHub</a>.',o="notify-tr-tutorial";else{i.find(t=>"en"==t.code)&&(a=`\n According to your browser headers, you know English. Please help to <a href="https://github.com/javascript-tutorial/${lang}.javascript.info#readme">translate the tutorial</a>.\n Thank you!\n `,o="notify-translate-tutorial-local")}if(a){let t=`<div class="notification notification_top notification_info sitetoolbar__notification" style="display:none" id="${o}">\n <div class="notification__content">${a}</div>\n <button class="notification__close" title="Close"></button>\n </div>`;document.write(t),showTopNotification()}}</script>

<div class="sitetoolbar__content">

<div class="sitetoolbar__lang-switcher"><button class="sitetoolbar__dropdown-button" data-dropdown-toggler="">EN</button>

<div class="sitetoolbar__dropdown-wrap">

<div class="sitetoolbar__dropdown-body">

<div class="sitetoolbar__lang-switcher-body">

<div class="supported-langs supported-langs_toolbar">

<div class="supported-langs__container">

*   [<span class="supported-langs__brief">EN</span><span class="supported-langs__title">English</span>](https://javascript.info/event-loop)
*   [<span class="supported-langs__brief">JA</span><span class="supported-langs__title">日本語</span>](https://ja.javascript.info/event-loop)
*   [<span class="supported-langs__brief">KO</span><span class="supported-langs__title">한국어</span>](https://ko.javascript.info/event-loop)
*   [<span class="supported-langs__brief">RU</span><span class="supported-langs__title">Русский</span>](https://learn.javascript.ru/event-loop)
*   [<span class="supported-langs__brief">TR</span><span class="supported-langs__title">Türkçe</span>](https://tr.javascript.info/)
*   [<span class="supported-langs__brief">ZH</span><span class="supported-langs__title">简体中文</span>](https://zh.javascript.info/event-loop)

</div>

<div class="supported-langs__text">

We want to make this open-source project available for people all around the world.

[Help to translate](https://javascript.info/translate) the content of this tutorial to your language!

</div>

</div>

</div>

</div>

</div>

</div>

<div class="sitetoolbar__logo-wrap">[![](/img/sitetoolbar__logo_en.svg)![](/img/sitetoolbar__logo_small_en.svg)<script>Array.prototype.forEach.call(document.querySelectorAll("img.sitetoolbar__logo"),function(e){let t=document.createElement("object");t.type="image/svg+xml",t.className=e.className,t.style.cssText="left:0;top:0;position:absolute",t.onload=function(){t.onload=null,e.style.visibility="hidden"},t.data=e.src,e.parentNode.insertBefore(t,e)});</script>](/)</div>

<nav class="sitetoolbar__sections"></nav>

<div class="sitetoolbar__book-wrap">[<span class="buy-book-button__extra-text">Buy</span>EPUB/PDF](/ebook)</div>

<div class="sitetoolbar__search-wrap">

<div class="sitetoolbar__search-content">

<form class="sitetoolbar__search" method="GET" action="/search">

<div class="sitetoolbar__search-input">

<div class="text-input"><input class="text-input__control" name="query" placeholder="Search on Javascript.info" required="required" type="text"></div>

<button class="sitetoolbar__find" type="submit">Search</button></div>

</form>

</div>

</div>

</div>

<div class="tablet-menu">

<div class="tablet-menu__line">

<div class="tablet-menu__content">

<form class="tablet-menu-search" action="/search/"><input class="tablet-menu-search__input" type="search" name="query" placeholder="Search in the tutorial" required="required"><button class="tablet-menu-search__button" type="submit" name="type" value="articles">Search</button></form>

</div>

</div>

<div class="tablet-menu__line">

<div class="tablet-menu__content">[<span class="map__text">Tutorial map</span>](/tutorial/map)</div>

</div>

<div class="tablet-menu__line">

<div class="tablet-menu__content">

<div class="share-icons"><span class="share-icons__title">Share</span>[](https://twitter.com/share?url=https%3A%2F%2Fjavascript.info%2Fevent-loop)[](https://www.facebook.com/sharer/sharer.php?s=100&p%5Burl%5D=https%3A%2F%2Fjavascript.info%2Fevent-loop)</div>

</div>

</div>

<div class="tablet-menu__line">

<div class="tablet-menu__content"><select class="tablet-menu__nav input-select input-select input-select_small" onchange="if(this.value) window.location.href=this.value"><option value="https://javascript.info/event-loop" selected="">English</option><option value="https://ja.javascript.info/event-loop">日本語</option><option value="https://ko.javascript.info/event-loop">한국어</option><option value="https://learn.javascript.ru/event-loop">Русский</option><option value="https://tr.javascript.info/">Türkçe</option><option value="https://zh.javascript.info/event-loop">简体中文</option></select></div>

</div>

</div>

</div>

<div class="page page_sidebar_on page_inner_padding"><script>if(localStorage.noSidebar){document.querySelector(".page").classList.remove("page_sidebar_on");var pageWrapper=document.querySelector(".page-wrapper");pageWrapper&&pageWrapper.classList.remove("page-wrapper_sidebar_on")}setTimeout(function(){document.querySelector(".page").classList.add("page_sidebar-animation-on")},0);</script>

<div class="page__inner">

<main class="main main_width-limit">

<header class="main__header">

<div class="main__header-inner">

<div class="main__header-group">

1.  [<span class="breadcrumbs__hidden-text">Tutorial</span>](/)
2.  [<span>Browser: Document, Events, Interfaces</span>](/ui)
3.  [<span>Miscellaneous</span>](/ui-misc)
<script type="application/ld+json">{"@context":"https://schema.org","@type":"BreadcrumbList","itemListElement":[{"@type":"ListItem","position":1,"name":"Tutorial","item":"https://javascript.info/"},{"@type":"ListItem","position":2,"name":"Browser: Document, Events, Interfaces","item":"https://javascript.info/ui"},{"@type":"ListItem","position":3,"name":"Miscellaneous","item":"https://javascript.info/ui-misc"}]}</script>

<div class="updated-at" data-tooltip="Last updated at 14th February 2020">

<div class="updated-at__content">14th February 2020</div>

</div>

</div>

# Event loop: microtasks and macrotasks

</div>

</header>

<div class="content">

<article class="formatted" itemscope="" itemtype="http://schema.org/TechArticle"><meta itemprop="name" content="Event loop: microtasks and macrotasks">

<div itemprop="author" itemscope="" itemtype="http://schema.org/Person"><meta itemprop="email" content="iliakan@gmail.com"><meta itemprop="name" content="Ilya Kantor"></div>

<div itemprop="articleBody">

Browser JavaScript execution flow, as well as in Node.js, is based on an _event loop_.

Understanding how event loop works is important for optimizations, and sometimes for the right architecture.

In this chapter we first cover theoretical details about how things work, and then see practical applications of that knowledge.

## [Event Loop](#event-loop)

The concept of _event loop_ is very simple. There’s an endless loop, when JavaScript engine waits for tasks, executes them and then sleeps waiting for more tasks.

The general algorithm of the engine:

1.  While there are tasks:
    *   execute them, starting with the oldest task.
2.  Sleep until a task appears, then go to 1.

That’s a formalization for what we see when browsing a page. JavaScript engine does nothing most of the time, only runs if a script/handler/event activates.

Examples of tasks:

*   When an external script `<script src="...">` loads, the task is to execute it.
*   When a user moves their mouse, the task is to dispatch `mousemove` event and execute handlers.
*   When the time is due for a scheduled `setTimeout`, the task is to run its callback.
*   …and so on.

Tasks are set – the engine handles them – then waits for more tasks (while sleeping and consuming close to zero CPU).

It may happen that a task comes while the engine is busy, then it’s enqueued.

The tasks form a queue, so-called “macrotask queue” (v8 term):

<figure>

<div class="image" style="width:479px"><object type="image/svg+xml" data="/article/event-loop/eventLoop.svg" width="479" height="279" class="image__image">![](/article/event-loop/eventLoop.svg)</object> </div>

</figure>

For instance, while the engine is busy executing a `script`, a user may move their mouse causing `mousemove`, and `setTimeout` may be due and so on, these tasks form a queue, as illustrated on the picture above.

Tasks from the queue are processed on “first come – first served” basis. When the engine browser is done with the `script`, it handles `mousemove` event, then `setTimeout` handler, and so on.

So far, quite simple, right?

Two more details:

1.  Rendering never happens while the engine executes a task. Doesn’t matter if the task takes a long time. Changes to DOM are painted only after the task is complete.
2.  If a task takes too long, the browser can’t do other tasks, process user events, so after a time it raises an alert like “Page Unresponsive” suggesting to kill the task with the whole page. That happens when there are a lot of complex calculations or a programming error leading to infinite loop.

That was a theory. Now let’s see how we can apply that knowledge.

## [Use-case 1: splitting CPU-hungry tasks](#use-case-1-splitting-cpu-hungry-tasks)

Let’s say we have a CPU-hungry task.

For example, syntax-highlighting (used to colorize code examples on this page) is quite CPU-heavy. To highlight the code, it performs the analysis, creates many colored elements, adds them to the document – for a large amount of text that takes a lot of time.

While the engine is busy with syntax highlighting, it can’t do other DOM-related stuff, process user events, etc. It may even cause the browser to “hiccup” or even “hang” for a bit, which is unacceptable.

We can avoid problems by splitting the big task into pieces. Highlight first 100 lines, then schedule `setTimeout` (with zero-delay) for the next 100 lines, and so on.

To demonstrate this approach, for the sake of simplicity, instead of text-highlighting, let’s take a function that counts from `1` to `1000000000`.

If you run the code below, the engine will “hang” for some time. For server-side JS that’s clearly noticeable, and if you are running it in-browser, then try to click other buttons on the page – you’ll see that no other events get handled until the counting finishes.

<div data-trusted="1" class="code-example">

<div class="codebox code-example__codebox">

<div class="toolbar codebox__toolbar">

<div class="toolbar__tool">[](# "run")</div>

<div class="toolbar__tool">[](# "open in sandbox")</div>

</div>

<div class="codebox__code" data-code="1">

    let i = 0;

    let start = Date.now();

    function count() {

      // do a heavy job
      for (let j = 0; j < 1e9; j++) {
        i++;
      }

      alert("Done in " + (Date.now() - start) + 'ms');
    }

    count();

</div>

</div>

</div>

The browser may even show a “the script takes too long” warning.

Let’s split the job using nested `setTimeout` calls:

<div data-trusted="1" class="code-example">

<div class="codebox code-example__codebox">

<div class="toolbar codebox__toolbar">

<div class="toolbar__tool">[](# "run")</div>

<div class="toolbar__tool">[](# "open in sandbox")</div>

</div>

<div class="codebox__code" data-code="1">

    let i = 0;

    let start = Date.now();

    function count() {

      // do a piece of the heavy job (*)
      do {
        i++;
      } while (i % 1e6 != 0);

      if (i == 1e9) {
        alert("Done in " + (Date.now() - start) + 'ms');
      } else {
        setTimeout(count); // schedule the new call (**)
      }

    }

    count();

</div>

</div>

</div>

Now the browser interface is fully functional during the “counting” process.

A single run of `count` does a part of the job `(*)`, and then re-schedules itself `(**)` if needed:

1.  First run counts: `i=1...1000000`.
2.  Second run counts: `i=1000001..2000000`.
3.  …and so on.

Now, if a new side task (e.g. `onclick` event) appears while the engine is busy executing part 1, it gets queued and then executes when part 1 finished, before the next part. Periodic returns to the event loop between `count` executions provide just enough “air” for the JavaScript engine to do something else, to react to other user actions.

The notable thing is that both variants – with and without splitting the job by `setTimeout` – are comparable in speed. There’s not much difference in the overall counting time.

To make them closer, let’s make an improvement.

We’ll move the scheduling to the beginning of the `count()`:

<div data-trusted="1" class="code-example">

<div class="codebox code-example__codebox">

<div class="toolbar codebox__toolbar">

<div class="toolbar__tool">[](# "run")</div>

<div class="toolbar__tool">[](# "open in sandbox")</div>

</div>

<div class="codebox__code" data-code="1">

    let i = 0;

    let start = Date.now();

    function count() {

      // move the scheduling to the beginning
      if (i < 1e9 - 1e6) {
        setTimeout(count); // schedule the new call
      }

      do {
        i++;
      } while (i % 1e6 != 0);

      if (i == 1e9) {
        alert("Done in " + (Date.now() - start) + 'ms');
      }

    }

    count();

</div>

</div>

</div>

Now when we start to `count()` and see that we’ll need to `count()` more, we schedule that immediately, before doing the job.

If you run it, it’s easy to notice that it takes significantly less time.

Why?

That’s simple: as you remember, there’s the in-browser minimal delay of 4ms for many nested `setTimeout` calls. Even if we set `0`, it’s `4ms` (or a bit more). So the earlier we schedule it – the faster it runs.

Finally, we’ve split a CPU-hungry task into parts – now it doesn’t block the user interface. And its overall execution time isn’t much longer.

## [Use case 2: progress indication](#use-case-2-progress-indication)

Another benefit of splitting heavy tasks for browser scripts is that we can show progress indication.

Usually the browser renders after the currently running code is complete. Doesn’t matter if the task takes a long time. Changes to DOM are painted only after the task is finished.

On one hand, that’s great, because our function may create many elements, add them one-by-one to the document and change their styles – the visitor won’t see any “intermediate”, unfinished state. An important thing, right?

Here’s the demo, the changes to `i` won’t show up until the function finishes, so we’ll see only the last value:

<div data-trusted="1" class="code-example">

<div class="codebox code-example__codebox">

<div class="toolbar codebox__toolbar">

<div class="toolbar__tool">[](# "show")</div>

<div class="toolbar__tool">[](# "open in sandbox")</div>

</div>

<div class="codebox__code" data-code="1">

    <div id="progress"></div>

    <script>

      function count() {
        for (let i = 0; i < 1e6; i++) {
          i++;
          progress.innerHTML = i;
        }
      }

      count();
    </script>

</div>

</div>

</div>

…But we also may want to show something during the task, e.g. a progress bar.

If we split the heavy task into pieces using `setTimeout`, then changes are painted out in-between them.

This looks prettier:

<div data-trusted="1" class="code-example">

<div class="codebox code-example__codebox">

<div class="toolbar codebox__toolbar">

<div class="toolbar__tool">[](# "show")</div>

<div class="toolbar__tool">[](# "open in sandbox")</div>

</div>

<div class="codebox__code" data-code="1">

    <div id="progress"></div>

    <script>
      let i = 0;

      function count() {

        // do a piece of the heavy job (*)
        do {
          i++;
          progress.innerHTML = i;
        } while (i % 1e3 != 0);

        if (i < 1e7) {
          setTimeout(count);
        }

      }

      count();
    </script>

</div>

</div>

</div>

Now the `<div>` shows increasing values of `i`, a kind of a progress bar.

## [Use case 3: doing something after the event](#use-case-3-doing-something-after-the-event)

In an event handler we may decide to postpone some actions until the event bubbled up and was handled on all levels. We can do that by wrapping the code in zero delay `setTimeout`.

In the chapter [Dispatching custom events](/dispatch-events) we saw an example: custom event `menu-open` is dispatched in `setTimeout`, so that it happens after the “click” event is fully handled.

<div data-trusted="1" class="code-example">

<div class="codebox code-example__codebox">

<div class="codebox__code" data-code="1">

    menu.onclick = function() {
      // ...

      // create a custom event with the clicked menu item data
      let customEvent = new CustomEvent("menu-open", {
        bubbles: true
      });

      // dispatch the custom event asynchronously
      setTimeout(() => menu.dispatchEvent(customEvent));
    };

</div>

</div>

</div>

## [Macrotasks and Microtasks](#macrotasks-and-microtasks)

Along with _macrotasks_, described in this chapter, there exist _microtasks_, mentioned in the chapter [Microtasks](/microtask-queue).

Microtasks come solely from our code. They are usually created by promises: an execution of `.then/catch/finally` handler becomes a microtask. Microtasks are used “under the cover” of `await` as well, as it’s another form of promise handling.

There’s also a special function `queueMicrotask(func)` that queues `func` for execution in the microtask queue.

**Immediately after every _macrotask_, the engine executes all tasks from _microtask_ queue, prior to running any other macrotasks or rendering or anything else.**

For instance, take a look:

<div data-trusted="1" class="code-example">

<div class="codebox code-example__codebox">

<div class="toolbar codebox__toolbar">

<div class="toolbar__tool">[](# "run")</div>

<div class="toolbar__tool">[](# "open in sandbox")</div>

</div>

<div class="codebox__code" data-code="1">

    setTimeout(() => alert("timeout"));

    Promise.resolve()
      .then(() => alert("promise"));

    alert("code");

</div>

</div>

</div>

What’s going to be the order here?

1.  `code` shows first, because it’s a regular synchronous call.
2.  `promise` shows second, because `.then` passes through the microtask queue, and runs after the current code.
3.  `timeout` shows last, because it’s a macrotask.

The richer event loop picture looks like this (order is from top to bottom, that is: the script first, then microtasks, rendering and so on):

<figure>

<div class="image" style="width:407px"><object type="image/svg+xml" data="/article/event-loop/eventLoop-full.svg" width="407" height="391" class="image__image">![](/article/event-loop/eventLoop-full.svg)</object> </div>

</figure>

All microtasks are completed before any other event handling or rendering or any other macrotask takes place.

That’s important, as it guarantees that the application environment is basically the same (no mouse coordinate changes, no new network data, etc) between microtasks.

If we’d like to execute a function asynchronously (after the current code), but before changes are rendered or new events handled, we can schedule it with `queueMicrotask`.

Here’s an example with “counting progress bar”, similar to the one shown previously, but `queueMicrotask` is used instead of `setTimeout`. You can see that it renders at the very end. Just like the synchronous code:

<div data-trusted="1" class="code-example" data-highlight="[{&quot;start&quot;:14,&quot;end&quot;:14}]">

<div class="codebox code-example__codebox">

<div class="toolbar codebox__toolbar">

<div class="toolbar__tool">[](# "show")</div>

<div class="toolbar__tool">[](# "open in sandbox")</div>

</div>

<div class="codebox__code" data-code="1">

    <div id="progress"></div>

    <script>
      let i = 0;

      function count() {

        // do a piece of the heavy job (*)
        do {
          i++;
          progress.innerHTML = i;
        } while (i % 1e3 != 0);

        if (i < 1e6) {
          queueMicrotask(count);
        }

      }

      count();
    </script>

</div>

</div>

</div>

## [Summary](#summary)

The more detailed algorithm of the event loop (though still simplified compare to the [specification](https://html.spec.whatwg.org/multipage/webappapis.html#event-loop-processing-model)):

1.  Dequeue and run the oldest task from the _macrotask_ queue (e.g. “script”).
2.  Execute all _microtasks_:
    *   While the microtask queue is not empty:
        *   Dequeue and run the oldest microtask.
3.  Render changes if any.
4.  If the macrotask queue is empty, wait till a macrotask appears.
5.  Go to step 1.

To schedule a new _macrotask_:

*   Use zero delayed `setTimeout(f)`.

That may be used to split a big calculation-heavy task into pieces, for the browser to be able to react on user events and show progress between them.

Also, used in event handlers to schedule an action after the event is fully handled (bubbling done).

To schedule a new _microtask_

*   Use `queueMicrotask(f)`.
*   Also promise handlers go through the microtask queue.

There’s no UI or network event handling between microtasks: they run immediately one after another.

So one may want to `queueMicrotask` to execute a function asynchronously, but within the environment state.

<div class="important important_smart">

<div class="important__header"><span class="important__type">Web Workers</span></div>

<div class="important__content">

For long heavy calculations that shouldn’t block the event loop, we can use [Web Workers](https://html.spec.whatwg.org/multipage/workers.html).

That’s a way to run code in another, parallel thread.

Web Workers can exchange messages with the main process, but they have their own variables, and their own event loop.

Web Workers do not have access to DOM, so they are useful, mainly, for calculations, to use multiple CPU cores simultaneously.

</div>

</div>

</div>

</article>

</div>

<div class="page__nav-wrap">[<span class="page__nav-text"><span class="page__nav-text-shortcut"></span></span><span class="page__nav-text-alternate">Previous lesson</span>](/selection-range)[<span class="page__nav-text"><span class="page__nav-text-shortcut"></span></span><span class="page__nav-text-alternate">Next lesson</span>](/frames-and-windows)</div>

<div class="article-tablet-foot tablet-only">

<div class="article-tablet-foot__layout">

<div class="share-icons"><span class="share-icons__title">Share</span>[](https://twitter.com/share?url=https%3A%2F%2Fjavascript.info%2Fevent-loop)[](https://www.facebook.com/sharer/sharer.php?s=100&p%5Burl%5D=https%3A%2F%2Fjavascript.info%2Fevent-loop)</div>

<div class="article-tablet-foot__map">[<span class="map__text">Tutorial map</span>](/tutorial/map)</div>

</div>

</div>

<div class="comments formatted" id="comments">

<div class="comments__header">

## [Comments](#comments)

<div class="comments__read-before"><span class="comments__read-before-link">read this before commenting…</span>

<div class="comments__read-before-popup">

<div class="comments__read-before-popup-i">

*   If you have suggestions what to improve - please [submit a GitHub issue](https://github.com/javascript-tutorial/en.javascript.info/issues/new) or a pull request instead of commenting.
*   If you can't understand something in the article – please elaborate.
*   To insert few words of code, use the `<code>` tag, for several lines – wrap them in `<pre>` tag, for more than 10 lines – use a sandbox ([plnkr](https://plnkr.co/edit/?p=preview), [jsbin](https://jsbin.com), [codepen](http://codepen.io)…)

</div>

</div>

</div>

</div>

<script>var disqus_config = function() { if (!this.page) this.page = {}; Object.assign(this.page, {"url":"https:\/\/javascript.info\/event-loop","identifier":"\/event-loop"}); };</script><script>var disqus_shortname = "javascriptinfo";</script><script>var disqus_enabled = true;</script></div>

</main>

</div>

<div class="sidebar page__sidebar sidebar sidebar_sticky-footer">[](/tutorial/map)

<div class="sidebar__inner">

<div class="sidebar__content">

<div class="sidebar__section">

#### Chapter

<nav class="sidebar__navigation">

*   [Miscellaneous](/ui-misc)

</nav>

</div>

<div class="sidebar__section">

#### Lesson navigation

<nav class="sidebar__navigation">

*   [Event Loop](#event-loop)
*   [Use-case 1: splitting CPU-hungry tasks](#use-case-1-splitting-cpu-hungry-tasks)
*   [Use case 2: progress indication](#use-case-2-progress-indication)
*   [Use case 3: doing something after the event](#use-case-3-doing-something-after-the-event)
*   [Macrotasks and Microtasks](#macrotasks-and-microtasks)
*   [Summary](#summary)

</nav>

</div>

<div class="sidebar__section">

<nav class="sidebar__navigation">

*   [Comments](#comments)

</nav>

</div>

<div class="sidebar__section">

<div class="sidebar__section-title">Share</div>

[](https://twitter.com/share?url=https%3A%2F%2Fjavascript.info%2Fevent-loop)[](https://www.facebook.com/sharer/sharer.php?s=100&p[url]=https%3A%2F%2Fjavascript.info%2Fevent-loop)</div>

<div class="sidebar__section">[Edit on GitHub](https://github.com/javascript-tutorial/en.javascript.info/blob/master/2-ui/99-ui-misc/03-event-loop)</div>

<div class="sidebar__section" id="sponsorBar">

<div class="sidebar__section-title">Ads via Carbon</div>

<script>window.initSponsorBar()</script></div>

</div>

</div>

</div>

</div>

</div>

<div class="page-footer">

*   © 2007—2020  Ilya Kantor
*   [about the project](/about)
*   [contact us](/about#contact-us)
*   [terms of usage](/terms)
*   [privacy policy](/privacy)

</div>
