---
layout: note
---

Concurrency and Parellel Programming in JS
==========================================
* Concurrency
  * Event-driven async programming
  * Promises
  * Web Workers
* Parallel
  * SIMD units
  * Multi-core Processors
  * Programmable GPUs

Concurrency
-----------

JavaScript Execution Model

* Single event queue
* Events run to completion, no interleaving
* Events may create new events
* Ordering of events may be non-deterministic

### Race Conditions

Always make sure your callback is defined before an event can fire.

### Errors can happen anywhere in your application.

Enter: Promises

* Promises/A+
* cujojs/when
* jQuery Deferred Objects

### Long Running Scripts

Enter: Web Workers

Spawn a second instance of  the JavaScript Engine

* No shared state
* Communicate using messages

Parallel Computing
------------------

Task Parallelism with Web Workers, it's up to the operating system. As a web developer you don't know.

### SIMD Programming

Single Instruction Multiple Data

* Typically on 4 or 8 element vectors
* Perform the same operation on each element
* Conditional control flow has to be encoded by merging values

    add [1,2,3,4]  [2,3,4,5] => [3,5,7,9]
    lessThan [1,2,3,4]  [4,3,2,1] => [T,T,F,F]
    select [T,F,T,F]  [1,2,3,4]  [2,3,4,5] => [1,3,3,5]
    shuffle [3,2,1,0]  [1,2,3,4] => [4,3,2,1]

Proposal by John McCutchan

* Add special vector-value types
  * SIMD style accessors
* Also arrays of these
* Use static SIMD object to provide a set of intrinsic operations

``` javascript
// Assume a and b are instances of Float32x4Arrays
var x = new Float32x4Array(a.length);
for (var i = 0; i < x.length; ++i) {
  x[i] = SIMD.add(a[i], b[i]);
}
```

``` javascript
var x = new Float32x4Array(a.length);
for (var i = 0; i < x.length; ++i) {
  var x_t = SIMD.add(a[i], b[i]);
  var x_e = SIMD.add(a[i], b[i]);
  var p = SIMD.greaterThan(a[i], 10);
  x[i] = SIMD.select(p, x_t, x_e);
```

### Parallel JavaScript (formerly River Trail)

High-level data-parallel programming API

* Operates on n-dimensional arrays
* Perform the same operation on each element (mostly)
* Designed for multi-core CPUs and programmable GPUs

Proposal by Intel Labs and Mozilla

* Extends standard JavaScript array objects and upcoming typed objects (formerly binary data)
* Provides new parallel methods
  * buildPar (factory)
  * mapPar
  * reducePar
  * scanPar
  * scatterPar
  * filterPar

``` javascript
var a = [1,2,3,4,5,6];
a.mapPar(function (v) { return v+1; });
```

Temporal Immutability: The global heap is immutable during parallel execution. Callback can not change the global scope. No side-effects.

``` javascript
// Will not work
var a = [1,2,3,4,5,6];
a.mapPar(function (v, i) { ++a[i]; });
```

Typed Objects: Grayscale

``` javascript
var Pixel = new ArrayType( uint8, 4 );
var Image = new ArrayType(ArrayType( Pixel, 480), 320);

var I = getImage(); // returns value type of Image

I.mapPar(2, function (v) {
  var lum = v[0] * 0.21 + v[1] * 0.72 + v[2] * 0.07;
  return new Pixel([lum, lum, lum, v[3]);
}
```

SIND and Parallelism can provide speedups in image processing.

* Firefox implementation in progress, available in the latest Nightly
* ECMA proposal available for comments

Conclusion
----------

Concurrency is a given in web Development

* Be aware of event semantics
* Promises are awesome
* Use Web Workers

Parallel Computing offers additional speedup

* Web Workers
* SIND is on it's way
* Parallel JavaScript for larger scale parallel computing
