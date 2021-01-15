---
layout: post
title:      "Using Emojis in HTML!"
date:       2021-01-15 04:30:11 +0000
permalink:  using_emojis_in_html
---


I have been searching for different images to use as an icon for my React/Redux project - a forum for bartenders to share their favorite cocktail recipes - and I was having trouble finding one that fit.

Then I had a thought: 

**"The martini glass emoji 🍸 would be perfect for this... I wish I could use emojis in my webapp."**

After some digging, I found out it is actually very easy to do this!


## HTML

In order to use emojis in an HTML file, we first need to make sure that the character set that is used in the file is set to UTF-8. Luckily for us, this is the default setting; we can check in the `meta` tag, found in the `head` section:

`<meta charset="UTF-8">`

Next, we need to find the correct decimal (dec) or hexadecimal (hex) reference for our corresponding emoji.

W3Schools offers a full list of supported emojis and their decimal references [here](https://www.w3schools.com/charsets/ref_emoji.asp).

Unfortunately, the list at W3S is quite large, and therefore difficult to search for your needed emoji. I found this [master list](https://gist.github.com/oliveratgithub/0bf11a9aff0d6da7b46f1490f86a71eb/) much easier to search. In this case, we want to display the cocktail glass, so I just typed `cmd + F` and searched for 'cocktail'. 

In the given JSON object, I found the `html` key, with a corresponding value of `&#127864;`.

When I input this value into an HTML file, the cocktail emoji is rendered! 

```
 <div className='welcome'>
          <h1 className='welcome-child'>&#127864; Welcome to Bar Talk! &#127864;</h1>
          <br />
					... 
</div>
```

The above code renders a heading with two martini glasses on either side:

### 🍸 Welcome to Bar Talk! 🍸

Cheers, and Happy Coding! 🥂

If you want to browse my code, check out the [Github Repo](https://github.com/blumenthaler/Bar-Talk-Frontend).





