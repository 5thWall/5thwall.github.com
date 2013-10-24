---
layout: note
---

D3 for Data Visualization
==================

* Open Source Project (2010)
* Layer of "abstraction" over SVG
* Also support for HTML5 Canvas
* [mbostock/d3](http://github.com/mbostock/d3)
* Not good if you need to support IE8 and previous

Why D3?
----------

* Data visualization
* Extremely versitile
* Leverage JavaScript skills
* Leverage SVG

What can it do?
------------------
* All the stuff you can do in SVG
* graphics / animation
* filters / gradients
* mouse / keyboards events
* custom charts / graphs
* Support for Ajax, JSON, XML, CSV files

How does it work?
--------------------
* Create SVG with JavaScript
* Often uses method chaining
* Select-data-enter-append
  * "TMCIID3" The most Common Idiom in D3

### Simple Example

``` javascript
d3.select("body")
  .append("svg")
  .attr("height", height)
  .attr("width", width);
```

What about 3D?
-------------------
* No 3D support in SVG (but SVG2 in 2014)
* We can use JS to simulate 3D
* Combine CSS3 3D with SVG?
  * No Hardware acceleration with SVG

D3 and SVG elements
-------------------------
* Filters
* Patterns
