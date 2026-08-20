+++
title = "Aus Fencer"
description = "A web app for hosting fencing tournaments and more."
date = "2026-08-13"
menu = "main"
author = "Benedict Setiawan"
+++

## [GitHub Link](https://github.com/RattlePenguin/ausfencer.git)

## Introduction

insert picture of fencing here

Fencing is an interesting sport.
First, you realise that you've never actually used your legs in your life.
Then, you spend years learning proper footwork, shedding blood and sweat and
incurring perpetual knee pain.
Finally, once you feel like you're getting pretty good,
you get destroyed by a kid 7 years younger than you at your first competition.

While I have an amazing ability to cry about fencing for hours,
I'm not really here to talk about that.

I want to walk you through a recent project I did to help make fencing
more accessible across the world. To start with, let's go through some
basics of fencing.

## Fencing

You may not know this, but fencing is a sport played between three people.
Two are fencers, and the third is the referee.
The referee plays a significant role in determining which fencer is awarded
the point, as well as keeping track of score and penalties.
This is normally done by looking at an electric scoreboard which lights up
when either fencer lands a hit, and using a remote to interact with it.

insert picture of favero

The issue is, for many clubs buying scoring kits can cost upwards of hundreds
if not thousands of dollars.
There aren't many ways to circumvent this if you want a true fencing experience,
however a widely accepted practice is to buy just the reels and lights, or to
fence without electrics. At [UNSW's Fencing Club](https://www.instagram.com/unswfencing/), we do that quite often.

The bare minimum most would accept is a set of reels (wiring) and a light up box.
This at least guarantees that when a touch is made, a light signal appears.
Unfortunately this is still very expensive, and you must keep track of
score on your own.

Fencing without electrics is a last resort, and a good referee makes it quite
possible to evaluate bouts accurately.
Referees usually use their fingers, paper, or edit a text file on their phone
to keep score.
As you might probably guess, fingers are barely reliable,
and a text file is definitely a step up, but not without room for improvement!

In my club, the idea of a phone app that helps keep score has
floated around for ages.
This would allow referees to focus less on their fingers and more on the game.
An equally demanded tool is one that allows the organisation of in-house competitions.
[FencingTimeLive](https://www.fencingtimelive.com) is the standard for hosting fencing tournaments, but it has
a yearly cost and feels a little bit dated.
During my exchange semester at UT Austin, I also took notice of a US-specific website called [FencingTracker](https://fencingtracker.com).
In fact, [I'm on there](https://fencingtracker.com/p/101785318/Benedict-Setiawan)!
This stores fencer-specific data which outlines competitions and clubs you've participated in.

I thought I would try my hand at combining the three, creating a seamless link between
refereeing a bout, storing that bout as data and linking it to fencers within Australia.

## Problem Summary

| Problem | Solution |
| -------------- | --------------- |
| If referees use their hands to keep score, they may lose track. | Provide an accessible UI on their phone to store bout information. |
| Bouts in practice sessions don't get stored when wanted, which could help spot weaknesses and progress. | Automatically store finished bouts into a database, aggregating stats to give fencers a profile. |
| Tournament hosting requires a FencingTimeLive subscription, which may be unsustainable for practice sessions. | Create a tournament hosting feature. Storing official licenses can be added later. |
| Tournament sites may have poor signal, forcing hosts to write on paper to key in results. | Requires a phone app to run source code while offline. This sounds difficult. |

## Tech Overview and Stack

I'll try not to go too deep into the technicalities of this project.
This isn't a README, though I do encourage you to try it out for yourself.

I started by mapping out what I expect users to see.
For referees, we should expect them to open some page on their phone,
emulating a scoring remote.
Once done, the bout scores, penalties, and additional notes can be
submitted to the database.
The data may be structured such that fencers are unique, allowing them to
search themselves up and see which bouts or tournaments they were in.

I decided to use C++ for our backend services, not because it was the most suitable
but because I am currently trying to master it.
C#, Java or Go may be more worthwhile to ease the use of dependencies.
Many high performance web server stacks still use C++ frameworks, but we
likely won't observe the benefits of such speed.
Another reason to use C++ is if I decide to extend this project
into the low-latency fencing equipment hardware.

For the server side, I used external C++ libraries
[Crow](), [SQLite](), and [SQLite_ORM]()
to manage the HTTP server, API, and database.

## Trying It Out

## Next Project

Many doubts surface about the nature of this project.
The core problem at hand is less about the ability to track bouts.
In most cases, it's not acceptable to fence without electrics, so
we should be trying to create a cheaper, broader alternative to
standard brands like Favero.

Instead of creating a specialised device to act as a scoreboard, I want to see
if fencing equipment can be hooked up directly to a laptop.
A laptop is much more accessible, and it seems like the bottleneck is converting
electrical signals from the three-prong plugs into data we can read.
If we can do that, then all we need is an adapter that connects two three-prong
plugs and our USB-A socket.
This should be much cheaper and easier than building a whole device to do everything,
but I may be underestimating the technical skill required to do so.
For now, I encourage you to try AusFencer for yourself [here](https://github.com/RattlePenguin/ausfencer.git)!
