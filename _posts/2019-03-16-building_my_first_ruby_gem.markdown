---
layout: post
title:      "Building My First Ruby Gem"
date:       2019-03-16 16:36:00 -0400
permalink:  building_my_first_ruby_gem
---


I built my first CLI gem!

The requirements to pass the project include: provide a CLI, provide access to data from a web page, and the data provided must go one level deep. Easy right?

I built a gem called TopFilms. It scrapes data from IMDB and lists the top 100 films based on user rating. You can then explore each film a little deeper to see the year it was made, the rating, description, director, etc. 

I've boiled my experience down to three major points.

1.  Bundler
1.  Scraping
1.  CLI Controller and Method Interaction

-----------------

## **1.  Bundler**

Thank you [Bundler](https://bundler.io/v1.16/guides/creating_gem.html) for making setting up a directory structure so easy. 
One line in terminal...

`bundle gem "gem-name"`

and you have an almost complete directory structure, save for your lib files.  
After that, it's only a matter of setting up the proper requirements, which I'll admit took longer than planned to figure out, filling in some blanks, and adding dependencies. You can get to actual coding pretty quickly.


![TopFilms Directory Structure](https://i.imgur.com/TtkEQYh.png)


## **2. Scraping**


My lib folder contained four classes, one of which 'version' was provided for me by bundler. The other three, CLI, film, and scraper contains the code that builds the project and makes it interactive. The film class was simple enough. It initialized with all the things that make it a film which you can see in the picture below.

![Film Class Initialize Method](https://i.imgur.com/BG9qS3Y.png)

The last line in initialize pushes the instance of each film into the empty 'all' array we use later to access data from the CLI controller. The controller I'll get to later. First I want to talk about my Scraper class. 

The Scraper class uses Nokogiri, another Ruby gem, to turn the HTML of a website into a nested array of data making it easier to iterate through and pull from. I say *easier* because there is still a lot of trial and error that goes into compiling the correct data. On a website like IMDB where data is presented in a familiar pattern throughout the webpage, scraping is simpler. For instance, all film runtimes in IMDB's HTML were in <span class="runtime">. Using the CSS selector "span.runtime" pulled the correct data. 

![](https://i.imgur.com/NOcRLTC.png)

But not all of the film data was presented equally. Most of the films had a "certificate" class that showed advisory data; "R", "PG", etc. But a few films had no "certificate" class which made collecting data trickier. I spent many hours playing around. In the end, my code works but is more convoluted than I'd like.

!["Not very pretty, but it works!"](https://i.imgur.com/GBuOk3I.png)

I'm feeling great about using Nokogiri after building this!

## **3. CLI Controller and Method Interaction**

Building the CLI controller was my favorite part of the project. It put me in the head of the user and forced me to consider how to interact with the gem. Designing the display of film data was a good lesson in logic and creativity, especially when it came to the flow of the program. I don't have a screenshot saved, but initially, all the controller interaction was contained within one or two methods. This meant the program would work fine if you followed the instruction to a T. I let my family play around and they broke it *immediately*. They mistyped or tried to force logic that didn't exist. It was a humbling lesson in UX. 

In order to fix this, I had to abstract my two methods into multiple methods that would call upon one another and give the user more options while simultaneously informing them of errors and forcing them to choose from the limited options presented. The way in which methods interact in Ruby makes for incredibly flexible and powerful programs. This CLI controller solidified my comprehension of method interaction and code organization.

### Conclusion

On a scale of usefulness, I feel the gem barely qualifies, but I assume that a penchant for writing truly useful gems comes after many years of programming and recognizing patterns when debugging or designing. What's more important to me in the current moment is understanding how code can fit together, how objects and methods interact, how to sift through data, and the basics of procedural Ruby. If the CLI project is to be a distillation of everything I've learned since day one, I'm feeling confident in my understanding.

To install TopFilms and review the source code check out [Github](https://github.com/derekjcerretani/top_films)!

<iframe width="560" height="315" src="https://www.youtube.com/embed/bGko9ODBS6s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>







