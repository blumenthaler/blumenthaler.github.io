---
layout: post
title:      "React Router - useHistory and useRouteMatch"
date:       2021-01-07 20:23:33 +0000
permalink:  react_router_-_usehistory_and_useroutematch
---


I am reaching ever closer to the end of my final project, utilizing React and Redux. For this project, I am expanding on my Ruby on Rails project, an application for bartenders and cocktail enthusiasts to post and compare their cocktail recipes.

I wanted users to be able to post multiple variations of a given cocktail recipe; for instance, one might craft a Dirty Martini differently with gin than with vodka, or their Rye Old Fashioned may have different proportions than their Bourbon variation of the same cocktail. 

Or, maybe a user just wants to change things up completely, getting creative and experimenting with different flavors. Who knows, maybe a Mountain Dew Margarita is what the world is missing? I doubt I would ever try it, but the user should be able to post their Dew Marg recipe with pride, as well as any other Margarita recipe they choose.

In order to give users this freedom, I had to design the database schema accordingly.
1. a User has many Recipes.
2. a Cocktail has many Recipes.
3. a Recipe belongs to a User and a Cocktail.

## REST

One of the requirements for this project is to utilize RESTful routing conventions. That is to say, if you are looking at a list of all cocktails, then the URL route should read "/cocktails", and if a user were to add a new recipe to a cocktail (id of 2), the route would show "/cocktails/2/recipes/new".

Using RESTful routing is helpful towards improving user experience. When looking at a URL, the user will see a corresponding description of the page they are viewing.

When using Rails, if you visit a route, let's say "/cocktails", Rails will render a new view template, loading a new page, showing all cocktails in the database. RESTful routing is quite intuitive when using Rails in this way.

Unlike Rails, React stores its data on the client side. Therefore, we have to design the routes ourselves. Luckily, the React Router gives us two functions that make this process much easier: `useHistory` and `useRouteMatch`.

`useHistory` gives you access to the history instance, allowing you to delineate routes as you please.
`useRoutematch` returns an object that contains the current route.

I used both of these functions to draw my own custom dynamic routes: 

```
// src/components/comments/CancelCommentButton.js :
import { useHistory, useRouteMatch } from 'react-router-dom'

export const CancelCommentButton = props => {
    const history = useHistory()
    const match = useRouteMatch()
    const handleClick = () => {
        props.triggerCommentForm()
        history.push(`${match.url}/`)
    }
    return (
        <button onClick={() => handleClick()}>Cancel</button>
    )
}
```

Here, I assigned the return values of each function to history and match. The CancelCommentButton is rendered when a user is viewing the new comment form. The url when this form is rendered is changed to '/cocktails/recipes/:recipe_id/comments/new' using a similar flow as seen above. Judging from the url, the user can correctly deduce that they are viewing a form to add a comment to a specific recipe.

When clicked, the CancelCommentButton toggles the comment form (passed as a prop from the CommentsContainer), changing the state of the CommentsContainer, and thus effectively rendering the NewCommentButton instead of the form. 

Since the state is changed, and we are no longer viewing the form, the route should reflect this change. Therefore, it uses the `history` and `match` variables to dynamically change the url back to the base url ('/cocktails/').

This incorporation of `useHistory` and `useRouteMatch` came in very handy for me when designing custom, RESTful routes!









