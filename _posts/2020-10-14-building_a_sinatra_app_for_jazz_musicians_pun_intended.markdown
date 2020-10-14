---
layout: post
title:      "Building a Sinatra App for Jazz Musicians (Pun Intended)"
date:       2020-10-14 20:18:33 +0000
permalink:  building_a_sinatra_app_for_jazz_musicians_pun_intended
---


I am committed to creating useful applications for myself and users in my community.  I studied classical and jazz music in college, and music remains as one of my great passions in life. Though I have been enrolled in a tech bootcamp, which is not directly related to music, I have continued to pursue music practice. Every week, I pick a jazz standard that I have not mastered, and I practice it so that I can play/sing the melody, play the chords, and create bass lines, all from memory. It gives me a chance to relax, taking a break from learning code, while also continuing my pursuit of musical study.

I know many jazz musicians need a way to organize their study of jazz standards. There are so many tunes in the idiom that logging and remembering which tunes you have practiced can be difficult. As I practice a new standard every week, I have one paper that I use to log all of my practice information for each tune. This will quickly get out of hand as I continue to learn standards. Therefore, I wanted to build a web app with the Sinatra Ruby gem that will help to organize all of the standards that I and other jazz musicians have learned and continue to learn.

# Outline

This app allows users to sign up and log in, as well as the ability to create their log of jazz standards. When a user creates a new standard for their list, they fill out the title, composer, recording, performer, tempo practised, the user's levels of knowledge of the tune (i.e. melody, lyrics, chords, etc.), and the date by which the tune is memorized. After having saved the standard in their practice log, the user can go back and edit any aspect of the tune. For example, if a user only learns the melody at first, but comes back and learns the the tune's chords by memory, they can add that to the standard at a later date. A user can also delete a tune in their log for a given reason. Once finished reviewing their log of standards, the user can log out, and upon logging back in, their list of jazz standards will be saved.

# Associations

This program utilizes Object Relational Mapping (ORM) with the Ruby gem ActiveRecord. This gem allows for associations between the two model types in this instance; a User *has many* Jazz Standards, while a Jazz Standard *belongs to* a User. This becomes especially helpful in certain use cases. For example, let us assume that there are two users, who both want to practice the same Jazz Standard. The first user, however, wants to log different information about that standard (a favorite recording, a practised tempo, different levels of knowledge) than the second user. 

Remember that a Jazz Standard *belongs to* a User. Because of our ActiveRecord associations, two users have independent lists containing the same jazz standard, even if they enter different, user-specific information about it. This way, users can practice the same tune at whatever tempo they want, as well as enter the name of their favorite recording/performer of the tune, or any other given information about it. 

# Community

I have been on far too many jazz gigs where either myself or a colleague will call a tune that at least someone in the group does not know. There is nothing more frustrating than calling many tunes in a row, and because someone does not know it, the group has to sit and waste time trying to think of something everyone can play.

In an effort to combat this, I started to build a community feature of this application, where a user can see other users' lists of standards. Users can compare different aspects of different tunes, and if they practice the same standard, they can meet up at a gig or a jam session and call the tune, knowing the other player has practiced it.

If enough users were to sign up and use the app, I would love to expand the community functionality. Jazz musicians in different cities, areas, and communities could stay organized in sub-groups on the site, so that more musicians can be prepared when they play together. If someone had a jazz gig and needed a trumpet player to play on it, for instance, they could look at the group in their area, see who plays trumpet, and see who has practiced the standards they want to play. Educators at schools or teaching privately could use a sub-group to keep their students' practice logs organized.


I had a ton of fun building this application. I wanted to build something that I would regularly use, and I hope musicians and music educators will be able to put it to good use!

If you would like to browse the code, check out [my Github repo.](https://github.com/blumenthaler/jazz-practice-log)






