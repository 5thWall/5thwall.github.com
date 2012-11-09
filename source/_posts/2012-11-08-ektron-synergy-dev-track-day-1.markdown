---
layout: post
title: "Ektron Synergy Dev Track - Day 1"
date: 2012-11-08 11:19
comments: true
categories: Ektron EktronSynergy C#
---

I'm attending [Ektron Synergy][eksy] this week for work and I've decided to
publish my notes from the Developer track.

[eksy]: http://synergy.ektron.com "Ektron Synergy Conference 2012"

## Beyond the Workarea

First up we have "Beyond the Workarea" by [Ken McAndrew][kma] from C-SPAN. Ken
talked about the reasons a company might want to go outside of the Ektron
Workarea, and gave a bit of demo of their custom UI. The talk didn't go into any
code, instead focusing on basic concepts. The big technical take-aways for me
were some smartform limitations he enumerated and an [updated version][eect] of
the code from [Bill Cava][bc]'s [Ektron Content Types Webinar][ectw].

The two smartform limitations had to do with specific field limitations, first
is that PageBuilder pages can't be selected for a content resource. Kind of lame
but not really surprising considering the normal mode for displaying a smartform
was designed with XSLT in mind. Even though PageBuilder pages are represented as
XML internally, there's not really a way to display them with XSLT, and the
Ektron ContentBlock control would choke on them.

The other limitation had to do with date fields which can hold time information
but the smartform can't handle time. So, if you create a custom UI to insert
dates, be aware that anyone saving that smartform in the workarea will overwrite
the time to 12AM.

[kma]: http://http://kmac23va.tumblr.com/ "The blog of Ken McAndrew"
[eect]: http://kmac23va.tumblr.com/post/17579016242/enhancing-ektron-content-types "Enhancing Ektron Content Types"
[bc]: http://twitter.com/billcava "Bill Cava, Ektron Chief Evangelist"
[ectw]: http://www.ektron.com/Resources/Webinars/Ektron-Content-Types/ "Ektron Content Types Webinar"

## Ektron Best Practices

Next we have the Ektron Best Practices talk by [Bill Cava][bc]. This talk was
very good at last years Synergy. This year's talk contained a good amount of the
same information which is a little disappointing but not entirely unexpected.
Bill pushed using smartforms, which is what we've already found to be very good
advice in general. Some things that were new for this year (as far as my
recollection goes anyway) included a few suggestions about when to use various
features and APIs.

### SmartForm Fields vs MetaData

Just like last year Bill really pushed using SmartForms for most content. At
[NAU][nau] we've very much found that to be the case. This year he added some
information about when to use a SmartForm field vs. when to put information into
the Content MetaData. Just as a general rule of thumb, use a SmartForm field
when the information is going to be displayed on the page. Metadata would be a
better choice for relating in other pieces of content. This is advice we're
following at work, so it's nice to see that we're on the right track.

While talking about modeling data in SmartForms, he mentioned the book
[Content Strategy for Mobile][csfm] as being a good resource for thinking about
how to break down content, and that it was good for more than just mobile.

### ContentManager vs SeachManager

Bill also went over the differences between the ContentManager and the
SearchManager in the new Ektron Framework API. This seemed to be mostly stuff
one might guess. The ContentManager has some simple filters that are limited to
the properties of ContentData, but has up-to-date and accurate information
coming directly from the database. SearchManager, on the other hand, has a more
expressive way of quering for data, but might not contain the latest, or latest
version, of content.

### Three-Tier Architecture & Templated Controls

Coming up soon is an Ektron MinSite install that creates a basic Web Application
project using a multi-tier architecture. Starting out it should just be
available through the [Synergy site][syn], but will later be one of the default
installation options.

Related to that, the old Ektron server controls won't work with a 3-tier
solution, but v8.6 introduced templated Ektron controls which now do. As an
added benefit, developers can now specify the output of the control just like
any other templated control (e.g. ListView, Repeater).

[nau]: http://nau.edu/ "Northern Arizona University"
[csfm]: http://www.abookapart.com/products/content-strategy-for-mobile "A Book Apart - Content Strategy for Mobile"
[syn]: http://synergy.ektron.com "Ektron Synergy Conference"
