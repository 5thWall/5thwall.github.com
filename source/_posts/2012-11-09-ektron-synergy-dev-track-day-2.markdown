---
layout: post
title: "Ektron Synergy Dev Track - Day 2"
date: 2012-11-09 09:16
comments: true
categories: Ektron EktronSynergy C# Aloha
published: false
---

Continuing into day two of the Ektron Synergy developer track.

## Flight of the Pheonix

## Making the 8.6 Editor Your Own

### Editor conundrum

Original editor was based on Telerik

Why most editors can't keep up: older editors use IFrames for inline editing with CSS. ContentEditable was here the whole time, and HTML5 expands it to almost any tag. This goes back at least 4 versions in every browser (with div tag).

It's a (user) experience

Content is king, but only after you create it. The content editor has been a large pain point for us and apparently a lot of other users.

console.log("Aloha World")

How he chose Aloha, looking at features, compatibility, ux, speed, and extensibility.

Aloha is more of a true WYSIWYG editor. [Rangy selection library][rsl].

making it your own

Built in extension points included
new editor control, configuration options (whitelist tags allowed), 9 prebuilt ektron plugins. Ektron looking to contribute back to the Aloha community, nice.

jquery ui all plugins are self contained js modules (easy to create/follow code)

Authoring experience

Ektron is very commited to improving authoring experience based on customer feedback, more configuration options, providing better customization points, adding additional integration points.

upcoming features

EVEN BETTER experience! x-browser compatibility, tighter integration points, workflow
drag and drop assets
server control integration (forum/blog)
better source editing support (syntax hilighting/formatting/line#s)
Editing personas
uniform in/out of context editing
meaningful mobile/tablet support
forms and more!

NO ALOHA FOR SMARTFORMS!!! boooo

right now 2.0.x, PHX will have jquery ui proposal

after phx plugins will be moved out of workarea

[rsl]: https://code.google.com/p/rangy/ "A cross-browser JavaScript range and selection library"

## Search in 8.6

The Ektron Search in 8.6 comes in 3 flavors
Serch Server Express <10 mil
Search Server >10mil
FAST Search >100mil

needs dedicated search, can't load-balance

Setup stuff, hardware, ports, admin, install search server, configure search server, connect ektron to searchserver, can decide what things the search server will crawl (can leave out forums, products, etc)

search views as the builtin user, search is going to see the entire site
search may see menu items, can hide stuff from the builtin user programatically (seems like a hack, but I'm not afraid of those) [ChrisJocquesJWU]
