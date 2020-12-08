---
layout: post
title:      "How I Learned (the Hard Way) to Avoid the Simplest Mistakes"
date:       2020-12-08 14:36:36 +0000
permalink:  how_i_learned_the_hard_way_to_avoid_the_simplest_mistakes
---

I am approaching the end of the curriculum for the Self-Paced Online Web Development course. I am truly amazed at what I have been able to accomplish in the past six months. I have come from almost zero tech training/knowledge, to being qualified as a Full Stack Web Developer. (I do not think I will grow tired of saying that anytime soon!)

Throughout the curriculum, I have celebrated my success and perserverence. Along with the triumphs, there are also shortcomings, of course. Even as I progress through the final module, I catch myself making mistakes that seem so amateur, and it is difficult to not be hard on myself for making them.

In a recent lab, I was learning about passing props from a parent component to a child in React. In theory, and as I understood it, the concept was fairly simple; there are properties that a parent gives to the child, and the child component has access to those props in its own functions.

Despite my understanding, the learn tests simply refused to pass. The prop I passed down and called in the child was apparently "undefined".

"Well," I thought, "this could be a syntax error." I was (and still am) relatively new to React, and I knew that becoming used to the syntax was going to be a hurdle, as it is with any new language or framework.

I checked back and forth between past lessons and documentation, making sure I had the correct syntax for passing a function as a prop.

To my frustration, I already had the correct syntax, yet my tests were still failing. What could possibly be the issue?

I hopped into Ask a Question feature to connect with someone to help me solve this. I was clearly missing something, and I did not know if it was due to my lack of understanding of React at this point, or something potentially wrong with the test suite.

We looked at the code for quite some time. At one point, the technical coach asked me to walk through the code from start point to end point, so we could both figure it out together.

"Okay", I said, "Here, in the parent component, I declare the function (**onAdoptPet**), and then I pass it to the child as a prop here-"

....
....
....
....

## **It was a typo.**

I named the prop **"*onAdpotPet*"**.

I could not believe that I would make such a simple mistake after completing multiple difficult portfolio projects in the curriculum.

The coach then gave me the best advice that I now always adhere to, in order to avoid lost time and frustration, which I will now bestow to you:

## *Always copy and paste function names wherever you use them!*
