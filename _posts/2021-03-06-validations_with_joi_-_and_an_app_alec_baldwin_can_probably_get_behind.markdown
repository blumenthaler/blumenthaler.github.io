---
layout: post
title:      "Validations with Joi - And an App Alec Baldwin Can (Probably) Get Behind"
date:       2021-03-06 16:01:45 -0500
permalink:  validations_with_joi_-_and_an_app_alec_baldwin_can_probably_get_behind
---


I watched a video rant by Alec Baldwin on Instagram the other day, discussing how he deactivated his Twitter account.

He said he was largely disappointed by the regular toxicity in the responses he received from his unincendiary tweets. He also said that his primary purpose for his Twitter feed was using it as a news aggregate, following various news sources that he liked. Since he decided to deactivate his account, he was looking for a new place to serve as his one-stop place for daily news and editorials.

I cannot speak for Alec in regards to unwanted attention; my tweets do not receive nearly as much attention as his, nor, therefore, as much hate.

What I can relate to, however, is the lack of a proper news aggregate. I am constantly searching for news sources that I like, and I do not have a way of organizing them or viewing their articles at once.

Similar ideas to this are too often cluttered with ads or other noise (Twitter), or they do not allow you to actually aggregate the sources you want, showing you news sources that you do not want to see (Apple News, Filpboard).


### "Imagine" I thought, "ONE place to view the news you ACTUALLY want to see!"


Although I am not a world-famous film star, I am a developer, which means I can build this dream app!


## Scraping with Node.js

For this project, I started to build a RESTful API with Node and Express. I knew that I also needed to build a web scraper, so I can dynamically update the application with the latest news from my favorite (free) sources.

I began with my favorite news source, Reuters. Currently, I scrape the top story from Reuters's homepage, and get the title and content for that story, and add it to the API.

I do not currently have a database in place, but I either plan to use the tried-and-true Postgres, or dive in to brand new territory with MongoDB. I am leaning towards utilizing Mongo, because then when I build the React-based frontend, I will officially have experience building a full-stack application in the MERN stack.

## Validation with Joi

After creating basic GET routes and testing them with seed data, I knew I had to build the POST route for my API. 

POST routes can be tricky, because they require *validation*; we should never just trust that our client is sending the correct data. Otherwise the application can easily break.

To start with data validation, I created the basic POST route and manually checked the request object for the required parameters (title and content): 

```
app.post('/api/articles', (req, res) => {
    if (!req.body.title || !req.body.content) {
        res.status(400).send('Articles must have a title and content.')
        return;
    }
    else {
        const article = {
            id: articles.length + 1,
            title: req.body.title,
            content: req.body.content
        }
        articles.push(article)
        res.send(article)
    }
})
```

Note: since I have not yet implemented a DBMS, I am simply adding the article to a global variable names `articles`, and assigning an article's id based on that array's length.

Here, I am manually checking to see if the request object contains a title value and a content value. This works just fine for this simple case, but if I am in a situation where I need to validate articles in different requests, then I will be repeating myself often to check validations over and over again. Furthermore, if the article data needs to be more complex as I add features, I will have to modify all of these validation instances.

Here is where [Joi ](https://www.npmjs.com/package/joi) comes in.

Joi is a lovely npm package that allows you to serialize your data validations. This became very helpful when creating POST routes, as you can see in the refactoring below:

Note: for this implementation, I used an older Joi version, 13.1.0


```
// requiring the package at the top of the file:
const Joi = require('joi')

....

app.post('/api/articles', (req, res) => {
    
		// delineate data's schema:
    const schema = {
        title: Joi.string().min(4).required(),
        content: Joi.string().min(4).required()
    }
    const result = Joi.validate(req.body, schema)
   
	  // check for an error
    if (result.error) {
        res.status(400).send(result.error)
        return;
    }t
    else {
        const article = {
            id: articles.length + 1,
            title: req.body.title,
            content: req.body.content
        }
        articles.push(article)
        res.send(article)
    }
})
```

Here, inside the POST request, I using Joi to create a schema for the news articles: each article has a string called 'title', and a string called 'content'. Then, I call `validate(req.body, schema)` on the Joi class object to check over the request object's `body` property against that schema.

If there is a title string value and a content string value, both with a minimum of 4 characters, then the request continues. If not, an `error` object is created, and we send it to the client: 

```
{
    "isJoi": true,
    "name": "ValidationError",
    "details": [
        {
            "message": "\"title\" is not allowed to be empty",
            "path": [
                "title"
            ],
            "type": "any.empty",
            "context": {
                "key": "title",
                "label": "title"
            }
        }
    ],
    "_object": {
        "title": "",
        "content": "blah blah blah"
    }
}
```

Pretty cool! However, we still have a problem: our validation is still inside ONLY this post request. If we need to validate our data in another route, we will surely have to repeat ourselves. 

To solve this, we extrapolate the logic to a function: 

```
const validateArticle = article => {
    const schema = {
        title: Joi.string().min(4).required(),
        content: Joi.string().min(4).required()
    }
    return Joi.validate(article, schema)
} 
```

Then we can call this function in our request:

```
app.post('/api/articles', (req, res) => {
    
    // new function call:
		const result = validateArticle(req.body)
		
    if (result.error) {
        res.status(400).send(result.error)
        return;
    }
    else {
        const article = {
            // placeholder for articles
            id: articles.length + 1,
            title: req.body.title,
            content: req.body.content
        }
        articles.push(article)
        res.send(article)
    }
})
```

Passing the request's body object to the function receives the same effect! Nice!

We can still do some refactoring here to make our code a bit cleaner. For one thing, when there is an error, we can destructure it from the result variable like so: 

```
....
		const result = validateArticle(req.body)
		const {error} = result
		
    if (error) {
        res.status(400).send(error)
        return;
    }
    else {
....
```

Also, when there is an error, we are really only concerned with the error message: 

```
.... 
 "details": [
        {
            "message": "\"title\" is not allowed to be empty",
						....
				}
 ]
....
```

Instead of sending the entire error object, we can simply send just this message: 

```
    if (error) {
        res.status(400).send(error.details[0].message)
        return;
    }
```

The final, DRY result:

```
app.post('/api/articles', (req, res) => {
    const result = validateArticle(req.body)
    const {error} = result
    if (error) {
        res.status(400).send(error.details[0].message)
        return;
    }
    else {
        const article = {
            id: articles.length + 1,
            title: req.body.title,
            content: req.body.content
        }
        articles.push(article)
        res.send(article)
    } 
})

const validateArticle = article => {
    const schema = {
        title: Joi.string().min(4).required(),
        content: Joi.string().min(4).required()
    }
    return Joi.validate(article, schema)
} 
```

Nice! Very DRY, modular code here. You love to see it!

With this validation in place, I am well on my way to adding multiple articles and news sources to my application. 

Hopefully Alec can rest easy knowing that there's a reliable news aggregate in the works!

Until next time: 

[Always Be Coding!](https://media.giphy.com/media/3ov9k3Pq54ky2rNyp2/giphy.gif)








