<div class="allwrapper">

<div class="nav">

<div class="branding">

<div class="logo">![](/assets/logo.png)</div>

<div class="name">[Mastering JS](/)</div>

<div class="links">[Tutorials](/all) [Newsletter](https://www.getrevue.co/profile/masteringjs)</div>

<script type="text/javascript">var xhr = new XMLHttpRequest(); xhr.open('POST', 'https://g0a3nbw0xa.execute-api.us-east-1.amazonaws.com/prod/track', true); xhr.setRequestHeader('Content-Type', 'application/json'); xhr.onreadystatechange = function() {}; xhr.send(JSON.stringify({ path: window.location.pathname, hostname: window.location.hostname }));</script></div>

</div>

<div class="content">

# What is a Plain Old JavaScript Object (POJO)?

<div class="date">Oct 8, 2019</div>

There's a lot of debate as to what a POJO is in JavaScript: [StackOverflow thinks it is any class that contains user data](https://stackoverflow.com/questions/49630228/create-a-model-pojo-in-javascript), but the [top npm module on Google](https://github.com/bttmly/is-pojo) defines a POJO as any object whose [prototype](/tutorials/fundamentals/prototype) is `Object.prototype`.

The intuition behind POJOs is that a POJO is an object that only contains data, as opposed to methods or internal state. Most JavaScript codebases consider objects created using curly braces `{}` to be POJOs. However, more strict codebases sometimes create POJOs [by calling `Object.create(null)`](https://davidwalsh.name/object-create-null) to avoid [inheriting from the built-in `Object` class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype).

    // If you create an object `obj` with `{}`, `obj` is an instance of
    // the `Object` class, and so it has some built-in properties.
    let obj = {};
    obj.hasOwnProperty; // [Function]
    obj.constructor === Object; // true

    // On the other hand, `Object.create(null)` creates an object that
    // doesn't inherit from **any** class.
    obj = Object.create(null);
    typeof obj; // 'object'
    obj.hasOwnProperty; // undefined
    obj.constructor; // undefined

    obj.prop = 42;
    obj.prop; // 42

## POJOs vs Maps

[JavaScript Maps](http://thecodebarbarian.com/the-80-20-guide-to-maps-in-javascript.html) are an alternative to POJOs for storing data because they do not have any inherited keys from the `Object` class. However, objects are generally easier to work with than maps, because not all JavaScript functions, frameworks, and libraries support maps. For example, [the `JSON.stringify()` function](http://thecodebarbarian.com/the-80-20-guide-to-json-stringify-in-javascript) doesn't serialize maps by default.

    const map = new Map([['answer', 42]]);
    JSON.stringify(map); // '{}'

## Checking if an Object is a POJO

Checking if an object is a POJO can be somewhat tricky and depends on whether you consider objects created using `Object.create(null)` to be POJOs. The safest way is using the [`Object.getPrototypeOf()` function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf) and comparing the object's prototype.

    function isPOJO(arg) {
      if (arg == null || typeof arg !== 'object') {
        return false;
      }
      const proto = Object.getPrototypeOf(arg);
      if (proto == null) {
        return true; // `Object.create(null)`
      }
      return proto === Object.prototype;
    }

    isPOJO({}); // true
    isPOJO(Object.create(null)); // true
    isPOJO(null); // false
    isPOJO(new Number(42)); // false

For example, below is [Mongoose's internal `isPOJO()` function](https://github.com/Automattic/mongoose/blob/43b63ae8d18e49db3ddb56b4c843637339495a76/lib/utils.js#L505-L514)

    exports.isPOJO = function isPOJO(arg) {
      if (arg == null || typeof arg !== 'object') {
        return false;
      }
      const proto = Object.getPrototypeOf(arg);
      // Prototype may be null if you used `Object.create(null)`
      // Checking `proto`'s constructor is safe because `getPrototypeOf()`
      // explicitly crosses the boundary from object data to object metadata
      return !proto || proto.constructor.name === 'Object';
    };

Mongoose checks for the `constructor.name` property instead of checking if `proto.constructor === Object` to support objects generated using [Node.js `vm` module](https://www.w3schools.com/nodejs/ref_vm.asp).

    const obj = require('vm').runInNewContext('({})');
    // `obj` inherits from a different JavaScript context's `Object` class.
    obj.constructor === Object; // false
    obj.constructor.name; // 'Object'

* * *

## More Fundamentals Tutorials

*   [The Promise then() Function in JavaScript](/tutorials/fundamentals/then)
*   [Promises in JavaScript](/tutorials/fundamentals/promise)
*   [The instanceof Operator in JavaScript](/tutorials/fundamentals/instanceof)
*   [Classes in JavaScript](/tutorials/fundamentals/class)
*   [JSON.stringify() in JavaScript](/tutorials/fundamentals/stringify)
*   [Object.seal() in JavaScript](/tutorials/fundamentals/seal)
*   [Intro to Object Prototypes in JavaScript](/tutorials/fundamentals/prototype)

</div>

</div>
