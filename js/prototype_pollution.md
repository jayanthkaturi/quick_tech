
[Source](https://medium.com/@daniakash/what-is-prototype-pollution-and-why-is-it-such-a-big-deal-2dd8d89a93c "Permalink to What is prototype pollution and why is it such a big deal?")

# What is prototype pollution and why is it such a big deal?

![Dani Akash][1]

It has been gaining a lot of traction recently but turns out it's been actually there since the dawn of Javascript

Photo by [Thomas Millot][2] on [Unsplash][3]

If you were following the news last month, you probably would have come across how jQuery received a new security patch which addresses the prototype pollution flaw. It is a huge deal, given how **74 percent** of all internet sites use the vulnerable version of the library!

Photo by [Greg Rakozy][4] on [Unsplash][3]

> Now before we all panic, prototype pollution isn't exactly an easy vulnerability to be exploited. It needs a fair amount of knowledge on the application architecture to be exploited. This also means all those open source Javascript frameworks and projects in Github are at a huge risk of being exploited.

Before we dig deeper into how much the risk is spread, let's understand what exactly causes the prototype pollution. In Javascript, prototypes define an object's structure and properties so that the application knows how to deal with the data. But it turns out if you modify the prototype in one place, it will affect how the objects work throughout the entire application.

Wait, What?!

Overwriting the prototype of a default javascript object is considered a bad practice for a long time. You might wanna try reading [this article][5] by Nicholas C. Zakas back in 2010.

So, you might not do it in your code. But what if the prototypes can be modified by someone else? That is my friend, **prototype pollution** and it happens due to some unsafe **_merge_**, **_clone_**, **_extend_** and **_path assignment_** operations on JSON objects obtained through user inputs.

It is pretty common in Javascript that you wanna merge two objects together. Generally, this is how such a merge operation looks like the following code snippet.

A typical object merge operation that might cause prototype pollution

The merge operation iterates through the source object and will add whatever property that is present in it to the target object. It's simple. But also makes things complicated if the source is supplied by a 3rd party.

All the attacker has to do to pollute your prototype is to provide you JSON data that has the **___proto___** property. A common payload will look something like this:
    
    
    {  
    "foo": "bar",  
    "__proto__": {  
    "polluted": "true",  
    }  
    }  
    

If you pass this payload to your merge operation without sanitizing the fields, it will completely pollute your object prototypes.

Prototype Pollution in action

> This kind of vulnerability is identified in the [hoek][6] package used by millions of projects

The severity of pollution depends on the type of payload and how you use your objects. If you use them to authorize admins
    
    
    if(user.isAdmin) {  
    // do something  
    }

Then it will let the attacker get access to sensitive information by polluting the scope with the **_isAdmin_** property. If the attacker changes some existing attribute to an unexpected return type (say toString attribute to return type integer) it will cause your application to crash (**Denial of Service**) or if you are using your server for code execution like **_node.js exec_** or **_eval_** then it might even lead to **Remote code execution(RCE)**.

Olivier Arteau explaining RCE with prototype pollution on GHOST CMS

## **So, How many libraries are affected?**

As per [Snyk][7] reports, there are more than 20+ known vulnerabilities across different packages that run on Node.js and the browser. There might be many that haven't yet been discovered.

## When was it discovered?

The term Prototype pollution was coined many years ago. It probably exists ever since people started using vulnerable operations in Javascript.

## What is the fix?

If you are using a vulnerable operation like the merge operation we saw above, you can fix it by simply preventing the merge if the key name is **___proto___** like the following code.

A safe object merge operation that will not allow prototype pollution

## What if the vulnerability is introduced by an NPM package?

In this case, first, you should check if you are affected by a vulnerable package by running the [**npm-audit**][8] command and you can mostly fix it automatically. Many popular vulnerable libraries such as jquery, lodash, hoek, etc have been updated to address prototype pollution.

If you happen to find a vulnerability in the package you use and an update hasn't been released for it, immediately notify the maintainer of the package.

There also happens to be some rare cases where **_updating the package might break the whole project_** like [this scenario][9] or the **_update will take a long time to be released_** like [this case][10]. If you happen to fall into one of these rare categories, you might wanna read how to fix prototype pollution with [no-pollution][11].

## What are the other vulnerable methods like merge?

**_Clone operation_** which is basically, merge operation on an empty object
    
    
    var clone = function(objectToBeCloned) {  
    return merge({}, objectToBeCloned);  
    }

**_Path-value assignment operation_** where you can define the property of an object by directly accessing its path. A vulnerable path assignment operation will look something like the following code snippet.

A vulnerable path-value assignment operation on a javascript object

The following code snippet explains how the above method causes prototype pollution
    
    
    var obj = pathAssignment({}, 'foo', 'bar');   
    // This will create and object { foo: "bar" }var obj = pathAssignment({}, '__proto__.polluted', true);  
    // This will totally pollute your object prototypes!

Path assignment based prototype pollution vulnerability is rare but it cannot be fixed by [no-pollution][11]. So, make sure the path of the operation can never be controlled by any 3rd party other than your own code. One known case of this vulnerability is affecting the [mpath][12] package which already received a fix.

Good programming practices will automatically mitigate prototype pollution attacks. Since this attack relies heavily on the data sent from the client side, make sure you sanitize them all and also run the npm-audit periodically to keep track of vulnerabilities in the packages you use. After all, It is better safe than to be sorry.

[1]: https://miro.medium.com/fit/c/96/96/1*VerZ4tpgqDL24M52i76cmQ.jpeg
[2]: https://unsplash.com/@tomlaudiophile?utm_source=medium&utm_medium=referral
[3]: https://unsplash.com?utm_source=medium&utm_medium=referral
[4]: https://unsplash.com/@grakozy?utm_source=medium&utm_medium=referral
[5]: https://humanwhocodes.com/blog/2010/03/02/maintainable-javascript-dont-modify-objects-you-down-own/
[6]: https://snyk.io/vuln/npm:hoek:20180212
[7]: https://snyk.io/
[8]: https://docs.npmjs.com/cli/audit
[9]: https://stackoverflow.com/q/50564246/5597641
[10]: https://stackoverflow.com/q/51696923/5597641
[11]: https://www.npmjs.com/package/no-pollution
[12]: https://snyk.io/vuln/SNYK-JS-MPATH-72672

  
