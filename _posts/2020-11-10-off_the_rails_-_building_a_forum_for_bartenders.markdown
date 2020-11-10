---
layout: post
title:      "Off The Rails - Building a Forum for Bartenders"
date:       2020-11-10 19:41:24 +0000
permalink:  off_the_rails_-_building_a_forum_for_bartenders
---


Rails is a beautiful framework with a ton of built-in "magic" that makes many processes much easier.

It is quite easy, however, for you and your project to quickly jump **off the rails** (how many times has that pun been made, I wonder...) if you do not plan adequately, nor follow convention from the start. This was my exact issue in building my Rails project, resulting in a whopping 156 commits for development alone. 

# Ideation
I wanted to build a forum application for bartenders and cocktail enthusiasts, so that they can post and compare their recipes for various cocktails. One user's Dirty Martini can be much different than another's; someone can add a twist to an old classic cocktail, like adding apple cider to an Old Fashioned. The variations are endless, and I wanted to build an app so that users can share their favorite recipes.

Originally I wanted to have Users, Cocktails, and Recipes as my models. However, as I have since learned about myself, I have a recurring issue with scope creep; I think "Wouldn't it be so cool to vote on each other's cocktails?" and "I want this page to be organized by each cocktail's spirit!".  I am finished with the app's requirements for my bootcamp, and yet I still want to implement comments for each recipe!

As a result of all this unchecked scope creep, I had to stop development multiple times to re-plan my models and database. I **highly recommend against this!** Countless headaches arose from this constant switching, and I was stuck in a development black hole that took days to climb out of.

# Development
Ultimately, I implemented both a voting system for recipes and a Spirit resource, within which the recipes index could be nested. I am happy with the result, but amending the new/edit forms as a result was extremely difficult. 

I learned my lesson with this project. Don't do what I did. Make a plan strictly of what you want to do, and stick to it; only add features if you must.

If you want to see my code, check out [my Github Repo](https://github.com/blumenthaler/Bar-Talk).
