---
layout: blog
title: "Three Failed Apps and the Lessons Learned"
---
It's important to learn from our failures.  For that reason, I present three failed side projects I've worked on, and the lessons I've learned from each.

## Tutor Dashboard
My first attempt at a real SaaS app was Tutor Dashboard. I was inspired after reading [Brandon Pearce's success](http://www.fourhourworkweek.com/blog/2011/03/04/engineering-a-%E2%80%9Cmuse%E2%80%9D-%E2%80%93-volume-3-case-studies-of-successful-cash-flow-businesses/) with [Music Teacher Helper](http://www.musicteachershelper.com/). The idea of building an app to help out small service providers appealed to me.  I'd also recently started listening to [Rob Walling's podcast](http://www.startupsfortherestofus.com/), so I was generally brimming with inspiration.  I chose to create a scheduling and invoicing app for tutors, as I personally knew several people working as tutors. I made a few phone calls, explained my basic vision for the tool, and got generally positive feedback. Seeing this as validation, I got to work.

### The Beginning
I did do some things correctly.  I bought a Wordpress theme from Theme Forest, added a MailChimp opt-in form.  I had a writer from oDesk write a five part course on improving tutoring businesses as an opt-in bribe. The site's blog wasn't exactly jam packed with content, but I did have a pretty good base of posts going. Overall, I was pretty proud of my content.

As for the actual app, I'd never built anything at this scale before. I knew my way around Django, my chosen framework, but still had much to learn. I couldn't afford to outsource the development of the entire app, but I did decide to outsource the creation of the invoicing component to a developer from oDesk. Quickly, and in spite of some misteps, a basic app started to come together.

### Doubt Sets In
Due to my efforts on my marketing site, I soon ranked #1 for my chosen keywords on Google.  Despite this ranking, I was only getting a trickle of traffic coming in.  By trickle, I mean something like 5 visitors a day.  This was really hard to see, as I was really hoping for organic traffic to be a sufficient source of leads to sustain the app.  Unless I had wildly misjudged the top keywords for the niche, it didn't look like this would ever happen.

I also decided to throw a $100 AdWords voucher's worth of traffic at my (woefully unoptimized) opt-in page.  This yielded some opt-ins, but not nearly enough to be sustainable when using actual money to pay for the clicks.

My app was coming together, but cracks were appearing that I didn't know how to fill. My outsourced developer had become unresponsive, leaving me with a partially finished invoicing component. Due to my inexperience with Django, my app was becoming somewhat tightly coupled.  Changes and new features in one compomponent would break others.  I had yet to embrace the use of a robust test suite, so I often didn't know I'd broken something until I found it myself.  Overall, my confidence wasn't high.

### The End
Things really came crashing down when a competitor popped onto the first page of Google, sporting a much better looking product than I was working on. Their product was targeted at tutoring agencies, rather than individual tutors like mine was.  I'd started getting e-mails from people on my list who owned agencies, and were requesting specific agency focused features. Due to my clumsy design, extending the app to included agencies was a non-trivial task.  Every day I struggled in my spare time to get something workable, the competing product was pumping out fully formed features.

Ultimately, I gave up. A combination of burnout and a growing lack of confidence in what I was doing led me to stop working on the product. When I considered coming back to it, I couldn't bring myself to work on my existing code. To this day, Tutor Dashboard remains vaporware.

### Lessons Learned
I learned a lot from this experience.  Specifically:

* Building a full scale SaaS app as your first major product in a framework is very difficult.
* It's not enough to identify a market (tutors).  It's important to understand who in that market (agencies) is actually willing to pay money for a solution.
* Competitors will show up, and they will be de-moralizing if you're not confident that you can provide a better product. 
* Search volume estimates from popular keyword tools can be misleading. Don't bank your app's success on a specific #1 ranking.
* Building and communicating with a pre-launch list is a tremendously informative exercise.

## Wedding Videographer Directory
My next app took a very different tack than my first. Inspired by some popular directories for wedding photographers that charged a monthly fee for premium listings, I decided to apply this concept to videographers in the same industry. Building the basic directory site was quite simple. I integrated with Vimeo Pro to allow videographers to upload their videos. I paid a worker on oDesk to build out a spreadsheet with 20 videographers from each state.  Another worker wrote a simple description for each one.  Once imported into the site, I had a fully populated directory with unique descriptions for every business.  

My theory was that the power of the long tail would kick in, and I would begin getting traffic to the site to all my business decsription pages. In the mean time, I began e-mailing videographers one by one to get them to upload their portfolio videos to their profiles, and "claim" the profile for themselves. I had some success with this, but adding even non-paying users was slow and tedious.  

Even with a growing collection of active profiles, I wasn't picking up any search traffic.  Since the business model depended on selling premium listings, I needed solid organic traffic to justify the cost.  I wasn't getting this at all.  After a year, when it was time to re-up for my Vimeo Pro subscription, I decided to shut the site down rather than pay for a site that wasn't anywhere close to earning a dime.

### Lessons Learned
* Once again, *don't rely on organic traffic for your business model!* I'm apparently slow at learning this lesson.
* Keeping the scope simple makes it easy launch and validate the idea. Idea to initial launch only took a few weeks, thanks to the smaller scope and my much improved Django skills.
* "Freemium" is too much work for me.  Going to charge people from here on out.

## Craigslist Ad Tracker
One week, I found myself selling a large number of items on Craigslist. I quickly found myself frustrated with the lack of data Craigslist provides.  How many views was I getting for my listings?  What time of day was best to post?  Where were people viewing my listings from? If I had answers to these questions, I could do a better job selling my stuff.  

True to form, I decided to build a tool to solve this problem.  I threw together a simple pixel tracker using [Scalatra](http://www.scalatra.org/) and [Akka](http://akka.io/), which was a learning exercise in itself. I started tracking my ads, with decent results.  This only took a few days to get working.

### The Problem
I quickly realized that I had a useful product on my hands. I was about to whip up a billing system and a marketing site, when I decided to read the Craigslist terms of service.  I quickly realized that tracking the IPs and geoIP locations of the ad viewers would break the ToS.  No matter, I thought, I can just leave that feature out.

The real finishing blow came when Craigslist announced that they would no longer be allowing `<img>` tags in "for sale" ads. Without the ability to embed the tracking pixel into the ad, the tool would be useless.  Another app, another failire.

### Lessons Learned
* Don't rely on another platform's implementation for your product's core feature.
* Scratching your own itch can lead to ideas worth validating.
* Getting a working prototype that solved the problem in a few days rather than a few weeks really reduced the pain of failure.

## Conclusions
Despite all of these failures, I'm still glad I built each of the above apps. The lessons I've learned from each of them have stuck with me, and the technical knowledge I've gained from each has been tremendous, as well. Please comment below and let me know about one of your failed side projects, if you have any.  
