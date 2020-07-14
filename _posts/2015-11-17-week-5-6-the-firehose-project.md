---
layout: post
title: Week 5 & 6 - the Firehose Project
date: 2015-11-17 02:23:48.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- firehoseproject
tags:
- codenewbie
- coding
- rails
- ruby
- rubyonrails
- tdd
meta:
  _edit_last: '1'
  _wpas_done_all: '1'
  classic-editor-remember: classic-editor
author:
permalink: "/2015/11/17/week-5-6-the-firehose-project/"
---
Week 5 & 6 have been the most challenging so far, the biggest challenges being Test Driven Development and coding challenges #3 and #4. I have been literally pulling out my hair & will be bald at the end of this program. LOL

Last time I blogged, I had worked on "Image Blur #1". The second coding challenge, "Image Blur #2" continued from "Image Blur #1". The challenge is to transform this:

```
0000 0100 0001 0000
```

to this(transforming the top, bottom, right, and left pixels next to the original 1 to a 1):

```
0100 1111 0111 0001
```

My mentor suggested I look up shallow vs. deep copies and the "Marshal" class. That and the .each\_with\_index method really helped with getting through this challenge. Then I started on Image Blur #3 - now instead of doing a 1 pixel transformation, I had to transform it by the "Manhattan distance". That took more than two loops.. I solved "LinkedList #1" today with the help of my mentor. That bad boy took me a good week and lots of drawings. I couldn't use&nbsp;arrays to loop through and mess around with so that drove me crazy. Next up is "LinkedList #2".

The test driven development section was difficult to process. My brain was just not focusing that day so I had to start all over the next day. By testing Splurty and Nomster, I was able to get a good idea of why we should use TDD- less or no bugs, tests cover your ass, etc. I've been trying to test as I build Flixter and it's still something that I am struggling with everyday but I am trying really hard to understand as I know it's super important when developing at work.

I've started Flixter & it's feels like they are taking away my training wheels! Flixter is a Udemy-clone with abilities for student and instructor login, courses/sections/lessons creation, and video uploads. So many self-directed steps. This is good & I actually know what I'm doing! I know how to install Twitter Bootstrap, add a top navigation bar, and integrating user login abilities using the devise gem. Feels good to say that. Although I did run into some problems with the bootstrap gem version and having to install sprockets but that's the life. Having to overcome problems using Google, GitHub/Gem docs, and Ruby/Rails docs is now the norm.

I went to my first Ruby meetup here in San Diego. It was cool and strange to see people that use ROR because so far I've been in my cave coding on my own. The two talks were great and I was not lost! I didn't stay after the talks because I felt really shy & new :/ Hopefully I get rid of all those feelings next time.

I leave you here - going to work on Flixter, TDD, and LinkedList #2.

Sending good vibes!

&nbsp;

