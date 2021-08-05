---
layout: page-back
title:  Building a modular design & dev architecture
description: The <strong>Community Directory 2.0</strong> is a tool to help members from the Google for Startups communities networking, hiring and staying connected with the space.
client: Google for Startups
client-logo: https://upload.wikimedia.org/wikipedia/commons/thumb/b/b6/Google_for_Startups_logo.svg/1280px-Google_for_Startups_logo.svg.png
tags: [UX research, UI design, Front-end Development]
image:  '/images/work/gfs-directory-2B.png'
---
Since we launched <a href="gfs-directory">the first version</a> of our Community Directory, many things changed. The global community went from offline to online, we welcomed new members from Japan, Korea and Warsaw, and the needs of both the members and the community builders evolved.

That version 1.0 was fairly simple, but our research pointed us to different new directions, and the Google team requested new features, so we decided to <strong>revamp the whole layout and the development pipeline</strong> to better adapt to product changes and improvements.

#### The layout was perfect... for just one thing

In Tel Aviv we discovered that people use Facebook as we use LinkedIn here in Spain–if you want to contact the CEO of a company you want to work with, you send them a friend request. Because Facebook is used both personally and professionally (and because the product itself is designed to be and endless source of content) the number of daily notifications turns valulable information into noise. 

That's why we designed <strong>the Home menu</strong>, a place where the community builder can publish relevant community updates and notify members when there's a time-sensitive activity going on (a small gathering with the founder of Waze that's visiting the space from 12:00 to 12:30 and so on).

The problem with our first layout was that it was perfect for showing a big grid of cards taking up a very small percentage of the space, but for any other menu... **it just didn't work**.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/directory-container.png)
<!-- *Search by skill* -->

#### Let's play it safe

We decided to **limit the width** of the main content and structure the product navigation around that. We kept the left pannel to show the user all the possible navigation options and added a right pannel for the profile viewer, so the user would be able to keep browsing the list of peope without having to close it.

For the People menu (and all other menus, too), a narrower container makes it easier to focus on the results: it's not an infinite list of randome people anymore–it feels like a curated database.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/directory-pannels.png)
<!-- *Search by skill* -->

That layout limited how we think about new features and also limited possible implementations; using a similar width for the main container in the mobile version, we also reduced developing workload in responsiveness–there's no need to design and mantain an XS and LG version of most components.

Te right pannel would be a full screen view on small viewports (aka mobile), and the left pannel with the visible navigation would be a fixed bottom bar.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/layout-responsive.png)
<!-- *Search by skill* -->

We're aware that some Google employees have Chromebooks or Pixel Slates –hybrid devices with not very common aspect ratios, somewhere between laptop and tablet–, and that community members can borrow one of those devices from the help desk.

Some members work with iPads or other tablets such as Microsoft Surface, so keeping that in mind, we tried to put some love into the "MD" viewport design.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/md-layout-2.png)
<!-- *Search by skill* -->

We gave all three containers a max-width, and the "LG" breakpoint would be the bigger one: in a giant screen you'll still see a 1.264px wide layout. As Adam Wathan and Steve Schoger note in Refactoring UI, "not every container has to be flexible".

A "mini" (XS) variation of the main navigation menu component would show up in laptops with narrower screens and in tablets in landscape orientation. In portrait mode, the tablet layout would work more or less like a scaled up mobile UI with a few tweaks: 2x spacing and a little ace up the sleeve.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/md-layout.png)
<!-- *Search by skill* -->

That ace is a typographic system that scales: we have a base font size that scales with media queries. The base font size is 14, making it great for mobile but too small for laptops and tablets, so we scale it to 16 and 20, respectively (14 * 1.250)

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/typo-scale-2.png)
<!-- *Search by skill* -->

It's as simple as picking a base size that's a multiple of 4 (our typographic grid is in base 4, because the layout grid is in base 8) and multiply it for a constant with a media query:

`media only screen and (min-width: $tablet) {
	font-size: $base-font-size * 1.250;
}`

where 

`$base-font-size: 14px;`

That way, in viewports where we really can't control our main container's width (tablets in portrait orientation, very wide smartphones...), typography will scale to fit.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/typographic-scale.png)
<!-- *Search by skill* -->

Optimal legibility is achieved calculating the number of characters in each line to avoid having less than 45 or more than 70, so if your container is 600px width width a 16px padding x2 (16 left + 16 right), with a 14px font size you'll have ~65 words per line in your body text.

![Search by skill]({{site.baseurl}}/images/work/gfs-directory-2/word-lenght.png)
<!-- *Search by skill* -->

That way we go from "too much negative space" to perfect usage of the available space without compromising the UI and achieving optimal legibility in each and every conceivable viewport (please, don't mention foldables or I'll hurt you very badly).