---
layout: post
title:      "Sinatra Portfolio Project"
date:       2019-05-15 22:41:28 +0000
permalink:  sinatra_portfolio_project
---


My second Flatiron project assignment was to build a Sinatra MVC web app, using ActiveRecord. I had worked through MVC patterns multiple times before the start of this project so the initial setup was simple, using the Corneal gem, and I used my extra time to experiment and arrange the user interface. Based on the ten requirements for completion I thought a simple email app would work and it interested me how users share email data. The requirements included:

1. Build an MVC Sinatra app
2. Use ActiveRecord with Sinatra
3. Use multiple models
4. Use at least one has_many relationship on a User model and one belongs_to relationship on another model.
5. Users must be able to sign up, sign in, and log out.
6. Validate Uniqueness of user login attribute (username or email).
7. Once logged in, a user must have the ability to create, read, update and destroy the resource that belong_to the user.
8. Users can edit and delete only their own resources.
9. Validate user input so bad data cannot be persisted to the database.
10. BONUS: Display validation failures to the user with error messages. 

	I chose an email app because I was determined to use a join table in my project to get a better grasp on how they work in ActiveRecord, and I knew that somehow users share email data.  It took some experimenting but eventually became obvious that emails belong_to multiple users, so emails would be my join table. I decided a user (sender) should be able to sign in, create an email and send it to another user (receiver), who I called the contact. A user can edit, or delete any email they create but can't alter any email received. My file structure can be seen below.

![](https://i.imgur.com/RM8FDHj.png)


Models:

There are three models, a user, and contact, and an email. 

A user has a username, an email address, and a password. A user has many emails and has many contacts through emails. I was able to validate the uniqueness of the user's email address by adding the ActiveRecord validate prompt to the user class.

A contact has an address and a user id. A contact has many emails and many users through emails.

An email has content. An email belongs to a user and belongs to a contact.

Views:

Following standard email app logic, I decided that when a user logs in successfully they would be directed to their inbox. From there they could read any messages they received by clicking on them or create a new email and contact. Once a user has clicked on a message or a contact they are directed to a show page that lets them see the full conversation between them and their contact. From there they can edit or delete sent messages. If at any point the user tried to submit a form that was blank they would receive an error message and have to try again. 


![](https://i.imgur.com/TFT00B5.png)

Controllers: 

There are three controllers. The User and Email controllers inherit from the Application controller. I designed the controllers to implement RESTful routes so that the logic was easy to follow.

After implementing the logic I used the layout to style the login pages and created another layout, mailbox.erb, to style the user's mailbox. Most of the css is laid out using Flexbox. I grabbed images for the header and background from Pixabay. Prickly Pear Cacti because I'm currently located in Tucson.

![](https://i.imgur.com/KyNYLZS.png)

This was a fun project and, in my mind, far from over. As of now, the user cannot remove emails from their inbox so I hope to implement that in the near future. Also, emails can only be associated with a single sender and single receiver and I'd like to make it so you can send messages to multiple contacts at once. 

I'm feeling great about using Sinatra to design simple web apps and am excited to move on to our next chapter, Rails! 

You can see the rest of my code [here.](http://github.com/derekjcerretani/lite-mail)
