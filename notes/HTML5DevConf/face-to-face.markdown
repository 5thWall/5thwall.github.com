---
layout: note
---

Face to Face Video for Fun and Profit 
=====================================

Making WebRTC work in the real world

Badri Rajasekar  
VP Engineering Tokbox  
[@baddn][baddn]

Overview
--------
* Basics of WebRTC
* Signaling
* Connectivity
* Interoperability
* Multi-party
* Ease of use
* Real world use-applications

WebRTC = Real time communication APIs. Browser to browser applications for voice calling, video chat, and P2P file sharing without plugins.

State of the Union
------------------
* Desktop
  * Chrome 23+
  * Firefox 22+
  * Opera 12
  * IE (Chrome Frame)
* Mobile
  * Chrome 29
  * Firefox 24
  * Opera 12

### Example

High Level P2P call

Phases

* Gain access to hardware input
* Negotiate and set session initialization
* Establish connectivity
* Send/receive media

### What can you do?

Not just for voice/video

#### Data Channels
* `createDataChannel()`
  * P2P data transport
* Reliable: TCP
* Unreliable: UDP

#### Examples
* BannanaBread
  * Mozilla FPS
* peerCDN
* Sharefest
  * Send files directly

Pretty Powerful, but the Real World Strikes

Signaling
---------
* The standard doesn't speak about how the signaling mechanism works
* Protocol options
  * Custom
  * SIP
  * XMPP
* Third party
  * Firebase
  * OpenTok
  * Channel API
* Depends on your application level messaging requirements

Connectivity
------------
* Real world use-cases involve people behind restrictive NATs/firewalls
* ICS is a framework for navigating NATs
* ReSTUND, TURN Server, rfc5766-Turn-Server

Interoperability
----------------
* What's the problem with mobile?
  * WebRTC reference implementation
  * Lack of browser support: Chrome 29 + Android
  * WebRTC - Audio Codec OPUS & Video Codec VP8
  * Software Encoding is expensive on mobile devices
  * Native Applications
* Problem on the desktop?
  * Safari + IE (CU-RTC-Web)
  * IE has a separate standard / fragmentation

Multi-Party
-----------
* WebRTC is inherently a P2P protocol
* Media Mesh: A mesh of peer connections
* Media Router: 3^rd party service (OpenTok) or build yourself

Quality Matters

* Every endpoint reports RTPC feedback to the publisher
* Common problem is to degrade to the lowest common denominator

Three applications from the real-world
--------------------------------------

###1. Remote classroom
* Multi-point scalable traffic
* Speaker support
* Bandwidth application to avoid LCD challenges

### 2. Insurance claims adjustment
* "See what I see" use cases
* Also requires device support
* Camera manipulation presents challenges

### 3. Robots
* Turns out that there's more than "Web" in WebRTC
* Telepresence robots
* All about device support
* All about connectivity

The Future
----------

Why you should be paying attention?  
More than a billion endpoints this year.

What's missing

* Mobile
* Multi-party
* Recording
* More, he changed the slide away too soon.

[twitter]: http://twitter.com/baddn
