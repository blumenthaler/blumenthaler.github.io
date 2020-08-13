---
layout: post
title:      "Investment Definitions - Building an Efficient Scraper"
date:       2020-08-13 20:51:03 +0000
permalink:  investment_definitions_-_building_an_efficient_scraper
---


I had been wracking my brain trying to come up with an idea for my first portfolio project. I wanted the project to be something that I personally would use regularly. I have an active interest in personal finance and economics, and I often come across terms that are either misleading in their name, or whose definitions are generally convoluted. Whenever I come across these terms, I typically will search it on the [Dictionary of Financial Terms ](http://investopedia.com/financial-term-dictionary-4769738)on Investopedia. Investopedia's site is great for thorough explanations of a given term, but as an introduction to a topic, the given information can be overwhelming. Furthermore, the site sometimes loads longer than desired, and is often full of unwanted ads.

Therefore, I decided to create a CLI application that scrapes Investopedia's Dictionary of Financial Terms and outputs a term's concise definition, as well as key takeaways for that topic, upon request.


Scraper

The biggest issue I had with building this application was building an efficient Scraper class. There are 600+ terms on Investopedia's Dictionary page, so scraping it had to be as efficient as possible. Otherwise, the program would run very slowly. Another complication was the fact that I could not obtain each topic's definition, nor key takeaways, without opening that topic's url first. Therefore, I had to implement logic that efficiently scrapes a topic's webpage.


Building

I originally wanted to show all topics at once, but I knew that scraping 600+ topics off of one page would seriously slow down my program. Therefore, to reduce the amount of work the program needed to do, I designed it to only scrape a list of topics organized by first letter. I changed the logic of the CLI by prompting the user: "Please enter the first letter (A-Z) of the topic you wish to learn more about (or # for number):", and upon request, the CLI would show the user that list of topics. 

In order to achieve this, I built the #get_page method for the Scraper, and then another method, #scrape_topic_page_from_input, which takes in the user's input as an argument, and finds the list of topics that start with that letter (or those that start with a number, in the case that input == "#"). Then a third method, #make_topics, creates instances of the Topic class, using the scraped data to assign the correct values for each topic's name and URL attributes.

Having the list of topics scraped, I had to address the second problem: scraping a specific topic's page for it's definition and key takeaways. I originally created the method to scrape all listed topic pages for their definitions and takeaways, which would be attributed to each topic instance. Then the user selects the complete topic, one at a time, to see the definition and takeaways. This process also slowed my program down greatly, and ultimately did not make much sense. Why would the program scrape all the pages at once if the user only sees one topic's details at a time?

So, to solve this, I decided to create a method, #scrape_details, that scrapes a topic's specific URL upon request. This will allow the program to find and assign only the selected topic's definition and key takeaway attributes, which greatly sped up the program's execution.


Lessons Learned

Aside from building a program from scratch that includes good Object Orientation and multiple relating classes, the most meaningful lesson I learned was that of increasing efficiency for the sake of running the program smoothly. If a program does not need nor utilize extra functionality that is coded, that code is extraneous, and most likely will slow the program down. When building programs in the future, I will, starting from the beginning, figure out exactly what I want the program to do, and then to build it as such, being careful not to add extraneous code.

If you would like to see the code, visit [my Github Repo](http://github.com/blumenthaler/invest).



