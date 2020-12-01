---
layout: post
title:      "Learning Piano Chords with JavaScript"
date:       2020-12-01 18:56:07 +0000
permalink:  learning_piano_chords_with_javascript
---


I am about to submit my fourth project for FlatIron's Self Paced Web Development Course. It is surreal to think about how quickly I have progressed through the curriculum, and I am proud of myself for taking it on, and of the projects I have built thus far.

The most recent addition to my portfolio is a single-page application (SPA) that teaches the user different types of piano chords via a keyboard built with CSS and JavaScript. As a musician, I remember the struggle of seeing a chord in sheet music for the first time with utter bewilderment, and not knowing how to play it. These moments could be very discouraging, and I often would not revisit the song nor chord for an extended period of time. Therefore, my hope with this application is that users can avoid the frustration I felt and make the process of learning new chords on piano easier.

## Development

This project required the use of a Rails API as the backend, as well as HTML, CSS, and JavaScript as the frontend. Linking the frontend and backend was surprisingly easy. The more difficult aspects of this project was making UI/UX as intuitive as possible. For example, I wanted the user to be able to click on any note with an applied chord type, and for that note to be played.  Each chord type has its own set of intervals (each note's distance from the start note, measured in half steps). I represented this in my chord class as an attribute, "structure", starting with zero (0) for the root note, and then a number for each note after it (i.e. for Major Triad: 0, 4, 7).

The user does not care about the chord's structure outside of the context of that chord's note names (ie. C Major Triad: C, E, G), therefore they should never interact with the chord structure directly; they select the Major Triad chord type, select a start note, and the program finds the corresponding notes from that structure, and the chord is played. 

However, the note names of that chord arent mapped; since chord types are not tied to one note, it would not make sense to associate the note names directly to the chord. Furthermore, I wanted the user to be able to submit a new chord, and it is not user-friendly to make the user enter a chord's structure upon submission (i.e. "Major Nine structure: 0, 4, 7, 11, 14?? These numbers are supposed to be notes??"). Therefore, the program needed a way to associate a chord's note names to its structure, both upon submission and when playing the chord.


I achieved this by adding an event listener to each key. If the user clicked or pressed the keyboard key (and if Chord Mode is selected), the program:


1. Finds the instance of the JavaScript class "Chord" that is mapped to the chord type dropdown and accesses the selected chord's structure. (selected chord: Major Triad;  chord structure: 0, 4, 7)

2. Finds the start note HTML element (using `event.target`), and selects the note's name from that element's id (start note: C)

3. Maps the chord's structure to the corresponding notes, based on the start note. (0, 4, 7 becomes C, E, G)

4. Finds the key elements of all of those notes

5. Plays the notes (that were previously mapped to the keyboard) together as a chord.


Similarly, the form for submitting a new chord (i.e. C Minor Triad) also has an event listener:


1. User enters chord name (C Minor Triad), and notes (C, Eb, G), then submits the form.

2. The event listener is triggered

3. The submitted notes are changed to a "structure" by converting them to indices of the constant codeNotes (all notes on the keyboard) (0, 3, 7)

4. Each index subtracts the value of the start note; the starting index then becomes zero (0), and the remaining indices maintain their represented value to it ("distance from start note")

5. A new instance of JavaScript Chord class in instantiated and saved, with the desired structure (0, 3, 7)


Note: for this example, codeNotes[0] is already the code for C, so (0, 3, 7) stays the same. However, if the user submitted notes for the D Minor Triad (D, F, A), the indices would be (2, 5, 9). Therefore we add step four, so that the actual structure is found (2, 5, 9 becomes our desired Minor Triad structure: 0, 3, 7).

In this way, the user adds a chord by the chord note names, and not the half-note structure. If a user knows what a C Minor 7 looks like, but not any other Minor 7, they can add it to the database by just entering the notes for the chord they know, without needing the specific half-note structure, and then find out what all other Minor 7 chords look like on the piano.

## Summary
I thoroughly enjoyed building this project! I hope to host this application as soon as possible. I had some stretch goals that I did not accomplish right away, such as an arpeggiate mode, which plays each note of a chord one at a time, instead of all together, as well as support for rootless voicings of chords, but I intend on revisiting it and adding these features at a later date. 

For now, I hope this webapp can help educators, beginning pianists, and songwriters/producers to help enrich their knowledge of piano chords.

If you would like to see my code, check out the [Github Repo](https://github.com/blumenthaler/Piano-Chords).

## Credit
This project was made possible with the help of an awesome repository called [audiosynth by Keith Horwood](https://github.com/keithwhor/audiosynth). I included the contents of this repo in src/audiosynth.js, which allows the browser to generate .wav files. This demonstrates how powerful JavaScript can be, and I was thrilled to find it when I had the idea for this application. Be sure to check it out!



