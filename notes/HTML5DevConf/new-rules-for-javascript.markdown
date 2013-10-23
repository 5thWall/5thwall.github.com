---
layout: note
---

New Rules for Javascript
===================

* http://youdontknowjs.com
* http://html5hub.com

This code will "hurt your feelings"

Javascript is not a dynamically typed language. Javascript does have types. Not type enforced.

Values have types in javascript, variables do not. Values have types and they can not change, but variables can hold any value at any time.

## Stop hating on `==` and implicit conversion.

* `==` allows coercion
* `===` disallows coercion

## Never treat `null` and `undefined` differently
You'll be rewarded with simpler and possibly faster code

## Stop using anonymous functions

``` javascript
function foo() { }
```
    
Bind gives us currying and closures. Named function expressions are always preferable. Also, stop bloating function closures.

Don't just assume the JS engine optimizes away all mistakes.

## Stop abusing your scope
Follow the principle of least exposure. Block scoping is coming and better than manually hosting variables.

Let blocks can work now in ES3. http://gethub.com/getify/let-er

Start also using block scoping, "let is not the new var"

## Stop using `this` until you really understand how it gets assigned

1. Is the call-site new-invoked?
2. Is the call-site binding overridden with call/apply?
3. Is the call-site on an owned-object?
4. Otherwise use global (except in strict mode)

`this` is only magical or confusing when you don't find the call-site.
`var self = this` is often (but not always) missguided, you can often use `.bind(this)`

## Stop using `new Something()` "constructors" to "instantiate" and "inherit" classes.

Objects Linked to Other Objects
Class-oriented vs delegation-oriented

### Delegation-Oriented
Just use objects.
