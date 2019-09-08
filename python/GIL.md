
[Source](https://wiki.python.org/moin/GlobalInterpreterLock "Permalink to GlobalInterpreterLock - Python Wiki")

# GlobalInterpreterLock - Python Wiki

In CPython, the **global interpreter lock**, or **GIL**, is a mutex that protects access to Python objects, preventing multiple threads from executing Python bytecodes at once. This lock is necessary mainly because CPython's memory management is not thread-safe. (However, since the GIL exists, other features have grown to depend on the guarantees that it enforces.) 

CPython extensions must be GIL-aware in order to avoid defeating threads. For an explanation, see [Global interpreter lock][1]. 

The GIL is controversial because it prevents multithreaded CPython programs from taking full advantage of multiprocessor systems in certain situations. Note that potentially blocking or long-running operations, such as I/O, image processing, and [NumPy][2] number crunching, happen _outside_ the GIL. Therefore it is only in multithreaded programs that spend a lot of time inside the GIL, interpreting CPython bytecode, that the GIL becomes a bottleneck. 

However [the GIL can degrade performance][3] even when it is not a bottleneck. Summarizing those slides: The system call overhead is significant, especially on multicore hardware. Two threads calling a function may take twice as much time as a single thread calling the function twice. The GIL can cause I/O-bound threads to be scheduled ahead of CPU-bound threads. And it prevents signals from being delivered. 

## Non-CPython implementations

* [Jython][4] and [IronPython][5] have no GIL and can fully exploit multiprocessor systems 
* [PyPy][6] currently has a GIL like CPython 
* in Cython the GIL exists, but can be released temporarily using a "with" statement 

[Mention place of GIL in [StacklessPython][7].] 

## Eliminating the GIL

Getting rid of the GIL is an occasional topic on the python-dev mailing list. No one has managed it yet. The following properties are all highly desirable for any potential GIL replacement; some are hard requirements. 

* **Simplicity.** The proposal must be implementable and maintainable in the long run. 
* **Concurrency.** The point of eliminating the GIL would be to improve the performance of multithreaded programs. So any proposal must show that it actually does so in practice. 
* **Speed.** The [BDFL][8] has said he will reject any proposal in this direction that slows down single-threaded programs. (citation needed) Note that this is harder than it looks. The existing reference count mechanism is very fast in the non-concurrent case, but means that almost any reference to an object is a modification (at least to the refcount); many concurrent GC algorithms assume that modifications are rare. 
* **Features.** The proposal must support existing CPython features including `__del__` and weak references. 
* **API compatibility.** The proposal should be source-compatible with the macros used by all existing CPython extensions (`Py_INCREF` and friends). See [Python/C API Reference Manual: Reference Counting][9]. 
* **Prompt destruction** (nice to have?). The existing reference-counting scheme destroys objects as soon as they become unreachable, except for objects in reference cycles. Those are collected later by Python's cycle collector. Some CPython programs depend on this, e.g. to close `file`s promptly, so it would be nice to keep this feature. 
* **Ordered destruction** (nice to have?). Barring cycles, Python currently always destroys an unreachable object _X_ before destroying any other objects referenced by _X_. This means all the object's attributes are still there when `__del__` runs. (Many garbage collection schemes don't guarantee this.) 

    * I'd say this is necessary for Python. There's very little you can usefully do with a half-destroyed object. That which you can do, you could also do without being exposed to half-destroyed objects. --Rhamphoryncus 

### API compatibility in detail

API compatibility is an especially difficult aspect of the problem. All concurrent memory management schemes we've found rely on one or more of the following techniques, all of which are incompatible with the existing Python/C API. 

* **Tracing.** Most garbage collectors need to be able to start with an object and enumerate all the objects that it points to. The builtin CPython pointer-containing types, like `PyList` and `PyDict`, all have a `tp_traverse` method that can do this, but not all extension types have that method. 
* **Write barriers.** A write barrier is a small piece of code that executes whenever a pointer variable is modified. Alas, no matter how you hack the `Py_INCREF` etc. macros, you can't make a write barrier hook out of them. Even if you could, many schemes require a different write barrier for stack variables vs. global variables vs. object fields that point to other objects; nothing in the Python/C API makes that distinction. 
* **Exact stack information.** Exact garbage collection schemes need to be able to mark all objects reachable from local C variables. To do this, some schemes need to know where such variables are located on the C stack (and/or registers)--something the Python/C API does not require extensions to track. 

It is barely credible that CPython might someday make `tp_traverse` mandatory for pointer-carrying types; adding support for write barriers or stack bookkeeping to the Python/C API seems extremely unlikely. 

Another issue in this area is that existing C extensions depend on the GIL guarantees. They assume that when extension code is called, all other threads are locked out. If an extension does need to deal with a threaded environment, it explicitly opts in (by releasing the GIL). Therefore any would-be GIL replacement must provide GIL-like guarantees by default. Threading must remain opt-in for extensions. 

## Recent discussions

[1]: https://docs.python.org/3/c-api/init.html#thread-state-and-the-global-interpreter-lock
[2]: https://wiki.python.org/moin/NumPy
[3]: http://www.dabeaz.com/python/GIL.pdf
[4]: https://wiki.python.org/moin/Jython
[5]: https://wiki.python.org/moin/IronPython
[6]: https://wiki.python.org/moin/PyPy
[7]: https://wiki.python.org/moin/StacklessPython
[8]: https://wiki.python.org/moin/BDFL
[9]: http://docs.python.org/api/countingRefs.html

  
