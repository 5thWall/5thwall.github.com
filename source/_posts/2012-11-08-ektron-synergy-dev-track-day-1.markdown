---
layout: post
title: "Ektron Synergy Dev Track - Day 1"
date: 2012-11-08 11:19
comments: true
categories: Ektron "Ektron Synergy" C#
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
but not really suprizing considering the normal mode for displaying a smartform
was designed with XSLT in mind. Even though PageBuilder pages are represented as
XML internally, there's not really a way to display them with XSLT, and the
Ektron ContentBlock control would choke on them.

The other limitation had to do with date fields which can hold time information
but the smartform can't handle time. So, if you create a custom UI to insert
dates, be aware that anyone saving that smartform in the workarea will ovewrite
the time to 12AM.

[kma]: http://http://kmac23va.tumblr.com/ "The blog of Ken McAndrew"
[eect]: http://kmac23va.tumblr.com/post/17579016242/enhancing-ektron-content-types "Enhancing Ektron Content Types"
[bc]: http://twitter.com/billcava "Bill Cava, Ektron Chief Evangelist"
[ectw]: http://www.ektron.com/Resources/Webinars/Ektron-Content-Types/ "Ektron Content Types Webinar"

## Ektron Best Practices

Next we have the Ektron Best Practices talk by [Bill Cava][bc]. This talk was
very good at last years Synergy though this year contained a good amount of the
same information.

### Software Architecture

This was mostly the same as last year

### Object Types

 * Content Types
  - Smart Forms
    Why aren't you using smartforms? You should always use smartforms. We use
    smartforms for everything.
  - HTML Content
    Word content?
  - Binary
  - Page Builder
 * Content Metadata
 * Folders
 * Taxonomies
 * Taxonomy Metadata
 * Collections
 * Menus
 * Users
 * User Properties
 * Groups

Smartform Vs Metadata
Rule of thumb, smartform field when it will be displayed, metadata if it's
more relational (We're doing it right)
SF:
First class content items
Stored as XML
Fields are usually displayed

MetaData:
Not a centent object
Associated to content objects to form relationships between content
typicaly not displayed

Webinar on mapping smartforms to Plain c# objects

Content modling
Book: Content Strategy for mobile (helpfull for more than mobile)

### Development Tooling

APIS
Why are we not using the 8.5 Framework API
Managers for CRUD operations
Data Classes
Criteria

Content manager vs search manager

cm
Returns ContentData
Queries against Source of Truth (db)
Quiries against contentdata props
express simple critiria using filters

sm
Returns SearchResult
Search Index is not instantly updated
Queries against wide set of properties
Express Complex criteria using expression trees

#### templated server controls
Have no presentation logic baked into them.

Legacy Server controls are rubbish

Templated server controls give full control over markup

#### Page Builder

Don't overuse pagebuilder

### Development Tips

Create a layered application

Build a layer on top of ektron, only access ektron through business access layer.
*Beware of baklava code* Separate component responsibilities. Check out webinars.

When upgrading tho only thing that changes is the data layer.

Starter site with layers included.

Create an application config file.

Use smartforms for config values.

### Resources
