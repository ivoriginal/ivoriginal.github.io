---
layout: page-back
title:  Helping people connect, from Tokyo to Madrid
description: The <strong>Community Directory</strong> is a tool to help members from the Google for Startups communities finding their people
tags: [UX research, UI design, Development]
image:  '/images/work/gfs-directory.png'
---
<!-- > In the future, robots will do all the work, so the only reasonable profession to pursue is to build and repair robots (until they repair themselves!)
–<i>Young Ivo, 1998</i> -->

Your first day at a <strong>co-working space</strong> is pretty much like your first day of school. Usually there's someone that explains to you the schedule, the rules and where you can pee. 

You know that you have to take your own stuff (say books, say laptop) and some money for food, but as soon as you get there you start realising that you don't know anyone and your life as a co-worker is gonna be pretty miserable if you don't fix that <a href="https://www.urbandictionary.com/define.php?term=asap">asap</a>.

If you're lucky enough to get accepted into <a href="https://campus.co/">one of Google for Startups campuses</a>, you'll be surrounded by founders, amazing technical people and so on, so you'll want to meet as many people as possible while your –typycally six months– membership lasts.

#### Turning informal knowledge into actionable insights

At that time, <a href="https://codingcarlos.com/">Carlos</a> and I had been part of the Madrid community for 5+ years, so we had basically met everyone. When the campus team started exploring how they could help people connect inside the community, they didn't take long to notice that we might have some insights on that.

We had a lot of informal knowledge, but this was the perfect chance to organise it; we built a simple script and a list of topics that we wanted to understand better, and we kickstarted a round of interviews.

![Carlos and I, gathering insights]({{site.baseurl}}/images/work/gfs-directory/campus-london.jpg)
*Carlos and I, gathering insights*

The questions where divided into 5 categories: 

- <strong>First contact</strong>: how did you find about the campus?
- <strong>The community and you</strong>: what's your position in the ecosystem?
- <strong>Your own ecosystem</strong>: are you part of other communities?
- <strong>Hiring and getting hired</strong>: let's learn about your hiring/job hunting process.
- <strong>Tools and processes</strong>: how do you communicate with your co-workers? And with your colleagues from the knotting meetup? And with your friends?

Asking that very same questions in the Tel Aviv community lead to very interesting insights, but you'll have to keep reading to find out.

#### Unknown unknowns

We soon realised that the main problem when trying to integrate is that <strong>you don't know what you don't know</strong>. If you randomly talked with Carlos, he'll ask you about your background and find good matches for you. If no one tells you to talk to a connector like him, you'll probably be relatively isolated for a while.

We also found out that the main driver to look for new connections was asking for help with a certain tool or technology (say Mixpanel or Python), but if you haven't met at least one technical profile, who should you ask for help? 

Here we found the first feature for what'll eventually become the Community Directory: search by skill, not by name.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory/ss-search.png)
*Search by skill*

We finally decided to build a simple directory of people with the ability to search by name, company and skill; user-generated content is risky, so the campus would provide professional headshots by <a href="https://www.instagram.com/p/B_hgK19jhvD/" target="_blank">Mario</a>, their in-house photographer. 

<div class="gallery-box">
  <div class="gallery">
    <img src="https://storage.googleapis.com/gfs-directory/pic/U/z/UzubL6rgA4mUKX_i5n7Xl.png">
    <img src="https://storage.googleapis.com/gfs-directory/pic/7/K/7K2qmGuWr19TxudHgTFA2.png">
    <img src="https://storage.googleapis.com/gfs-directory/pic/7/g/7gB5n2TNG5b5KpWFmphZP.png">
    <!-- <img src="https://storage.googleapis.com/campus-directory.appspot.com/ddbb/images/User_98_resized.jpg">
    <img src="https://storage.googleapis.com/campus-directory.appspot.com/ddbb/images/user_183_resized.jpg">
    <img src="https://storage.googleapis.com/gfs-directory/pic/7/s/7sGIjuFf8pEDRTBslfPHi.png"> -->
  </div>
  <em>Headshots by <a href="https://www.instagram.com/p/B_hgK19jhvD/" target="_blank">Mario</a></em>
</div>

The back-end was a simple spreadsheet and the front-end was built with vue.js + Vuetify, because: 
1. we had total freedom to choose the stack, and we wanted to learn vue.js, so this was a great chance.
2. the directory was going to be promoted by Google as an internal pilot, so it needed to look like their products; Vuetify is an implementation of the Material Design principles for vue.js

We started styling our components using their brand guidelines as reference and built a simple layout that worked great in mobile as well as in desktop, but we made a great mistake. Despite conducting severall interviews to find out more about community members and their habits, when we started desgining, we ignored the context.

![First version]({{site.baseurl}}/images/work/gfs-directory/ss-first.png)
*The MVP was fairly ugly*

We assumed that you wander around the space looking for someone on your phone, so we focused on the mobile UI, following the "mobile first" mantra. Our mistake was to be so self absorbed. If you visit the campus, you can see almost everyone sitting at their desk, working on their laptops.

After releasing that first version, analytics helped us realise that +80% of traffic was from desktop. 

> The ability to see who has a similar skillset to your own is a great icebreaker.

On one hand, giving the search bar such prominent position gave us an idea of what things people hoped to find on the directory.

Implementing that quick filter bar greatly increased profile views and search by category

#### Searching is a mess

I need help with/I offer help with. Lo de los quick filters.

![Young Ivo and granpa]({{site.baseurl}}/images/about/granpa-and-ivo.jpg)
*Young Ivo and granpa (what a cutie!)*

<br>

#### Datalytics

After the initial pilot, it went well. The contract. A global product.

<br>

![Young Ivo and granpa]({{site.baseurl}}/images/about/granpa-and-ivo.jpg)
*Young Ivo and granpa (what a cutie!)*

<br>

#### Iterating

I need help with/I offer help with.

> The ability to see who has a similar skillset to your own is a great icebreaker.
> 
<cite>George Bernard Shaw</cite>

<br>

![Young Ivo and granpa]({{site.baseurl}}/images/about/granpa-and-ivo.jpg)
*Young Ivo and granpa (what a cutie!)*

<br>

Mazo cosas wapas.