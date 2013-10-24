---
layout: note
---

Web Components Revolution
=========================

Rob Dodson  
[@rob_dodson][twitter]

* Web Components?
* The Specs
* Use 'em Today!

**How do you use Bootstrap/jQuery UI/etc?**

1. Go to docs
2. Copy all the things
3. Get widget
4. Repeat

We can do better. Just use the thing. Web Components!

1. Create your own HTML elements
2. Encapsulate your styles
3. React with lifecycle callbacks

Web components use the same tools that the browser makers use.

``` html
<chart-pie></chart-pie>

<mark-down>
  ## O hai!
  ### how _you_ doin?
  [Link me!](foo.com)
</markdown>
```
    
What are Web Components?
------------------------

**Templates:** Scaffolding  
**Shadow Dom:** Encapsulation  
**Custom elements:** Extensions  
**Imports:** Packaging  

### Templates
Inner chunks of DOM that we can re-use throuought the page.

``` html
<template id="my-widget">
  {{ content }}
</template>
```

#### Gotchas
No built-in data interpolation `{{ }}` don't do anything yet
Nested templates are not automatically activated

Works on Chrome/Mobile Chrome, Firefox, Opera/Opera Mini

### Shadow Dom
Huge topic

Provides Style and markup encapsulation

Same technology used by browser makers to implement `<video>` etc.

Shadow Host : node contains all our shadow dome , shadow root : first node, shadow nodes, shadow tree, shadow boundary : container

    element.createShadowRoot()
    
Can put styles inside the `<template>`

`applyAuthorStyles` allows authors to style your elements

`root.resetStyleInheritance`

You can poke holes in the shadow boundary using `part`

``` javascript
part="foo"
.widget::part("foo") { color: red; }
```

Insertion points use `<content>` takes stuff inside the shadow host and puts it into the shadow dom. Specific content can be selected with "select" attribute.

Browser support: chrome/mobile chrome, opera/opera mini.

### Custom Elements
Templates + Shadow DOM = Custom elements

``` javascript
document.register('tag-name', {
  prototype: proto
});
```
    
#### Lifecycle Callbacks
* `createdCallback()` Use like constructor
* `enteredViewCallback()` When an element is added to the page
* `leftViewCallback()` When an element is removed, cleanup
* `attributeChangedCallback(attrName, oldVal, newVal)` When one of an elements attributes changes

Type extension elements, use `extends`, and `is="my-element`

Ignore blog posts about `<element>` for now, right now only method for creating element is Javascript.

#### Imports
Imports load external documents into our page

``` html
<link rel="import" href="my-import.html">
```

Like CSS, just assume it's there and work.
Browser support: Chrome with a flag

Use 'em Today
-------------

### Polymer
A collection of polyfills which let us use web components in all modern browsers.
Also a framework for building web applications with web components.
Looks a lot like angular, from Google so maybe similar codebase? Probably work together

Resources
---------
* [HTML5 Rocks][h5r]
* [Polymer][poly]
* [X-Tags][xtags]
* [Brick][brick]
* [customelements.io][custom]
* [Chromium dashboard][chrome]

[twitter]: http://twitter.com/rod_dodson
[h5r]: http://www.html5rocks.com/en/
[poly]: http://www.polymer-project.org/
[xtags]: http://x-tags.org/
[brick]: http://mozilla.github.io/brick/
[custom]: http://customelements.io
[chrome]: http://www.chromestatus.com/features
