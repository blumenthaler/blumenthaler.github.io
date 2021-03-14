---
layout: post
title:      "Playing Music and Building Web Apps are... Similar?"
date:       2021-03-14 22:11:06 +0000
permalink:  playing_music_and_building_web_apps_are_similar
---


I have been studying and performing music to some capacity or another since I was a child. I started learning Upright Bass in grade school, studied classical and jazz Bass as an undergraduate, and performed in various settings, for fun and professionally, throughout. In my music study, I learned various other instruments and skills, from producing music for singer/songwriters to my current study of jazz guitar. 

Needless to say, I have loved listening to, performing, and studying music for as long as I can remember, and it continues to be, as it always has been, a large part of my life.

So the decision to switch my professional pursuit from a career in music to a career in software engineering was no doubt surprising; not only for my peers, family, and friends, who have all known me as a musician for years, but for myself as well.  I never knew much about software, computers, or how they worked, so why did I find it so compelling?

I could not explain it at first, but something about it came very naturally to me. The more I thought about it, the process of creating web apps is amazingly similar to many aspects of being a musician. 

These similarities regularly surface and take me by surprise to this day, well after starting and finishing my bootcamp course at FlatIron School.

So.... what is it? What are these similarities?

## Separation of Concerns

Let's say we are composing a jazz tune, meant for a trio setting: for this example, we will compose for piano, drums, and bass.

We have come up with a melody and chords for the tune, and we need to decide which instrument will play the melody.

Before we decide who plays the melody, we consider the instrumentation; what are the *roles* of each of the instruments? What part will each instrument play?

We can pretty quickly rule out giving the melody to the drummer. Typically, drums do not play pitched notes as most melodies require. Instead, the drummer's role is to maintain the beat/groove, with statically-pitched components, such as drums and cymbals.

This leaves us with the piano and the bass. In this setting, we would (typically, not always!) avoid giving the main melody to the bassist. The bass has such a low range and soft timbre; if we did give the bass the melody, it would not stand out, and could be difficult to hear. Therefore, the bass's role is usually to provide the lowend harmony, allowing for another voice to play the melody on top.

So, for this example, it makes the best sense to give the melody to the pianist; due to its brighter timbre and wide range, the piano is best suited for the melody. 

Instruments in a musical setting all have a specific role, and they must stick to that role in order for the composition or performance to work as intended (aka, to sound good).

Imagine if the piano started playing a bassline at the same time as the bass. Both instruments would step all over each other in the same range, creating an absolute mess. Plus, now *no one is playing the melody!* When instruments take on each other's jobs, the piece quickly becomes disastrous.

###### This situation, believe it or not, also applies when building web applications.

In software engineering, there is a design paradigm known as the Separation of Concerns, or the Single Responsibility Principle. Each piece of code is responsible for one job; each function has one role, and should not interfere with other function's operations or outcomes. 

When building a full-stack application, for example, you may have data sitting in an API on a server, and you want to retrieve that data, process it, and display it to the user. 

All of the code that is used for retrieving data is *only* responsible for retrieving the data. It should not be *concerned* with manipulating that data, nor with showing it to the user. 

When building applications, this principle helps to keep our code organized. This way, if a bug is found in your application, you can easily check each part of the process for where the bug occurs.

Giving each function or method a Single Responsibility in building an application is very similar to assigning roles to your instruments in a given musical composition.

## Pulling from a Learned Vocabulary

In jazz performance, a musician is often required to improvise. This can be difficult for beginners, because they either do not know what to play, or they think they can play whatever they want when improvising, while ignoring the chords or other musical voices happening in the performance.

In order to develop this skill, jazz musicians not only practice and play a ton (and I mean a *ton*); they also learn specific licks (aka phrases of melodic material) to play in specific situations and over certain chord progressions. These licks can originate from anywhere, from classic jazz recordings to melodies in new pop songs; there is [one lick in particular](https://www.youtube.com/watch?v=krDxhnaKD7Q) that seems to permeate decades of recorded music.

Jazz musicians memorize how to play these licks (as well as seemingly limitless scales, arpeggios, intervals, chord voicings, triad pairs....) so that when it is time to solo, they can pull them out and play them effortlessly. 

###### This notion is similar to standard methods for data types in a given coding language.

Let us take a basic Array in JavaScript as an example:

```
let array = [3, 5, 2, 4, 1]
//=> [3, 5, 2, 4, 1]
```

Suppose we are tasked with reordering the contents of this array from the lowest number to the highest.

In JavaScript, we have a built-in method for this data type, `.sort()`, that will give us that exact result:

```
array.sort()
//=> [1, 2, 3, 4, 5]
```

Now with our sorted array, let's say we need to remove it's first element. Luckily for us, there is another built-in method for this exact use case, `.shift()`:

```
array
//=> [1, 2, 3, 4, 5]  // our sorted array

array.shift()
//=> 1  // returns the element that was removed

array
//=> [2, 3, 4, 5]
```

These are built-in functions for every instance of an array in JavaScript. Developers will often rely on these functions *from memory*, chaining them together like our example to manipulate and organize their data as needed.

Building a knowledge of vocabulary to use in specific cases to achieve a specific goal? Sounds an awful lot like improvising a jazz solo to me!

## Conclusion

There are still many similarities between being a musician and creating web applications. The more I think about it, the more similarities arise. It is incredible to me, considering how different the industries and disciplines really are.

If you are a musician, or a creative person of any kind, I can honestly say that, however unlikely that it may seem, software engineering may be a good path for you. 
