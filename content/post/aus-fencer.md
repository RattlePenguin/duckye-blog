+++
draft = true
+++

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
fence without electrics.

The bare minimum most would accept is a set of reels (wiring) and a light up box.
This at least guarantees that when a touch is made, a light signal appears.
Unfortunately this is still very expensive, and you still must keep track of
score on your own.

Fencing without electrics is a last resort, and a good referee makes it quite
possible to evaluate accurately.
Referees usually use their fingers, paper, or edit a text file on their phone
to keep score.
As you might probably guess, fingers are barely reliable.
A text file is definitely a step up, but not without room for improvement!

In my club, the idea of a phone app that helps keep score has
floated around for ages.
This would allow referees to focus less on their fingers and more on the game.
An equally demanded tool is one that allows the organisation of in-house competitions.
FencingTimeLive[]() is the standard for hosting fencing tournaments,

## Problems

| Problem | Solution |
| -------------- | --------------- |
| If referees use their hands to keep score, they may lose track. | Provide an accessible UI on their phone to store bout information. |
| Bouts in practice sessions don't get stored due to inconvenience, which could be useful to spot weaknesses and progress. | Automatically store finished bouts into a database, aggregating stats to give fencers a profile. |

## Tech Overview and Stack

I decided to use C++ for our backend services, not because it was the most suitable
but because I am currently trying to master it.
If I didn't want to bother with linking external dependencies and libraries,
then C#, Java or Go may be more worthwhile.
Many high performance web server stacks still use C++ frameworks, but we
likely won't observe the benefits of such speed.
C++ might pay off in the future if I decide to extend this project into the
low-latency fencing equipment hardware.

For the server side, I used Sqlite3[]() and SqliteCpp[](),
Crow[](), and nlohmann/json[]()
to manage the database, HTTP server and API.
