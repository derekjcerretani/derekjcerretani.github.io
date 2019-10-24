---
layout: post
title:      "Rails with Javascript Portfolio Project"
date:       2019-09-13 14:33:16 -0400
permalink:  rails_with_javascript_portfolio_project
---


My fourth Flatiron project assignment was to expand upon my [Rails project, Taut,](https://drkjc.github.io/rails_portfolio_project) using javascript to add dynamic features only available through the JSON API . Instead of building on Taut I decided to start from scratch. A few weeks ago while working at the coffee shop, I was discussing Taut with a friend, explaining the problems I was encoutering, and we came up with a better schema on top of the dishwasher. 
!["Stainless Steel Boarding" as we called it.](https://i.imgur.com/3pWlXkL.jpg?1)
It was too late to apply this schema to Taut but it was perfect for this project. This project, called KIT (keep in touch), is Taut redesigned to work as *almost* a single page application. Only one search functionality requires a refresh. Basically, it's a simple chat app.

There were five requirement for this project. 

1. Must translate JSON responses from your Rails app into JavaScript Model Objects using either ES6 class or constructor syntax. The Model Objects must have at least one method on the prototype. (Formatters work really well for this.)
2. Must render at least one index page (index resource - 'list of things') via JavaScript and an Active Model Serialization JSON Backend.
3. Must render at least one show page (show resource - 'one specific thing') via JavaScript and an Active Model Serialization JSON Backend.
4. Your Rails application must dynamically render on the page at least one serialized 'has_many' relationship through JSON using JavaScript.
5. Must use your Rails application to render a form for creating a resource that is submitted dynamically and displayed through JavaScript and JSON without a page refresh.

**What's different** 

Despite the javascript, which I'll get to later, the basic functionality of the app is the same. A user, once logged in, can send messages to groups they belong to, or direct messages to contacts. The main difference in the models is that instead of users having groups and contacts they simply have rooms. Users have many rooms and rooms have many messages. That's essentially it. 

The login/signup pages look like this. Users can also log in with github.

![Login Page](https://i.imgur.com/ttGsWg2.png)

And after a user logs in they are directed to their home page where most of the action takes place.  

![User 'Dwight' is logged in and his setting are displayed.](https://i.imgur.com/dJq94cg.png)

The user 'Dwight' is logged in and his name is displayed in the top right. The settings link under his name has also been clicked and displays his username and email. This covers the 3rd requirement. When the settings link is clicked the `showSettings();` function inserts the html in the view window.

Under the settings and logout link are the channels. Dwight is part of two channels at the moment, 'conference room' and 'sales'.

Hovering over the link highlights and when it's clicked the index of messages appears for that group. 

![Conference Room messages](https://i.imgur.com/zQvtCV8.png)

 Since channels belongs to multiple users, multiple users can post in the group as shown in the photo. This meets requirements 1, 2, and 4. 

![Message constructor](https://i.imgur.com/LlXsCEx.png) ![showMessages();](https://i.imgur.com/71laFBk.png)

Messages are created and rendered on the front end through a message constructor and the ```
showMessages();``` function. When the prototype method ```renderMessage();``` is called in ```showMessages();```
messages that have been pulled from the database and serialized though the message serializer are turned into javascript objects and are appended to the DOM in the order they were created. Since a room 'has_many' messages this becomes the messages index page for that particular room. The same thing happens with direct messages. When the direct messages link is clicked the user is redirected to the search page.

![Search page](https://i.imgur.com/qzhFyRo.png)

Users can then search for contacts or other channels and join rooms or direct message other users. 

![Direct message between Dwight and Jim](https://i.imgur.com/MrC5W9e.png)

If users would like to create a group from scratch they can click on the '+' symbol next to 'Channels.' This dynamically creates a form where the user can submit a group name and create a new group. This covers the 5th requirement. 

![Create new channels](https://i.imgur.com/8db54p8.png)

If you'd like to see the full source code check out the project on [github.](https://github.com/drkjc/kit). You can also follow me on [twitter.](https://twitter.com/drkjc_)

Below is a video walkthrough of a how a user interacts with KIT.

<iframe width="560" height="315" src="https://www.youtube.com/embed/wUWpgFARa8o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

