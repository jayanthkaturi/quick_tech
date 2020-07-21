<nav class="navbar fixed-top navbar-expand-lg navbar-dark flex-column nav-message">

<div class="container flex-row">[![Real Python](/static/real-python-logo.893c30edea53.svg) ](/) <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation"><span class="navbar-toggler-icon"></span></button> 

<div class="collapse navbar-collapse" id="navbarSupportedContent">

*   [Start Here](/start-here/)
*   [<span class="fa fa-graduation-cap"></span>Learn Python](#)

    <div class="dropdown-menu" aria-labelledby="navbarDropdownLibrary">[Python Tutorials →  
    <small class="text-secondary">In-depth articles and tutorials</small>](/) [Video Courses →  
    <small class="text-secondary">Step-by-step video lessons</small>](/courses/) [Quizzes →  
    <small class="text-secondary">Check your learning progress</small>](/quizzes/) [Learning Paths →  
    <small class="text-secondary">Guided study plans for accelerated learning</small>](/learning-paths/) [Community →  
    <small class="text-secondary">Learn with other Pythonistas</small>](/community/) [Topics →  
    <small class="text-secondary">Focus on a specific area or skill level</small>](/tutorials/all/) [Unlock All Content](/account/join/)</div>

*   [Store](#)

    <div class="dropdown-menu" aria-labelledby="navbarDropdownBooksCourses">[RP Membership](/account/join/) [Python Basics Book](/products/python-basics-book/) [Python Tricks Book](/products/python-tricks-book/) [CPython Internals Book](/products/cpython-internals-book/) [The Real Python Course](/products/real-python-course/) [Managing Python Dependencies](/products/managing-python-dependencies/) [Sublime Text + Python Setup](/products/sublime-python/) [Pythonic Wallpapers Pack](/products/pythonic-wallpapers/) [Python Mugs, T-Shirts, and More](https://nerdlettering.com) [Pythonista Cafe Community](https://www.pythonistacafe.com) [Browse All »](/products/)</div>

*   [More](#)

    <div class="dropdown-menu" aria-labelledby="navbarDropdownMore">[Python Newsletter](/newsletter/) [Python Podcast](/podcasts/rpp/) [Python Job Board](https://www.pythonjobshq.com) [Meet the Team](/team/) [Become a Tutorial Author](/write-for-us/) [Become a Video Instructor](/become-an-instructor/)</div>

<div class="d-block d-xl-none">

*   [<span class="d-block d-lg-none">Search</span><span class="d-none d-lg-block"></span>](/search "Search")

</div>

<div class="d-none d-xl-flex align-items-center mr-2">

<form class="form-inline" action="/search" method="GET">[](/search "Search")<input class="search-field form-control form-control-md mr-sm-1 mr-lg-2 w-100" style="padding-left: 2rem;" maxlength="50" type="search" placeholder="Search" aria-label="Search" name="q"> <input type="hidden" name="_from" value="nav"></form>

</div>

*   [Join](/account/join/)
*   [Sign‑In](/account/login/)

</div>

</div>

<div class="flex-row w-100" style="border-top: 1px dashed #ffc107 !important;">

<div class="container">[

<span class="text-warning">😷**Stuck at home?** Enjoy free courses, on us →</span>

](https://realpython.com/free-courses-march-2020)</div>

</div>

</nav>

<div class="container main-content">

<div class="row justify-content-center">

<div class="col-md-11 col-lg-8 article">

<figure class="embed-responsive embed-responsive-16by9">![Getting Started With Testing in Python](https://files.realpython.com/media/Getting-Started-with-Testing-in-Python_Watermarked.9f22be97343d.jpg)</figure>

# Getting Started With Testing in Python

<span class="text-muted">by [Anthony Shaw](#author) <span class="ml-2 mr-1 fa fa-comments"></span>[<span class="disqus-comment-count" data-disqus-identifier="https://realpython.com/python-testing/"></span>](#reader-comments)<span class="ml-2 fa fa-tags"></span>[best-practices](/tutorials/best-practices/) [intermediate](/tutorials/intermediate/) [testing](/tutorials/testing/)</span>

<div class="d-flex flex-row justify-content-between my-2">

<div class="align-self-center"><span>[Tweet](https://twitter.com/intent/tweet/?text=Check out this %23Python tutorial: Getting%20Started%20With%20Testing%20in%20Python by @realpython&url=https%3A//realpython.com/python-testing/) [Share](https://facebook.com/sharer/sharer.php?u=https%3A//realpython.com/python-testing/) [Email](mailto:?subject=Python article for you&body=Check out this Python tutorial:%0A%0AGetting%20Started%20With%20Testing%20in%20Python%0A%0Ahttps%3A//realpython.com/python-testing/)</span></div>

</div>

<div class="article-body">

<div class="bg-light sidebar-module sidebar-module-inset" id="toc">

Table of Contents

<div class="toc">

*   [Testing Your Code](#testing-your-code)
    *   [Automated vs. Manual Testing](#automated-vs-manual-testing)
    *   [Unit Tests vs. Integration Tests](#unit-tests-vs-integration-tests)
    *   [Choosing a Test Runner](#choosing-a-test-runner)
*   [Writing Your First Test](#writing-your-first-test)
    *   [Where to Write the Test](#where-to-write-the-test)
    *   [How to Structure a Simple Test](#how-to-structure-a-simple-test)
    *   [How to Write Assertions](#how-to-write-assertions)
    *   [Side Effects](#side-effects)
*   [Executing Your First Test](#executing-your-first-test)
    *   [Executing Test Runners](#executing-test-runners)
    *   [Understanding Test Output](#understanding-test-output)
    *   [Running Your Tests From PyCharm](#running-your-tests-from-pycharm)
    *   [Running Your Tests From Visual Studio Code](#running-your-tests-from-visual-studio-code)
*   [Testing for Web Frameworks Like Django and Flask](#testing-for-web-frameworks-like-django-and-flask)
    *   [Why They’re Different From Other Applications](#why-theyre-different-from-other-applications)
    *   [How to Use the Django Test Runner](#how-to-use-the-django-test-runner)
    *   [How to Use unittest and Flask](#how-to-use-unittest-and-flask)
*   [More Advanced Testing Scenarios](#more-advanced-testing-scenarios)
    *   [Handling Expected Failures](#handling-expected-failures)
    *   [Isolating Behaviors in Your Application](#isolating-behaviors-in-your-application)
    *   [Writing Integration Tests](#writing-integration-tests)
    *   [Testing Data-Driven Applications](#testing-data-driven-applications)
*   [Testing in Multiple Environments](#testing-in-multiple-environments)
    *   [Installing Tox](#installing-tox)
    *   [Configuring Tox for Your Dependencies](#configuring-tox-for-your-dependencies)
    *   [Executing Tox](#executing-tox)
*   [Automating the Execution of Your Tests](#automating-the-execution-of-your-tests)
*   [What’s Next](#whats-next)
    *   [Introducing Linters Into Your Application](#introducing-linters-into-your-application)
    *   [Keeping Your Test Code Clean](#keeping-your-test-code-clean)
    *   [Testing for Performance Degradation Between Changes](#testing-for-performance-degradation-between-changes)
    *   [Testing for Security Flaws in Your Application](#testing-for-security-flaws-in-your-application)
*   [Conclusion](#conclusion)

</div>

</div>

<div class="border rounded p-3 card mb-2">

<span class="badge badge-pill badge-success">Watch Now</span> This tutorial has a related video course created by the Real Python team. Watch it together with the written tutorial to deepen your understanding: [**Test-Driven Development With PyTest**](/courses/test-driven-development-pytest/)

</div>

This tutorial is for anyone who has written a fantastic application in Python but hasn’t yet written any tests.

Testing in Python is a huge topic and can come with a lot of complexity, but it doesn’t need to be hard. You can get started creating simple tests for your application in a few easy steps and then build on it from there.

In this tutorial, you’ll learn how to create a basic test, execute it, and find the bugs before your users do! You’ll learn about the tools available to write and execute tests, check your application’s performance, and even look for security issues.

<div class="alert alert-warning" role="alert">

**Free Bonus:** [5 Thoughts On Python Mastery](https://realpython.com/bonus/python-mastery-course/), a free course for Python developers that shows you the roadmap and the mindset you'll need to take your Python skills to the next level.

</div>

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

<section class="section2" id="testing-your-code">

## Testing Your Code

There are many ways to test your code. In this tutorial, you’ll learn the techniques from the most basic steps and work towards advanced methods.

<section class="section3" id="automated-vs-manual-testing">

### Automated vs. Manual Testing

The good news is, you’ve probably already created a test without realizing it. Remember when you ran your application and used it for the first time? Did you check the features and experiment using them? That’s known as **exploratory testing** and is a form of manual testing.

Exploratory testing is a form of testing that is done without a plan. In an exploratory test, you’re just exploring the application.

To have a complete set of manual tests, all you need to do is make a list of all the features your application has, the different types of input it can accept, and the expected results. Now, every time you make a change to your code, you need to go through every single item on that list and check it.

That doesn’t sound like much fun, does it?

This is where automated testing comes in. Automated testing is the execution of your test plan (the parts of your application you want to test, the order in which you want to test them, and the expected responses) by a script instead of a human. Python already comes with a set of tools and libraries to help you create automated tests for your application. We’ll explore those tools and libraries in this tutorial.

</section>

<section class="section3" id="unit-tests-vs-integration-tests">

### Unit Tests vs. Integration Tests

The world of testing has no shortage of terminology, and now that you know the difference between automated and manual testing, it’s time to go a level deeper.

Think of how you might test the lights on a car. You would turn on the lights (known as the **test step**) and go outside the car or ask a friend to check that the lights are on (known as the **test assertion**). Testing multiple components is known as **integration testing**.

Think of all the things that need to work correctly in order for a simple task to give the right result. These components are like the parts to your application, all of those classes, functions, and modules you’ve written.

A major challenge with integration testing is when an integration test doesn’t give the right result. It’s very hard to diagnose the issue without being able to isolate which part of the system is failing. If the lights didn’t turn on, then maybe the bulbs are broken. Is the battery dead? What about the alternator? Is the car’s computer failing?

If you have a fancy modern car, it will tell you when your light bulbs have gone. It does this using a form of **unit test**.

A unit test is a smaller test, one that checks that a single component operates in the right way. A unit test helps you to isolate what is broken in your application and fix it faster.

You have just seen two types of tests:

1.  An integration test checks that components in your application operate with each other.
2.  A unit test checks a small component in your application.

You can write both integration tests and unit tests in Python. To write a unit test for the built-in function `sum()`, you would check the output of `sum()` against a known output.

For example, here’s how you check that the `sum()` of the numbers `(1, 2, 3)` equals `6`:

<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">>>></span>

<pre><span></span>`<span class="gp">>>></span> <span class="k">assert</span> <span class="nb">sum</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">])</span> <span class="o">==</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span>` </pre>

</div>

This will not output anything on the REPL because the values are correct.

If the result from `sum()` is incorrect, this will fail with an `AssertionError` and the message `"Should be 6"`. Try an assertion statement again with the wrong values to see an `AssertionError`:

<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">>>></span>

<pre><span></span>`<span class="gp">>>></span> <span class="k">assert</span> <span class="nb">sum</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">])</span> <span class="o">==</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span>
<span class="gt">Traceback (most recent call last):</span>
  File <span class="nb">"<stdin>"</span>, line <span class="m">1</span>, in <span class="n"><module></span>
<span class="gr">AssertionError</span>: <span class="n">Should be 6</span>` </pre>

</div>

In the REPL, you are seeing the raised `AssertionError` because the result of `sum()` does not match `6`.

Instead of testing on the REPL, you’ll want to put this into a new Python file called `test_sum.py` and execute it again:

<div class="highlight python">

<pre><span></span>`<span class="k">def</span> <span class="nf">test_sum</span><span class="p">():</span>
    <span class="k">assert</span> <span class="nb">sum</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">])</span> <span class="o">==</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span>

<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s2">"__main__"</span><span class="p">:</span>
    <span class="n">test_sum</span><span class="p">()</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"Everything passed"</span><span class="p">)</span>` </pre>

</div>

Now you have written a **test case**, an assertion, and an entry point (the command line). You can now execute this at the command line:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python test_sum.py
<span class="go">Everything passed</span>` </pre>

</div>

You can see the successful result, `Everything passed`.

In Python, `sum()` accepts any iterable as its first argument. You tested with a list. Now test with a tuple as well. Create a new file called `test_sum_2.py` with the following code:

<div class="highlight python">

<pre><span></span>`<span class="k">def</span> <span class="nf">test_sum</span><span class="p">():</span>
    <span class="k">assert</span> <span class="nb">sum</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">])</span> <span class="o">==</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span>

<span class="k">def</span> <span class="nf">test_sum_tuple</span><span class="p">():</span>
    <span class="k">assert</span> <span class="nb">sum</span><span class="p">((</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">2</span><span class="p">))</span> <span class="o">==</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span>

<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s2">"__main__"</span><span class="p">:</span>
    <span class="n">test_sum</span><span class="p">()</span>
    <span class="n">test_sum_tuple</span><span class="p">()</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"Everything passed"</span><span class="p">)</span>` </pre>

</div>

When you execute `test_sum_2.py`, the script will give an error because the `sum()` of `(1, 2, 2)` is `5`, not `6`. The result of the script gives you the error message, the line of code, and the traceback:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python test_sum_2.py
<span class="go">Traceback (most recent call last):</span>
 <span class="go">File "test_sum_2.py", line 9, in <module></span>
 <span class="go">test_sum_tuple()</span>
 <span class="go">File "test_sum_2.py", line 5, in test_sum_tuple</span>
 <span class="go">assert sum((1, 2, 2)) == 6, "Should be 6"</span>
<span class="go">AssertionError: Should be 6</span>` </pre>

</div>

Here you can see how a mistake in your code gives an error on the console with some information on where the error was and what the expected result was.

Writing tests in this way is okay for a simple check, but what if more than one fails? This is where test runners come in. The test runner is a special application designed for running tests, checking the output, and giving you tools for debugging and diagnosing tests and applications.

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

<section class="section3" id="choosing-a-test-runner">

### Choosing a Test Runner

There are many test runners available for Python. The one built into the Python standard library is called `unittest`. In this tutorial, you will be using `unittest` test cases and the `unittest` test runner. The principles of `unittest` are easily portable to other frameworks. The three most popular test runners are:

*   `unittest`
*   `nose` or `nose2`
*   `pytest`

Choosing the best test runner for your requirements and level of experience is important.

<section class="section4" id="unittest">

#### `unittest`

`unittest` has been built into the Python standard library since version 2.1\. You’ll probably see it in commercial Python applications and open-source projects.

`unittest` contains both a testing framework and a test runner. `unittest` has some important requirements for writing and executing tests.

`unittest` requires that:

*   You put your tests into classes as methods
*   You use a series of special assertion methods in the `unittest.TestCase` class instead of the built-in `assert` statement

To convert the earlier example to a `unittest` test case, you would have to:

1.  [Import](https://realpython.com/absolute-vs-relative-python-imports/) `unittest` from the standard library
2.  Create a class called `TestSum` that inherits from the `TestCase` class
3.  Convert the test functions into methods by adding `self` as the first argument
4.  Change the assertions to use the `self.assertEqual()` method on the `TestCase` class
5.  Change the command-line entry point to call `unittest.main()`

Follow those steps by creating a new file `test_sum_unittest.py` with the following code:

<div class="highlight python">

<pre><span></span>`<span class="kn">import</span> <span class="nn">unittest</span>

<span class="k">class</span> <span class="nc">TestSum</span><span class="p">(</span><span class="n">unittest</span><span class="o">.</span><span class="n">TestCase</span><span class="p">):</span>

    <span class="k">def</span> <span class="nf">test_sum</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="nb">sum</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">]),</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span><span class="p">)</span>

    <span class="k">def</span> <span class="nf">test_sum_tuple</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="nb">sum</span><span class="p">((</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">2</span><span class="p">)),</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span><span class="p">)</span>

<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s1">'__main__'</span><span class="p">:</span>
    <span class="n">unittest</span><span class="o">.</span><span class="n">main</span><span class="p">()</span>` </pre>

</div>

If you execute this at the command line, you’ll see one success (indicated with `.`) and one failure (indicated with `F`):

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python test_sum_unittest.py
<span class="go">.F</span>
<span class="go">======================================================================</span>
<span class="go">FAIL: test_sum_tuple (__main__.TestSum)</span>
<span class="go">----------------------------------------------------------------------</span>
<span class="go">Traceback (most recent call last):</span>
 <span class="go">File "test_sum_unittest.py", line 9, in test_sum_tuple</span>
 <span class="go">self.assertEqual(sum((1, 2, 2)), 6, "Should be 6")</span>
<span class="go">AssertionError: Should be 6</span>

<span class="go">----------------------------------------------------------------------</span>
<span class="go">Ran 2 tests in 0.001s</span>

<span class="go">FAILED (failures=1)</span>` </pre>

</div>

You have just executed two tests using the `unittest` test runner.

<div class="alert alert-primary" role="alert">

**Note:** Be careful if you’re writing test cases that need to execute in both Python 2 and 3\. In Python 2.7 and below, `unittest` is called `unittest2`. If you simply [import](https://realpython.com/python-import/) from `unittest`, you will get different versions with different features between Python 2 and 3.

</div>

For more information on `unittest`, you can explore the [unittest Documentation](https://docs.python.org/3/library/unittest.html).

</section>

<section class="section4" id="nose">

#### `nose`

You may find that over time, as you write hundreds or even thousands of tests for your application, it becomes increasingly hard to understand and use the output from `unittest`.

`nose` is compatible with any tests written using the `unittest` framework and can be used as a drop-in replacement for the `unittest` test runner. The development of `nose` as an open-source application fell behind, and a fork called `nose2` was created. If you’re starting from scratch, it is recommended that you use `nose2` instead of `nose`.

To get started with `nose2`, install `nose2` from PyPI and execute it on the command line. `nose2` will try to discover all test scripts named `test*.py` and test cases inheriting from `unittest.TestCase` in your current directory:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> pip install nose2
<span class="gp">$</span> python -m nose2
<span class="go">.F</span>
<span class="go">======================================================================</span>
<span class="go">FAIL: test_sum_tuple (__main__.TestSum)</span>
<span class="go">----------------------------------------------------------------------</span>
<span class="go">Traceback (most recent call last):</span>
 <span class="go">File "test_sum_unittest.py", line 9, in test_sum_tuple</span>
 <span class="go">self.assertEqual(sum((1, 2, 2)), 6, "Should be 6")</span>
<span class="go">AssertionError: Should be 6</span>

<span class="go">----------------------------------------------------------------------</span>
<span class="go">Ran 2 tests in 0.001s</span>

<span class="go">FAILED (failures=1)</span>` </pre>

</div>

You have just executed the test you created in `test_sum_unittest.py` from the `nose2` test runner. `nose2` offers many command-line flags for filtering the tests that you execute. For more information, you can explore the [Nose 2 documentation](https://nose2.readthedocs.io/).

</section>

<section class="section4" id="pytest">

#### `pytest`

[`pytest`](https://realpython.com/pytest-python-testing/) supports execution of `unittest` test cases. The real advantage of `pytest` comes by writing `pytest` test cases. `pytest` test cases are a series of functions in a Python file starting with the name `test_`.

`pytest` has some other great features:

*   Support for the built-in `assert` statement instead of using special `self.assert*()` methods
*   Support for filtering for test cases
*   Ability to rerun from the last failing test
*   An ecosystem of hundreds of plugins to extend the functionality

Writing the `TestSum` test case example for `pytest` would look like this:

<div class="highlight python">

<pre><span></span>`<span class="k">def</span> <span class="nf">test_sum</span><span class="p">():</span>
    <span class="k">assert</span> <span class="nb">sum</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">])</span> <span class="o">==</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span>

<span class="k">def</span> <span class="nf">test_sum_tuple</span><span class="p">():</span>
    <span class="k">assert</span> <span class="nb">sum</span><span class="p">((</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">2</span><span class="p">))</span> <span class="o">==</span> <span class="mi">6</span><span class="p">,</span> <span class="s2">"Should be 6"</span>` </pre>

</div>

You have dropped the `TestCase`, any use of classes, and the command-line entry point.

More information can be found at the [Pytest Documentation Website](https://docs.pytest.org/en/latest/).

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

</section>

</section>

<section class="section2" id="writing-your-first-test">

## Writing Your First Test

Let’s bring together what you’ve learned so far and, instead of testing the built-in `sum()` function, test a simple implementation of the same requirement.

Create a new project folder and, inside that, create a new folder called `my_sum`. Inside `my_sum`, create an empty file called `__init__.py`. Creating the `__init__.py` file means that the `my_sum` folder can be imported as a module from the parent directory.

Your project folder should look like this:

<div class="highlight">

<pre><span></span>`project/
│
└── my_sum/
    └── __init__.py` </pre>

</div>

Open up `my_sum/__init__.py` and create a new function called `sum()`, which takes an iterable (a list, tuple, or set) and adds the values together:

<div class="highlight python">

<pre><span></span>`<span class="k">def</span> <span class="nf">sum</span><span class="p">(</span><span class="n">arg</span><span class="p">):</span>
    <span class="n">total</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="k">for</span> <span class="n">val</span> <span class="ow">in</span> <span class="n">arg</span><span class="p">:</span>
        <span class="n">total</span> <span class="o">+=</span> <span class="n">val</span>
    <span class="k">return</span> <span class="n">total</span>` </pre>

</div>

This code example creates a variable called `total`, iterates over all the values in `arg`, and adds them to `total`. It then returns the result once the iterable has been exhausted.

<section class="section3" id="where-to-write-the-test">

### Where to Write the Test

To get started writing tests, you can simply create a file called `test.py`, which will contain your first test case. Because the file will need to be able to import your application to be able to test it, you want to place `test.py` above the package folder, so your directory tree will look something like this:

<div class="highlight">

<pre><span></span>`project/
│
├── my_sum/
│   └── __init__.py
|
└── test.py` </pre>

</div>

You’ll find that, as you add more and more tests, your single file will become cluttered and hard to maintain, so you can create a folder called `tests/` and split the tests into multiple files. It is convention to ensure each file starts with `test_` so all test runners will assume that Python file contains tests to be executed. Some very large projects split tests into more subdirectories based on their purpose or usage.

<div class="alert alert-primary" role="alert">

**Note:** What if your application is a single script?

You can import any attributes of the script, such as classes, functions, and variables by using the built-in `__import__()` function. Instead of `from my_sum import sum`, you can write the following:

<div class="highlight python">

<pre><span></span>`<span class="n">target</span> <span class="o">=</span> <span class="nb">__import__</span><span class="p">(</span><span class="s2">"my_sum.py"</span><span class="p">)</span>
<span class="nb">sum</span> <span class="o">=</span> <span class="n">target</span><span class="o">.</span><span class="n">sum</span>` </pre>

</div>

The benefit of using `__import__()` is that you don’t have to turn your project folder into a package, and you can specify the file name. This is also useful if your filename collides with any standard library packages. For example, `math.py` would collide with the `math` module.

</div>

</section>

<section class="section3" id="how-to-structure-a-simple-test">

### How to Structure a Simple Test

Before you dive into writing tests, you’ll want to first make a couple of decisions:

1.  What do you want to test?
2.  Are you writing a unit test or an integration test?

Then the structure of a test should loosely follow this workflow:

1.  Create your inputs
2.  Execute the code being tested, capturing the output
3.  Compare the output with an expected result

For this application, you’re testing `sum()`. There are many behaviors in `sum()` you could check, such as:

*   Can it sum a list of whole numbers (integers)?
*   Can it sum a tuple or set?
*   Can it sum a list of floats?
*   What happens when you provide it with a bad value, such as a single integer or a string?
*   What happens when one of the values is negative?

The most simple test would be a list of integers. Create a file, `test.py` with the following Python code:

<div class="highlight python">

<pre><span></span>`<span class="kn">import</span> <span class="nn">unittest</span>

<span class="kn">from</span> <span class="nn">my_sum</span> <span class="kn">import</span> <span class="nb">sum</span>

<span class="k">class</span> <span class="nc">TestSum</span><span class="p">(</span><span class="n">unittest</span><span class="o">.</span><span class="n">TestCase</span><span class="p">):</span>
    <span class="k">def</span> <span class="nf">test_list_int</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="sd">"""</span>
 <span class="sd">Test that it can sum a list of integers</span>
 <span class="sd">"""</span>
        <span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">]</span>
        <span class="n">result</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">data</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">result</span><span class="p">,</span> <span class="mi">6</span><span class="p">)</span>

<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s1">'__main__'</span><span class="p">:</span>
    <span class="n">unittest</span><span class="o">.</span><span class="n">main</span><span class="p">()</span>` </pre>

</div>

This code example:

1.  Imports `sum()` from the `my_sum` package you created

2.  Defines a new test case class called `TestSum`, which inherits from `unittest.TestCase`

3.  Defines a test method, `.test_list_int()`, to test a list of integers. The method `.test_list_int()` will:

    *   Declare a variable `data` with a list of numbers `(1, 2, 3)`
    *   Assign the result of `my_sum.sum(data)` to a `result` variable
    *   Assert that the value of `result` equals `6` by using the `.assertEqual()` method on the `unittest.TestCase` class
4.  Defines a command-line entry point, which runs the `unittest` test-runner `.main()`

If you’re unsure what `self` is or how `.assertEqual()` is defined, you can brush up on your object-oriented programming with [Python 3 Object-Oriented Programming](https://realpython.com/python3-object-oriented-programming/).

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

<section class="section3" id="how-to-write-assertions">

### How to Write Assertions

The last step of writing a test is to validate the output against a known response. This is known as an **assertion**. There are some general best practices around how to write assertions:

*   Make sure tests are repeatable and run your test multiple times to make sure it gives the same result every time
*   Try and assert results that relate to your input data, such as checking that the result is the actual sum of values in the `sum()` example

`unittest` comes with lots of methods to assert on the values, types, and existence of variables. Here are some of the most commonly used methods:

<div class="table-responsive">

<table class="table table-hover">

<thead>

<tr>

<th>Method</th>

<th>Equivalent to</th>

</tr>

</thead>

<tbody>

<tr>

<td>`.assertEqual(a, b)`</td>

<td>`a == b`</td>

</tr>

<tr>

<td>`.assertTrue(x)`</td>

<td>`bool(x) is True`</td>

</tr>

<tr>

<td>`.assertFalse(x)`</td>

<td>`bool(x) is False`</td>

</tr>

<tr>

<td>`.assertIs(a, b)`</td>

<td>`a is b`</td>

</tr>

<tr>

<td>`.assertIsNone(x)`</td>

<td>`x is None`</td>

</tr>

<tr>

<td>`.assertIn(a, b)`</td>

<td>`a in b`</td>

</tr>

<tr>

<td>`.assertIsInstance(a, b)`</td>

<td>`isinstance(a, b)`</td>

</tr>

</tbody>

</table>

</div>

`.assertIs()`, `.assertIsNone()`, `.assertIn()`, and `.assertIsInstance()` all have opposite methods, named `.assertIsNot()`, and so forth.

</section>

<section class="section3" id="side-effects">

### Side Effects

When you’re writing tests, it’s often not as simple as looking at the return value of a function. Often, executing a piece of code will alter other things in the environment, such as the attribute of a class, a file on the filesystem, or a value in a database. These are known as **side effects** and are an important part of testing. Decide if the side effect is being tested before including it in your list of assertions.

If you find that the unit of code you want to test has lots of side effects, you might be breaking the [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). Breaking the Single Responsibility Principle means the piece of code is doing too many things and would be better off being refactored. Following the Single Responsibility Principle is a great way to design code that it is easy to write repeatable and simple unit tests for, and ultimately, reliable applications.

</section>

</section>

<section class="section2" id="executing-your-first-test">

## Executing Your First Test

Now that you’ve created the first test, you want to execute it. Sure, you know it’s going to pass, but before you create more complex tests, you should check that you can execute the tests successfully.

<section class="section3" id="executing-test-runners">

### Executing Test Runners

The Python application that executes your test code, checks the assertions, and gives you test results in your console is called the **test runner**.

At the bottom of `test.py`, you added this small snippet of code:

<div class="highlight python">

<pre><span></span>`<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s1">'__main__'</span><span class="p">:</span>
    <span class="n">unittest</span><span class="o">.</span><span class="n">main</span><span class="p">()</span>` </pre>

</div>

This is a command line entry point. It means that if you execute the script alone by running `python test.py` at the command line, it will call `unittest.main()`. This executes the test runner by discovering all classes in this file that inherit from `unittest.TestCase`.

This is one of many ways to execute the `unittest` test runner. When you have a single test file named `test.py`, calling `python test.py` is a great way to get started.

Another way is using the `unittest` command line. Try this:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python -m unittest <span class="nb">test</span>` </pre>

</div>

This will execute the same test module (called `test`) via the command line.

You can provide additional options to change the output. One of those is `-v` for verbose. Try that next:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python -m unittest -v <span class="nb">test</span>
<span class="go">test_list_int (test.TestSum) ... ok</span>

<span class="go">----------------------------------------------------------------------</span>
<span class="go">Ran 1 tests in 0.000s</span>` </pre>

</div>

This executed the one test inside `test.py` and printed the results to the console. Verbose mode listed the names of the tests it executed first, along with the result of each test.

Instead of providing the name of a module containing tests, you can request an auto-discovery using the following:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python -m unittest discover` </pre>

</div>

This will search the current directory for any files named `test*.py` and attempt to test them.

Once you have multiple test files, as long as you follow the `test*.py` naming pattern, you can provide the name of the directory instead by using the `-s` flag and the name of the directory:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python -m unittest discover -s tests` </pre>

</div>

`unittest` will run all tests in a single test plan and give you the results.

Lastly, if your source code is not in the directory root and contained in a subdirectory, for example in a folder called `src/`, you can tell `unittest` where to execute the tests so that it can import the modules correctly with the `-t` flag:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python -m unittest discover -s tests -t src` </pre>

</div>

`unittest` will change to the `src/` directory, scan for all `test*.py` files inside the the `tests` directory, and execute them.

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

<section class="section3" id="understanding-test-output">

### Understanding Test Output

That was a very simple example where everything passes, so now you’re going to try a failing test and interpret the output.

`sum()` should be able to accept other lists of numeric types, like fractions.

At the top of the `test.py` file, add an import statement to import the `Fraction` type from the `fractions` module in the standard library:

<div class="highlight python">

<pre><span></span>`<span class="kn">from</span> <span class="nn">fractions</span> <span class="kn">import</span> <span class="n">Fraction</span>` </pre>

</div>

Now add a test with an assertion expecting the incorrect value, in this case expecting the sum of 1/4, 1/4, and 2/5 to be 1:

<div class="highlight python">

<pre><span></span>`<span class="kn">import</span> <span class="nn">unittest</span>

<span class="kn">from</span> <span class="nn">my_sum</span> <span class="kn">import</span> <span class="nb">sum</span>

<span class="k">class</span> <span class="nc">TestSum</span><span class="p">(</span><span class="n">unittest</span><span class="o">.</span><span class="n">TestCase</span><span class="p">):</span>
    <span class="k">def</span> <span class="nf">test_list_int</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="sd">"""</span>
 <span class="sd">Test that it can sum a list of integers</span>
 <span class="sd">"""</span>
        <span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">]</span>
        <span class="n">result</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">data</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">result</span><span class="p">,</span> <span class="mi">6</span><span class="p">)</span>

 <span class="hll"><span class="k">def</span> <span class="nf">test_list_fraction</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span></span> <span class="hll"><span class="sd">"""</span></span><span class="hll"> <span class="sd">Test that it can sum a list of fractions</span>
</span><span class="hll"> <span class="sd">"""</span>
</span> <span class="hll"><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="n">Fraction</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">),</span> <span class="n">Fraction</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">),</span> <span class="n">Fraction</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span> <span class="mi">5</span><span class="p">)]</span></span> <span class="hll"><span class="n">result</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">data</span><span class="p">)</span></span> <span class="hll"><span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">result</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span></span> 
<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s1">'__main__'</span><span class="p">:</span>
    <span class="n">unittest</span><span class="o">.</span><span class="n">main</span><span class="p">()</span>` </pre>

</div>

If you execute the tests again with `python -m unittest test`, you should see the following output:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python -m unittest <span class="nb">test</span>
<span class="go">F.</span>
<span class="go">======================================================================</span>
<span class="go">FAIL: test_list_fraction (test.TestSum)</span>
<span class="go">----------------------------------------------------------------------</span>
<span class="go">Traceback (most recent call last):</span>
 <span class="go">File "test.py", line 21, in test_list_fraction</span>
 <span class="go">self.assertEqual(result, 1)</span>
<span class="go">AssertionError: Fraction(9, 10) != 1</span>

<span class="go">----------------------------------------------------------------------</span>
<span class="go">Ran 2 tests in 0.001s</span>

<span class="go">FAILED (failures=1)</span>` </pre>

</div>

In the output, you’ll see the following information:

1.  The first line shows the execution results of all the tests, one failed (`F`) and one passed (`.`).

2.  The `FAIL` entry shows some details about the failed test:

    *   The test method name (`test_list_fraction`)
    *   The test module (`test`) and the test case (`TestSum`)
    *   A traceback to the failing line
    *   The details of the assertion with the expected result (`1`) and the actual result (`Fraction(9, 10)`)

Remember, you can add extra information to the test output by adding the `-v` flag to the `python -m unittest` command.

</section>

<section class="section3" id="running-your-tests-from-pycharm">

### Running Your Tests From PyCharm

If you’re using the PyCharm IDE, you can run `unittest` or `pytest` by following these steps:

1.  In the Project tool window, select the `tests` directory.
2.  On the context menu, choose the run command for `unittest`. For example, choose _Run ‘Unittests in my Tests…’_.

This will execute `unittest` in a test window and give you the results within PyCharm:

[![PyCharm Testing](https://files.realpython.com/media/py_run_test_folder.b0e61b478c81.png)](https://files.realpython.com/media/py_run_test_folder.b0e61b478c81.png)

More information is available on the [PyCharm Website](https://www.jetbrains.com/help/pycharm/performing-tests.html).

</section>

<section class="section3" id="running-your-tests-from-visual-studio-code">

### Running Your Tests From Visual Studio Code

If you’re using the Microsoft Visual Studio Code IDE, support for `unittest`, `nose`, and `pytest` execution is built into the Python plugin.

If you have the Python plugin installed, you can set up the configuration of your tests by opening the Command Palette with <span class="keys"><kbd class="key-control">Ctrl</kbd><span>+</span><kbd class="key-shift">Shift</kbd><span>+</span><kbd class="key-p">P</kbd></span> and typing “Python test”. You will see a range of options:

[![Visual Studio Code Step 1](https://files.realpython.com/media/vscode-test-capture.dfefa1d20789.PNG)](https://files.realpython.com/media/vscode-test-capture.dfefa1d20789.PNG)

Choose _Debug All Unit Tests_, and VSCode will then raise a prompt to configure the test framework. Click on the cog to select the test runner (`unittest`) and the home directory (`.`).

Once this is set up, you will see the status of your tests at the bottom of the window, and you can quickly access the test logs and run the tests again by clicking on these icons:

[![Visual Studio Code Step 2](https://files.realpython.com/media/vscode-test-results.951be75c3d3b.PNG)](https://files.realpython.com/media/vscode-test-results.951be75c3d3b.PNG)

This shows the tests are executing, but some of them are failing.

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

</section>

<section class="section2" id="testing-for-web-frameworks-like-django-and-flask">

## Testing for Web Frameworks Like Django and Flask

If you’re writing tests for a web application using one of the popular frameworks like Django or Flask, there are some important differences in the way you write and run the tests.

<section class="section3" id="why-theyre-different-from-other-applications">

### Why They’re Different From Other Applications

Think of all the code you’re going to be testing in a web application. The routes, views, and models all require lots of imports and knowledge about the frameworks being used.

This is similar to the car test at the beginning of the tutorial: you have to start up the car’s computer before you can run a simple test like checking the lights.

Django and Flask both make this easy for you by providing a test framework based on `unittest`. You can continue writing tests in the way you’ve been learning but execute them slightly differently.

</section>

<section class="section3" id="how-to-use-the-django-test-runner">

### How to Use the Django Test Runner

The Django `startapp` template will have created a `tests.py` file inside your application directory. If you don’t have that already, you can create it with the following contents:

<div class="highlight python">

<pre><span></span>`<span class="kn">from</span> <span class="nn">django.test</span> <span class="kn">import</span> <span class="n">TestCase</span>

<span class="k">class</span> <span class="nc">MyTestCase</span><span class="p">(</span><span class="n">TestCase</span><span class="p">):</span>
    <span class="c1"># Your test methods</span>` </pre>

</div>

The major difference with the examples so far is that you need to inherit from the `django.test.TestCase` instead of `unittest.TestCase`. These classes have the same API, but the Django `TestCase` class sets up all the required state to test.

To execute your test suite, instead of using `unittest` at the command line, you use `manage.py test`:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python manage.py <span class="nb">test</span>` </pre>

</div>

If you want multiple test files, replace `tests.py` with a folder called `tests`, insert an empty file inside called `__init__.py`, and create your `test_*.py` files. Django will discover and execute these.

More information is available at the [Django Documentation Website](https://docs.djangoproject.com/en/2.1/topics/testing/overview/).

</section>

<section class="section3" id="how-to-use-unittest-and-flask">

### How to Use `unittest` and Flask

Flask requires that the app be imported and then set in test mode. You can instantiate a test client and use the test client to make requests to any routes in your application.

All of the test client instantiation is done in the `setUp` method of your test case. In the following example, `my_app` is the name of the application. Don’t worry if you don’t know what `setUp` does. You’ll learn about that in the [More Advanced Testing Scenarios](#more-advanced-testing-scenarios) section.

The code within your test file should look like this:

<div class="highlight python">

<pre><span></span>`<span class="kn">import</span> <span class="nn">my_app</span>
<span class="kn">import</span> <span class="nn">unittest</span>

<span class="k">class</span> <span class="nc">MyTestCase</span><span class="p">(</span><span class="n">unittest</span><span class="o">.</span><span class="n">TestCase</span><span class="p">):</span>

    <span class="k">def</span> <span class="nf">setUp</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="n">my_app</span><span class="o">.</span><span class="n">app</span><span class="o">.</span><span class="n">testing</span> <span class="o">=</span> <span class="kc">True</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">app</span> <span class="o">=</span> <span class="n">my_app</span><span class="o">.</span><span class="n">app</span><span class="o">.</span><span class="n">test_client</span><span class="p">()</span>

    <span class="k">def</span> <span class="nf">test_home</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="n">result</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">app</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="s1">'/'</span><span class="p">)</span>
        <span class="c1"># Make your assertions</span>` </pre>

</div>

You can then execute the test cases using the `python -m unittest discover` command.

More information is available at the [Flask Documentation Website](http://flask.pocoo.org/docs/0.12/testing/).

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

</section>

<section class="section2" id="more-advanced-testing-scenarios">

## More Advanced Testing Scenarios

Before you step into creating tests for your application, remember the three basic steps of every test:

1.  Create your inputs
2.  Execute the code, capturing the output
3.  Compare the output with an expected result

It’s not always as easy as creating a static value for the input like a string or a number. Sometimes, your application will require an instance of a class or a context. What do you do then?

The data that you create as an input is known as a **fixture**. It’s common practice to create fixtures and reuse them.

If you’re running the same test and passing different values each time and expecting the same result, this is known as **parameterization**.

<section class="section3" id="handling-expected-failures">

### Handling Expected Failures

Earlier, when you made a list of scenarios to test `sum()`, a question came up: What happens when you provide it with a bad value, such as a single integer or a string?

In this case, you would expect `sum()` to throw an error. When it does throw an error, that would cause the test to fail.

There’s a special way to handle expected errors. You can use `.assertRaises()` as a context-manager, then inside the `with` block execute the test steps:

<div class="highlight python">

<pre><span></span>`<span class="kn">import</span> <span class="nn">unittest</span>

<span class="kn">from</span> <span class="nn">my_sum</span> <span class="kn">import</span> <span class="nb">sum</span>

<span class="k">class</span> <span class="nc">TestSum</span><span class="p">(</span><span class="n">unittest</span><span class="o">.</span><span class="n">TestCase</span><span class="p">):</span>
    <span class="k">def</span> <span class="nf">test_list_int</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="sd">"""</span>
 <span class="sd">Test that it can sum a list of integers</span>
 <span class="sd">"""</span>
        <span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">]</span>
        <span class="n">result</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">data</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">result</span><span class="p">,</span> <span class="mi">6</span><span class="p">)</span>

    <span class="k">def</span> <span class="nf">test_list_fraction</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="sd">"""</span>
 <span class="sd">Test that it can sum a list of fractions</span>
 <span class="sd">"""</span>
        <span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="n">Fraction</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">),</span> <span class="n">Fraction</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">),</span> <span class="n">Fraction</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span> <span class="mi">5</span><span class="p">)]</span>
        <span class="n">result</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">data</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">result</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>

 <span class="hll"><span class="k">def</span> <span class="nf">test_bad_type</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span></span> <span class="hll"><span class="n">data</span> <span class="o">=</span> <span class="s2">"banana"</span></span> <span class="hll"><span class="k">with</span> <span class="bp">self</span><span class="o">.</span><span class="n">assertRaises</span><span class="p">(</span><span class="ne">TypeError</span><span class="p">):</span></span> <span class="hll"><span class="n">result</span> <span class="o">=</span> <span class="nb">sum</span><span class="p">(</span><span class="n">data</span><span class="p">)</span></span> 
<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s1">'__main__'</span><span class="p">:</span>
    <span class="n">unittest</span><span class="o">.</span><span class="n">main</span><span class="p">()</span>` </pre>

</div>

This test case will now only pass if `sum(data)` raises a `TypeError`. You can replace `TypeError` with any exception type you choose.

</section>

<section class="section3" id="isolating-behaviors-in-your-application">

### Isolating Behaviors in Your Application

Earlier in the tutorial, you learned what a side effect is. Side effects make unit testing harder since, each time a test is run, it might give a different result, or even worse, one test could impact the state of the application and cause another test to fail!

[![Testing Side Effects](https://files.realpython.com/media/YXhT6fA.d277d5317026.gif)](https://files.realpython.com/media/YXhT6fA.d277d5317026.gif)

There are some simple techniques you can use to test parts of your application that have many side effects:

*   Refactoring code to follow the Single Responsibility Principle
*   Mocking out any method or function calls to remove side effects
*   Using integration testing instead of unit testing for this piece of the application

If you’re not familiar with mocking, see [Python CLI Testing](https://realpython.com/python-cli-testing/#mocks) for some great examples.

</section>

<section class="section3" id="writing-integration-tests">

### Writing Integration Tests

So far, you’ve been learning mainly about unit testing. Unit testing is a great way to build predictable and stable code. But at the end of the day, your application needs to work when it starts!

Integration testing is the testing of multiple components of the application to check that they work together. Integration testing might require acting like a consumer or user of the application by:

*   Calling an HTTP REST API
*   Calling a Python API
*   Calling a web service
*   Running a command line

Each of these types of integration tests can be written in the same way as a unit test, following the Input, Execute, and Assert pattern. The most significant difference is that integration tests are checking more components at once and therefore will have more side effects than a unit test. Also, integration tests will require more fixtures to be in place, like a database, a network socket, or a configuration file.

This is why it’s good practice to separate your unit tests and your integration tests. The creation of fixtures required for an integration like a test database and the test cases themselves often take a lot longer to execute than unit tests, so you may only want to run integration tests before you push to production instead of once on every commit.

A simple way to separate unit and integration tests is simply to put them in different folders:

<div class="highlight">

<pre><span></span>`project/
│
├── my_app/
│   └── __init__.py
│
└── tests/
    |
    ├── unit/
    |   ├── __init__.py
    |   └── test_sum.py
    |
    └── integration/
        ├── __init__.py
        └── test_integration.py` </pre>

</div>

There are many ways to execute only a select group of tests. The specify source directory flag, `-s`, can be added to `unittest discover` with the path containing the tests:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> python -m unittest discover -s tests/integration` </pre>

</div>

`unittest` will have given you the results of all the tests within the `tests/integration` directory.

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

<section class="section3" id="testing-data-driven-applications">

### Testing Data-Driven Applications

Many integration tests will require backend data like a database to exist with certain values. For example, you might want to have a test that checks that the application displays correctly with more than 100 customers in the database, or the order page works even if the product names are displayed in Japanese.

These types of integration tests will depend on different test fixtures to make sure they are repeatable and predictable.

A good technique to use is to store the test data in a folder within your integration testing folder called `fixtures` to indicate that it contains test data. Then, within your tests, you can load the data and run the test.

Here’s an example of that structure if the data consisted of JSON files:

<div class="highlight">

<pre><span></span>`project/
│
├── my_app/
│   └── __init__.py
│
└── tests/
    |
    └── unit/
    |   ├── __init__.py
    |   └── test_sum.py
    |
    └── integration/
        |
        ├── fixtures/
        |   ├── test_basic.json
        |   └── test_complex.json
        |
        ├── __init__.py
        └── test_integration.py` </pre>

</div>

Within your test case, you can use the `.setUp()` method to load the test data from a fixture file in a known path and execute many tests against that test data. Remember you can have multiple test cases in a single Python file, and the `unittest` discovery will execute both. You can have one test case for each set of test data:

<div class="highlight python">

<pre><span></span>`<span class="kn">import</span> <span class="nn">unittest</span>

<span class="k">class</span> <span class="nc">TestBasic</span><span class="p">(</span><span class="n">unittest</span><span class="o">.</span><span class="n">TestCase</span><span class="p">):</span>
    <span class="k">def</span> <span class="nf">setUp</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="c1"># Load test data</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">app</span> <span class="o">=</span> <span class="n">App</span><span class="p">(</span><span class="n">database</span><span class="o">=</span><span class="s1">'fixtures/test_basic.json'</span><span class="p">)</span>

    <span class="k">def</span> <span class="nf">test_customer_count</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">app</span><span class="o">.</span><span class="n">customers</span><span class="p">),</span> <span class="mi">100</span><span class="p">)</span>

    <span class="k">def</span> <span class="nf">test_existence_of_customer</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="n">customer</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">app</span><span class="o">.</span><span class="n">get_customer</span><span class="p">(</span><span class="nb">id</span><span class="o">=</span><span class="mi">10</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">customer</span><span class="o">.</span><span class="n">name</span><span class="p">,</span> <span class="s2">"Org XYZ"</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">customer</span><span class="o">.</span><span class="n">address</span><span class="p">,</span> <span class="s2">"10 Red Road, Reading"</span><span class="p">)</span>

<span class="k">class</span> <span class="nc">TestComplexData</span><span class="p">(</span><span class="n">unittest</span><span class="o">.</span><span class="n">TestCase</span><span class="p">):</span>
    <span class="k">def</span> <span class="nf">setUp</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="c1"># load test data</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">app</span> <span class="o">=</span> <span class="n">App</span><span class="p">(</span><span class="n">database</span><span class="o">=</span><span class="s1">'fixtures/test_complex.json'</span><span class="p">)</span>

    <span class="k">def</span> <span class="nf">test_customer_count</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">app</span><span class="o">.</span><span class="n">customers</span><span class="p">),</span> <span class="mi">10000</span><span class="p">)</span>

    <span class="k">def</span> <span class="nf">test_existence_of_customer</span><span class="p">(</span><span class="bp">self</span><span class="p">):</span>
        <span class="n">customer</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">app</span><span class="o">.</span><span class="n">get_customer</span><span class="p">(</span><span class="nb">id</span><span class="o">=</span><span class="mi">9999</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">customer</span><span class="o">.</span><span class="n">name</span><span class="p">,</span> <span class="sa">u</span><span class="s2">"バナナ"</span><span class="p">)</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">assertEqual</span><span class="p">(</span><span class="n">customer</span><span class="o">.</span><span class="n">address</span><span class="p">,</span> <span class="s2">"10 Red Road, Akihabara, Tokyo"</span><span class="p">)</span>

<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s1">'__main__'</span><span class="p">:</span>
    <span class="n">unittest</span><span class="o">.</span><span class="n">main</span><span class="p">()</span>` </pre>

</div>

If your application depends on data from a remote location, like a remote API, you’ll want to ensure your tests are repeatable. Having your tests fail because the API is offline or there is a connectivity issue could slow down development. In these types of situations, it is best practice to store remote fixtures locally so they can be recalled and sent to the application.

The `requests` library has a complimentary package called `responses` that gives you ways to create response fixtures and save them in your test folders. Find out more [on their GitHub Page](https://github.com/getsentry/responses).

</section>

</section>

<section class="section2" id="testing-in-multiple-environments">

## Testing in Multiple Environments

So far, you’ve been testing against a single version of Python using a virtual environment with a specific set of dependencies. You might want to check that your application works on multiple versions of Python, or multiple versions of a package. Tox is an application that automates testing in multiple environments.

<section class="section3" id="installing-tox">

### Installing Tox

Tox is available on PyPI as a package to install via [`pip`](https://realpython.com/what-is-pip/):

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> pip install tox` </pre>

</div>

Now that you have Tox installed, it needs to be configured.

</section>

<section class="section3" id="configuring-tox-for-your-dependencies">

### Configuring Tox for Your Dependencies

Tox is configured via a configuration file in your project directory. The Tox configuration file contains the following:

*   The command to run in order to execute tests
*   Any additional packages required before executing
*   The target Python versions to test against

Instead of having to learn the Tox configuration syntax, you can get a head start by running the quickstart application:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> tox-quickstart` </pre>

</div>

The Tox configuration tool will ask you those questions and create a file similar to the following in `tox.ini`:

<div class="highlight ini">

<pre><span></span>`<span class="k">[tox]</span>
<span class="na">envlist</span> <span class="o">=</span> <span class="s">py27, py36</span>

<span class="k">[testenv]</span>
<span class="na">deps</span> <span class="o">=</span>

<span class="na">commands</span> <span class="o">=</span><span class="s"></span>
 <span class="s">python -m unittest discover</span>` </pre>

</div>

Before you can run Tox, it requires that you have a `setup.py` file in your application folder containing the steps to install your package. If you don’t have one, you can follow [this guide](https://packaging.python.org/tutorials/packaging-projects/#setup-py) on how to create a `setup.py` before you continue.

Alternatively, if your project is not for distribution on PyPI, you can skip this requirement by adding the following line in the `tox.ini` file under the `[tox]` heading:

<div class="highlight ini">

<pre><span></span>`<span class="k">[tox]</span>
<span class="na">envlist</span> <span class="o">=</span> <span class="s">py27, py36</span>
<span class="hll"><span class="na">skipsdist</span><span class="o">=</span><span class="s">True</span></span> `</pre>

</div>

If you don’t create a `setup.py`, and your application has some dependencies from PyPI, you’ll need to specify those on a number of lines under the `[testenv]` section. For example, Django would require the following:

<div class="highlight ini">

<pre><span></span>`<span class="k">[testenv]</span>
<span class="na">deps</span> <span class="o">=</span> <span class="s">django</span>` </pre>

</div>

Once you have completed that stage, you’re ready to run the tests.

You can now execute Tox, and it will create two virtual environments: one for Python 2.7 and one for Python 3.6\. The Tox directory is called `.tox/`. Within the `.tox/` directory, Tox will execute `python -m unittest discover` against each virtual environment.

You can run this process by calling Tox at the command line:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> tox` </pre>

</div>

Tox will output the results of your tests against each environment. The first time it runs, Tox takes a little bit of time to create the virtual environments, but once it has, the second execution will be a lot faster.

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

<section class="section3" id="executing-tox">

### Executing Tox

The output of Tox is quite straightforward. It creates an environment for each version, installs your dependencies, and then runs the test commands.

There are some additional command line options that are great to remember.

Run only a single environment, such as Python 3.6:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> tox -e py36` </pre>

</div>

Recreate the virtual environments, in case your dependencies have changed or [site-packages](https://docs.python.org/3/install/#how-installation-works) is corrupt:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> tox -r` </pre>

</div>

Run Tox with less verbose output:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> tox -q` </pre>

</div>

Running Tox with more verbose output:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> tox -v` </pre>

</div>

More information on Tox can be found at the [Tox Documentation Website](https://tox.readthedocs.io/en/latest/).

</section>

</section>

<section class="section2" id="automating-the-execution-of-your-tests">

## Automating the Execution of Your Tests

So far, you have been executing the tests manually by running a command. There are some tools for executing tests automatically when you make changes and commit them to a source-control repository like Git. Automated testing tools are often known as CI/CD tools, which stands for “Continuous Integration/Continuous Deployment.” They can run your tests, compile and publish any applications, and even deploy them into production.

[Travis CI](https://travis-ci.com/) is one of many available CI (Continuous Integration) services available.

Travis CI works nicely with Python, and now that you’ve created all these tests, you can automate the execution of them in the cloud! Travis CI is free for any open-source projects on GitHub and GitLab and is available for a charge for private projects.

To get started, login to the website and authenticate with your GitHub or GitLab credentials. Then create a file called `.travis.yml` with the following contents:

<div class="highlight yaml">

<pre><span></span>`<span class="nt">language</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">python</span>
<span class="nt">python</span><span class="p">:</span>
  <span class="p p-Indicator">-</span> <span class="s">"2.7"</span>
  <span class="p p-Indicator">-</span> <span class="s">"3.7"</span>
<span class="nt">install</span><span class="p">:</span>
  <span class="p p-Indicator">-</span> <span class="l l-Scalar l-Scalar-Plain">pip install -r requirements.txt</span>
<span class="nt">script</span><span class="p">:</span>
  <span class="p p-Indicator">-</span> <span class="l l-Scalar l-Scalar-Plain">python -m unittest discover</span>` </pre>

</div>

This configuration instructs Travis CI to:

1.  Test against Python 2.7 and 3.7 (You can replace those versions with any you choose.)
2.  Install all the packages you list in `requirements.txt` (You should remove this section if you don’t have any dependencies.)
3.  Run `python -m unittest discover` to run the tests

Once you have committed and pushed this file, Travis CI will run these commands every time you push to your remote Git repository. You can check out the results on their website.

<div class="w-100 text-center js-needs-scaling" style="transform-origin: 0 0;">[Remove ads](/account/join/)</div>

</section>

<section class="section2" id="whats-next">

## What’s Next

Now that you’ve learned how to create tests, execute them, include them in your project, and even execute them automatically, there are a few advanced techniques you might find handy as your test library grows.

<section class="section3" id="introducing-linters-into-your-application">

### Introducing Linters Into Your Application

Tox and Travis CI have configuration for a test command. The test command you have been using throughout this tutorial is `python -m unittest discover`.

You can provide one or many commands in all of these tools, and this option is there to enable you to add more tools that improve the quality of your application.

One such type of application is called a linter. A linter will look at your code and comment on it. It could give you tips about mistakes you’ve made, correct trailing spaces, and even predict bugs you may have introduced.

For more information on linters, read the [Python Code Quality tutorial](https://realpython.com/python-code-quality/).

<section class="section4" id="passive-linting-with-flake8">

#### Passive Linting With `flake8`

A popular linter that comments on the style of your code in relation to the [PEP 8](https://www.youtube.com/watch?v=Hwckt4J96dI) specification is `flake8`.

You can install `flake8` using `pip`:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> pip install flake8` </pre>

</div>

You can then run `flake8` over a single file, a folder, or a pattern:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> flake8 test.py
<span class="go">test.py:6:1: E302 expected 2 blank lines, found 1</span>
<span class="go">test.py:23:1: E305 expected 2 blank lines after class or function definition, found 1</span>
<span class="go">test.py:24:20: W292 no newline at end of file</span>` </pre>

</div>

You will see a list of errors and warnings for your code that `flake8` has found.

`flake8` is configurable on the command line or inside a configuration file in your project. If you wanted to ignore certain rules, like `E305` shown above, you can set them in the configuration. `flake8` will inspect a `.flake8` file in the project folder or a `setup.cfg` file. If you decided to use Tox, you can put the `flake8` configuration section inside `tox.ini`.

This example ignores the `.git` and `__pycache__` directories as well as the `E305` rule. Also, it sets the max line length to 90 instead of 80 characters. You will likely find that the default constraint of 79 characters for line-width is very limiting for tests, as they contain long method names, string literals with test values, and other pieces of data that can be longer. It is common to set the line length for tests to up to 120 characters:

<div class="highlight ini">

<pre><span></span>`<span class="k">[flake8]</span>
<span class="na">ignore</span> <span class="o">=</span> <span class="s">E305</span>
<span class="na">exclude</span> <span class="o">=</span> <span class="s">.git,__pycache__</span>
<span class="na">max-line-length</span> <span class="o">=</span> <span class="s">90</span>` </pre>

</div>

Alternatively, you can provide these options on the command line:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> flake8 --ignore E305 --exclude .git,__pycache__ --max-line-length<span class="o">=</span><span class="m">90</span>` </pre>

</div>

A full list of configuration options is available on the [Documentation Website](http://flake8.pycqa.org/en/latest/user/options.html).

You can now add `flake8` to your CI configuration. For Travis CI, this would look as follows:

<div class="highlight yaml">

<pre><span></span>`<span class="nt">matrix</span><span class="p">:</span>
  <span class="nt">include</span><span class="p">:</span>
    <span class="p p-Indicator">-</span> <span class="nt">python</span><span class="p">:</span> <span class="s">"2.7"</span>
      <span class="nt">script</span><span class="p">:</span> <span class="s">"flake8"</span>` </pre>

</div>

Travis will read the configuration in `.flake8` and fail the build if any linting errors occur. Be sure to add the `flake8` dependency to your `requirements.txt` file.

</section>

<section class="section4" id="aggressive-linting-with-a-code-formatter">

#### Aggressive Linting With a Code Formatter

`flake8` is a passive linter: it recommends changes, but you have to go and change the code. A more aggressive approach is a code formatter. Code formatters will change your code automatically to meet a collection of style and layout practices.

`black` is a very unforgiving formatter. It doesn’t have any configuration options, and it has a very specific style. This makes it great as a drop-in tool to put in your test pipeline.

<div class="alert alert-primary" role="alert">

**Note:** `black` requires Python 3.6+.

</div>

You can install `black` via pip:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> pip install black` </pre>

</div>

Then to run `black` at the command line, provide the file or directory you want to format:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> black test.py` </pre>

</div>

</section>

</section>

<section class="section3" id="keeping-your-test-code-clean">

### Keeping Your Test Code Clean

When writing tests, you may find that you end up copying and pasting code a lot more than you would in regular applications. Tests can be very repetitive at times, but that is by no means a reason to leave your code sloppy and hard to maintain.

Over time, you will develop a lot of [technical debt](https://martinfowler.com/bliki/TechnicalDebt.html) in your test code, and if you have significant changes to your application that require changes to your tests, it can be a more cumbersome task than necessary because of the way you structured them.

Try to follow the **DRY** principle when writing tests: **D**on’t **R**epeat **Y**ourself.

Test fixtures and functions are a great way to produce test code that is easier to maintain. Also, readability counts. Consider deploying a linting tool like `flake8` over your test code:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> flake8 --max-line-length<span class="o">=</span><span class="m">120</span> tests/` </pre>

</div>

</section>

<section class="section3" id="testing-for-performance-degradation-between-changes">

### Testing for Performance Degradation Between Changes

There are many ways to benchmark code in Python. The standard library provides the `timeit` module, which can time functions a number of times and give you the distribution. This example will execute `test()` 100 times and `print()` the output:

<div class="highlight python">

<pre><span></span>`<span class="k">def</span> <span class="nf">test</span><span class="p">():</span>
    <span class="c1"># ... your code</span>

<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s1">'__main__'</span><span class="p">:</span>
    <span class="kn">import</span> <span class="nn">timeit</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">timeit</span><span class="o">.</span><span class="n">timeit</span><span class="p">(</span><span class="s2">"test()"</span><span class="p">,</span> <span class="n">setup</span><span class="o">=</span><span class="s2">"from __main__ import test"</span><span class="p">,</span> <span class="n">number</span><span class="o">=</span><span class="mi">100</span><span class="p">))</span>` </pre>

</div>

Another option, if you decided to use `pytest` as a test runner, is the `pytest-benchmark` plugin. This provides a `pytest` fixture called `benchmark`. You can pass `benchmark()` any callable, and it will log the timing of the callable to the results of `pytest`.

You can install `pytest-benchmark` from PyPI using `pip`:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> pip install pytest-benchmark` </pre>

</div>

Then, you can add a test that uses the fixture and passes the callable to be executed:

<div class="highlight python">

<pre><span></span>`<span class="k">def</span> <span class="nf">test_my_function</span><span class="p">(</span><span class="n">benchmark</span><span class="p">):</span>
    <span class="n">result</span> <span class="o">=</span> <span class="n">benchmark</span><span class="p">(</span><span class="n">test</span><span class="p">)</span>` </pre>

</div>

Execution of `pytest` will now give you benchmark results:

[![Pytest benchmark screenshot](https://files.realpython.com/media/pytest-bench-screen.6d83bffe8e21.png)](https://files.realpython.com/media/pytest-bench-screen.6d83bffe8e21.png)

More information is available at the [Documentation Website](https://pytest-benchmark.readthedocs.io/en/latest/).

</section>

<section class="section3" id="testing-for-security-flaws-in-your-application">

### Testing for Security Flaws in Your Application

Another test you will want to run on your application is checking for common security mistakes or vulnerabilities.

You can install `bandit` from PyPI using `pip`:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> pip install bandit` </pre>

</div>

You can then pass the name of your application module with the `-r` flag, and it will give you a summary:

<div class="highlight sh">

<pre><span></span>`<span class="gp">$</span> bandit -r my_sum
<span class="go">[main]  INFO    profile include tests: None</span>
<span class="go">[main]  INFO    profile exclude tests: None</span>
<span class="go">[main]  INFO    cli include tests: None</span>
<span class="go">[main]  INFO    cli exclude tests: None</span>
<span class="go">[main]  INFO    running on Python 3.5.2</span>
<span class="go">Run started:2018-10-08 00:35:02.669550</span>

<span class="go">Test results:</span>
 <span class="go">No issues identified.</span>

<span class="go">Code scanned:</span>
 <span class="go">Total lines of code: 5</span>
 <span class="go">Total lines skipped (#nosec): 0</span>

<span class="go">Run metrics:</span>
 <span class="go">Total issues (by severity):</span>
 <span class="go">Undefined: 0.0</span>
 <span class="go">Low: 0.0</span>
 <span class="go">Medium: 0.0</span>
 <span class="go">High: 0.0</span>
 <span class="go">Total issues (by confidence):</span>
 <span class="go">Undefined: 0.0</span>
 <span class="go">Low: 0.0</span>
 <span class="go">Medium: 0.0</span>
 <span class="go">High: 0.0</span>
<span class="go">Files skipped (0):</span>` </pre>

</div>

As with `flake8`, the rules that `bandit` flags are configurable, and if there are any you wish to ignore, you can add the following section to your `setup.cfg` file with the options:

<div class="highlight ini">

<pre><span></span>`<span class="k">[bandit]</span>
<span class="na">exclude: /test</span>
<span class="na">tests: B101,B102,B301</span>` </pre>

</div>

More details are available at the [GitHub Website](https://github.com/PyCQA/bandit).

</section>

</section>

<section class="section2" id="conclusion">

## Conclusion

Python has made testing accessible by building in the commands and libraries you need to validate that your applications work as designed. Getting started with testing in Python needn’t be complicated: you can use `unittest` and write small, maintainable methods to validate your code.

As you learn more about testing and your application grows, you can consider switching to one of the other test frameworks, like `pytest`, and start to leverage more advanced features.

Thank you for reading. I hope you have a bug-free future with Python!

</section>

<div class="border rounded p-3 card mb-2">

<span class="badge badge-pill badge-success">Watch Now</span> This tutorial has a related video course created by the Real Python team. Watch it together with the written tutorial to deepen your understanding: [**Test-Driven Development With PyTest**](/courses/test-driven-development-pytest/)

</div>

</div>

<div class="card mt-4 mb-4 bg-secondary">

🐍 Python Tricks 💌

<div class="card-body">

<div class="container">

<div class="row">

<div class="col-xs-12 col-sm-7">

Get a short & sweet **Python Trick** delivered to your inbox every couple of days. No spam ever. Unsubscribe any time. Curated by the Real Python team.

</div>

<div class="col-xs-12 col-sm-5">![Python Tricks Dictionary Merge](/static/pytrick-dict-merge.4201a0125a5e.png)</div>

</div>

<div class="row mb-3">

<form class="col-12" action="/optins/process/" method="post"><input type="hidden" name="csrfmiddlewaretoken" value="n1aC8gVbJ98ATazaXgt2lPpmoz0Z5SgunqPBbQGMLocScYvGlXnQFHwuULFuPUyN"> <input type="hidden" name="slug" value="static-python-tricks-footer">

<div class="form-group"><input name="email" type="email" class="form-control form-control-lg" placeholder="Email Address" required=""></div>

<button name="submit" type="submit" class="btn btn-primary btn-lg btn-block">Send Me Python Tricks »</button></form>

</div>

</div>

</div>

</div>

<div class="card mt-3" id="author">

About **Anthony Shaw**

<div class="card-body">

<div class="container p-0">

<div class="row">

<div class="col-12 col-md-3 align-self-center">[![Anthony Shaw](https://files.realpython.com/media/10995490_10152772557676353_1442757472697890998_n.e88e3d7b17c7.jpg)](/team/ashaw/) [![Anthony Shaw](https://files.realpython.com/media/10995490_10152772557676353_1442757472697890998_n.e88e3d7b17c7.jpg)](/team/ashaw/)</div>

<div class="col mt-3">

Anthony is an avid Pythonista and writes for Real Python. Anthony is a Fellow of the Python Software Foundation and member of the Open-Source Apache Foundation.

[» More about Anthony](/team/ashaw/)</div>

</div>

</div>

</div>

* * *

<div class="card-body pb-0">

<div class="container">

<div class="row">

_Each tutorial at Real Python is created by a team of developers so that it meets our high quality standards. The team members who worked on this tutorial are:_

</div>

<div class="row align-items-center w-100 mx-auto">

<div class="col-4 col-sm-2 align-self-center">[![Aldren Santos](https://files.realpython.com/media/asantos-avatar.888c78fffab3.jpg)](/team/asantos/)</div>

<div class="col pl-0 d-none d-sm-block">[

Aldren

](/team/asantos/)</div>

<div class="col-4 col-sm-2 align-self-center">[![David Amos](https://files.realpython.com/media/me-small.f5f49f1c48e1.jpg)](/team/damos/)</div>

<div class="col pl-0 d-none d-sm-block">[

David

](/team/damos/)</div>

<div class="col-4 col-sm-2 align-self-center">[![Geir Arne Hjelle](https://files.realpython.com/media/gahjelle.470149ee709e.jpg)](/team/gahjelle/)</div>

<div class="col pl-0 d-none d-sm-block">[

Geir Arne

](/team/gahjelle/)</div>

</div>

<div class="row align-items-center w-100 mx-auto">

<div class="col-4 col-sm-2 align-self-center">[![Joanna Jablonski](https://files.realpython.com/media/jjablonksi-avatar.e37c4f83308e.jpg)](/team/jjablonski/)</div>

<div class="col pl-0 d-none d-sm-block">[

Joanna

](/team/jjablonski/)</div>

</div>

</div>

</div>

</div>

<div class="bg-light rounded py-4 my-4 shadow shadow-sm mx-n2">

<div class="col-12 text-center d-block d-md-none">

Master <u><span class="marker-highlight">Real-World Python Skills</span></u> With Unlimited Access to Real Python

![](/static/videos/lesson-locked.f5105cfd26db.svg)

**Join us and get access to hundreds of tutorials, hands-on video courses, and a community of expert Pythonistas:**

[Level Up Your Python Skills »](/account/join/?utm_source=rp_article_footer&utm_content=python-testing)

</div>

<div class="col-12 text-center d-none d-md-block">

Master <u><span class="marker-highlight">Real-World Python Skills</span></u>  
With Unlimited Access to Real Python

![](/static/videos/lesson-locked.f5105cfd26db.svg)

**Join us and get access to hundreds of tutorials, hands-on video courses, and a community of expert Pythonistas:**

[Level Up Your Python Skills »](/account/join/?utm_source=rp_article_footer&utm_content=python-testing)

</div>

</div>

<div class="card mt-4" id="reader-comments">

What Do You Think?

<div class="text-center mt-3 mb-0 p-0"><span>[Tweet](https://twitter.com/intent/tweet/?text=Check out this %23Python tutorial: Getting%20Started%20With%20Testing%20in%20Python by @realpython&url=https%3A//realpython.com/python-testing/) [Share](https://facebook.com/sharer/sharer.php?u=https%3A//realpython.com/python-testing/) [Email](mailto:?subject=Python article for you&body=Check out this Python tutorial:%0A%0AGetting%20Started%20With%20Testing%20in%20Python%0A%0Ahttps%3A//realpython.com/python-testing/)</span></div>

<div class="card-body">

<div class="alert alert-dark">

**Real Python Comment Policy:** The most useful comments are those written with the goal of learning from or helping out other readers—after reading the whole article and all the earlier comments. Complaints and insults generally won’t make the cut here.

</div>

What’s your #1 takeaway or favorite thing you learned? How are you going to put your newfound skills to use? Leave a comment below and let us know.

</div>

</div>

<div class="card mt-4 mb-4">

Keep Learning

<div class="card-body">

Related Tutorial Categories: [best-practices](/tutorials/best-practices/) [intermediate](/tutorials/intermediate/) [testing](/tutorials/testing/)

Recommended Video Course: [Test-Driven Development With PyTest](/courses/test-driven-development-pytest/)

</div>

</div>

<div class="modal fade" tabindex="-1" role="dialog" id="rpvc">

<div class="modal-dialog modal-lg modal-dialog-centered" role="document">

<div class="modal-content">

<div class="modal-header border-0 mt-3">

<div class="col-12 modal-title text-center">

## Master <u>Real-World Python Skills</u> With Unlimited Access to Real Python

Already a member? [Sign-In](/account/login/)

</div>

</div>

<div class="modal-body bg-light">

<div class="col-12 text-center">

[![](/static/videos/lesson-locked.f5105cfd26db.svg)](/account/join/?utm_source=rp&utm_medium=web&utm_campaign=pwn&utm_content=v1)

**Join us and get access to hundreds of tutorials, hands-on video courses, and a community of expert Pythonistas:**

[See Membership Options »](/account/join/?utm_source=rp&utm_medium=web&utm_campaign=pwn&utm_content=v1)

</div>

</div>

<div class="modal-footer border-0">[Close](#!)</div>

</div>

</div>

</div>

</div>

<aside class="col-md-7 col-lg-4">

<div class="card mb-3 bg-secondary">

<form class="card-body" action="/optins/process/" method="post">

<div class="form-group">

— FREE Email Series —

🐍 Python Tricks 💌

![Python Tricks Dictionary Merge](/static/pytrick-dict-merge.4201a0125a5e.png)

</div>

<div class="form-group"><input type="hidden" name="csrfmiddlewaretoken" value="n1aC8gVbJ98ATazaXgt2lPpmoz0Z5SgunqPBbQGMLocScYvGlXnQFHwuULFuPUyN"> <input type="hidden" name="slug" value="static-python-tricks-sidebar"> <input type="email" class="form-control form-control-md" name="email" placeholder="Email…" required=""></div>

<button type="submit" name="submit" class="btn btn-primary btn-md btn-block">Get Python Tricks »</button>

🔒 No spam. Unsubscribe any time.

</form>

</div>

<div class="sidebar-module sidebar-module-inset border">

[All Tutorial Topics](/tutorials/all/)

[advanced](/tutorials/advanced/) [api](/tutorials/api/) [basics](/tutorials/basics/) [best-practices](/tutorials/best-practices/) [community](/tutorials/community/) [databases](/tutorials/databases/) [data-science](/tutorials/data-science/) [devops](/tutorials/devops/) [django](/tutorials/django/) [docker](/tutorials/docker/) [flask](/tutorials/flask/) [front-end](/tutorials/front-end/) [intermediate](/tutorials/intermediate/) [machine-learning](/tutorials/machine-learning/) [projects](/tutorials/projects/) [python](/tutorials/python/) [testing](/tutorials/testing/) [tools](/tutorials/tools/) [web-dev](/tutorials/web-dev/) [web-scraping](/tutorials/web-scraping/)</div>

<div class="sidebar-sticky sidebar-nav-message">

<div class="bg-light sidebar-module sidebar-module-inset" style="max-height: 80vh; overflow-y: scroll;" id="sidebar-toc">

[Table of Contents](#toc)

<div class="toc">

*   [Testing Your Code](#testing-your-code)
    *   [Automated vs. Manual Testing](#automated-vs-manual-testing)
    *   [Unit Tests vs. Integration Tests](#unit-tests-vs-integration-tests)
    *   [Choosing a Test Runner](#choosing-a-test-runner)
*   [Writing Your First Test](#writing-your-first-test)
    *   [Where to Write the Test](#where-to-write-the-test)
    *   [How to Structure a Simple Test](#how-to-structure-a-simple-test)
    *   [How to Write Assertions](#how-to-write-assertions)
    *   [Side Effects](#side-effects)
*   [Executing Your First Test](#executing-your-first-test)
    *   [Executing Test Runners](#executing-test-runners)
    *   [Understanding Test Output](#understanding-test-output)
    *   [Running Your Tests From PyCharm](#running-your-tests-from-pycharm)
    *   [Running Your Tests From Visual Studio Code](#running-your-tests-from-visual-studio-code)
*   [Testing for Web Frameworks Like Django and Flask](#testing-for-web-frameworks-like-django-and-flask)
    *   [Why They’re Different From Other Applications](#why-theyre-different-from-other-applications)
    *   [How to Use the Django Test Runner](#how-to-use-the-django-test-runner)
    *   [How to Use unittest and Flask](#how-to-use-unittest-and-flask)
*   [More Advanced Testing Scenarios](#more-advanced-testing-scenarios)
    *   [Handling Expected Failures](#handling-expected-failures)
    *   [Isolating Behaviors in Your Application](#isolating-behaviors-in-your-application)
    *   [Writing Integration Tests](#writing-integration-tests)
    *   [Testing Data-Driven Applications](#testing-data-driven-applications)
*   [Testing in Multiple Environments](#testing-in-multiple-environments)
    *   [Installing Tox](#installing-tox)
    *   [Configuring Tox for Your Dependencies](#configuring-tox-for-your-dependencies)
    *   [Executing Tox](#executing-tox)
*   [Automating the Execution of Your Tests](#automating-the-execution-of-your-tests)
*   [What’s Next](#whats-next)
    *   [Introducing Linters Into Your Application](#introducing-linters-into-your-application)
    *   [Keeping Your Test Code Clean](#keeping-your-test-code-clean)
    *   [Testing for Performance Degradation Between Changes](#testing-for-performance-degradation-between-changes)
    *   [Testing for Security Flaws in Your Application](#testing-for-security-flaws-in-your-application)
*   [Conclusion](#conclusion)

</div>

</div>

<div class="sidebar-module sidebar-module-inset text-center my-3 py-0"><span>[Tweet](https://twitter.com/intent/tweet/?text=Check out this %23Python tutorial: Getting%20Started%20With%20Testing%20in%20Python by @realpython&url=https%3A//realpython.com/python-testing/) [Share](https://facebook.com/sharer/sharer.php?u=https%3A//realpython.com/python-testing/) [Email](mailto:?subject=Python article for you&body=Check out this Python tutorial:%0A%0AGetting%20Started%20With%20Testing%20in%20Python%0A%0Ahttps%3A//realpython.com/python-testing/)</span></div>

<div class="sidebar-module sidebar-module-inset border card">

<span class="badge badge-pill badge-success">Recommended Video Course</span>  
[Test-Driven Development With PyTest](/courses/test-driven-development-pytest/)

</div>

</div>

</aside>

</div>

</div>

<div class="modal fade" id="modal-python-mastery-course" tabindex="-1" role="dialog" aria-hidden="true">

<div class="modal-dialog modal-dialog-centered modal-lg" role="document">

<div class="modal-content">

<div class="modal-header bg-light pt-3 pb-2">

<div class="container-fluid">

<div class="row">

<div class="col-12">

Almost there! Complete this form and click the button below to gain instant access:

</div>

</div>

</div>

<button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">×</span></button></div>

<div class="modal-body m-4">

<div class="container-fluid">

<div class="row align-items-center">

<div class="col-12 col-lg-4">![](https://files.realpython.com/media/python-logo.8eb72ea6927b.png)</div>

<div class="col">

5 Thoughts On Python Mastery

<form class="col-12" action="/optins/process/" method="post"><input type="hidden" name="csrfmiddlewaretoken" value="n1aC8gVbJ98ATazaXgt2lPpmoz0Z5SgunqPBbQGMLocScYvGlXnQFHwuULFuPUyN"> <input type="hidden" name="slug" value="python-mastery-course">

<div class="form-group"><input type="email" name="email" class="form-control" placeholder="Email Address" required="" autofocus=""></div>

<button name="submit" type="submit" class="btn btn-primary btn-block text-wrap">Start the Class »</button></form>

</div>

</div>

</div>

</div>

</div>

</div>

</div>

<footer class="footer">

<div class="container">

© 2012–2020 Real Python ⋅ [Newsletter](/newsletter/) ⋅ [Podcast](/podcasts/rpp/) ⋅ [YouTube](https://www.youtube.com/realpython) ⋅ [Twitter](https://twitter.com/realpython) ⋅ [Facebook](https://facebook.com/LearnRealPython) ⋅ [Instagram](https://www.instagram.com/realpython/) ⋅ [Python Tutorials](/) ⋅ [Search](/search) ⋅ [Privacy Policy](/privacy-policy/) ⋅ [Energy Policy](/energy-policy/) ⋅ [Advertise](/sponsorships/) ⋅ [Contact](/contact/)  
❤️ Happy Pythoning!

</div>

</footer>

<script>(function(document, history, location) { var HISTORY_SUPPORT = !!(history && history.pushState); var anchorScrolls = { ANCHOR_REGEX: /^#[^ ]+$/, OFFSET_HEIGHT_PX: 120, /** * Establish events, and fix initial scroll position if a hash is provided. */ init: function() { this.scrollToCurrent(); window.addEventListener('hashchange', this.scrollToCurrent.bind(this)); document.body.addEventListener('click', this.delegateAnchors.bind(this)); }, /** * Return the offset amount to deduct from the normal scroll position. * Modify as appropriate to allow for dynamic calculations */ getFixedOffset: function() { return this.OFFSET_HEIGHT_PX; }, /** * If the provided href is an anchor which resolves to an element on the * page, scroll to it. * @param {String} href * @return {Boolean} - Was the href an anchor. */ scrollIfAnchor: function(href, pushToHistory) { var match, rect, anchorOffset; if(!this.ANCHOR_REGEX.test(href)) { return false; } match = document.getElementById(href.slice(1)); if(match) { rect = match.getBoundingClientRect(); anchorOffset = window.pageYOffset + rect.top - this.getFixedOffset(); window.scrollTo(window.pageXOffset, anchorOffset); // Add the state to history as-per normal anchor links if(HISTORY_SUPPORT && pushToHistory) { history.pushState({}, document.title, location.pathname + href); } } return !!match; }, /** * Attempt to scroll to the current location's hash. */ scrollToCurrent: function() { this.scrollIfAnchor(window.location.hash); }, /** * If the click event's target was an anchor, fix the scroll position. */ delegateAnchors: function(e) { var elem = e.target; if( elem.nodeName === 'A' && this.scrollIfAnchor(elem.getAttribute('href'), true) ) { e.preventDefault(); } } }; window.addEventListener( 'DOMContentLoaded', anchorScrolls.init.bind(anchorScrolls) ); })(window.document, window.history, window.location);</script> <script>window.rp_prop_id = '58946116052';</script> <script>(function() { function throttle(a, b) { var c, d; return function () { var e = this, f = arguments, g = +new Date; c && g < c + a ? (clearTimeout(d), d = setTimeout(function () { c = g, b.apply(e, f) }, a)) : (c = g, b.apply(e, f)) } } var elems = document.getElementsByClassName("js-needs-scaling"); var resizeAll = function() { Array.prototype.forEach.call(elems, function(elem) { var frames = elem.getElementsByTagName("iframe") if (frames.length === 0) { return; } var disclosure = elem.getElementsByClassName("js-disclosure"); if (disclosure.length > 0) { disclosure[0].style.display = ""; } else { disclosure[0].style.display = "none"; } if (frames[0].clientWidth <= elem.parentElement.clientWidth) { elem.style.transform = ""; elem.classList.add("text-center"); return; } elem.classList.remove("text-center"); elem.style.transform = "scale(" + elem.clientWidth / frames[0].width + ")"; }); } var periodicResize = function() { resizeAll(); setTimeout(periodicResize, 100); } setTimeout(periodicResize, 100); })();</script> <script>var disqus_config = function () { this.page.url = 'https://realpython.com/python-testing/'; this.page.identifier = 'https://realpython.com/python-testing/'; this.callbacks.onReady = [function() { if (window.onDisqusReady) { window.onDisqusReady(); } }]; }; var disqus_script_url = 'https://realpython.disqus.com/embed.js';</script> <script>var OneSignal = window.OneSignal || []; OneSignal.push(function() { OneSignal.init({ appId: "c0081e20-a523-42bb-b0ac-04c5a9e8bf40" }); });</script> <script type="application/ld+json">{ "@context": "http://schema.org", "@type": "Article", "headline": "Getting Started With Testing in Python", "image": { "@type": "ImageObject", "url": "https://files.realpython.com/media/Getting-Started-with-Testing-in-Python_Watermarked.9f22be97343d.jpg", "width": 1920, "height": 1080 }, "mainEntityOfPage": { "@type": "WebPage", "@id": "https://realpython.com/python-testing/" }, "datePublished": "2018-10-22T14:00:00+00:00", "dateModified": "2020-07-10T23:19:07.338271+00:00", "publisher": { "@type": "Organization", "name": "Real Python", "logo": { "@type": "ImageObject", "url": "https://realpython.com/static/real-python-logo-square-tiny.b2452b6d3823.png", "width": 60, "height": 60 } }, "author": { "@type": "Organization", "name": "Real Python", "url": "https://realpython.com", "logo": "https://realpython.com/static/real-python-logo-square.146e987bf77c.png" }, "description": "In this in-depth tutorial, you’ll see how to create Python unit tests, execute them, and find the bugs before your users do. You’ll learn about the tools available to write and execute tests, check your application’s performance, and even look for security issues." }</script> <script>var _dcq = _dcq || []; var _dcs = _dcs || {}; _dcs.account = '6214500'; (function() { var dc = document.createElement('script'); dc.type = 'text/javascript'; dc.async = true; dc.src = '//tag.getdrip.com/6214500.js'; var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(dc, s); })();</script> <script>!function(f,b,e,v,n,t,s) {if(f.fbq)return;n=f.fbq=function(){n.callMethod? n.callMethod.apply(n,arguments):n.queue.push(arguments)}; if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0'; n.queue=[];t=b.createElement(e);t.async=!0; t.src=v;s=b.getElementsByTagName(e)[0]; s.parentNode.insertBefore(t,s)}(window, document,'script', 'https://connect.facebook.net/en_US/fbevents.js'); fbq('init', '2220911568135371'); fbq('track', 'PageView');</script>

<noscript>![](https://www.facebook.com/tr?id=2220911568135371&ev=PageView&noscript=1)</noscript>
