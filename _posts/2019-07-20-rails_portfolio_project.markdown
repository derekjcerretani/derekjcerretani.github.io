---
layout: post
title:      "Rails Portfolio Project"
date:       2019-07-20 20:40:30 -0400
permalink:  rails_portfolio_project
---


My third Flatiron project assignment was to build a rails app from scratch. I've been really curious about how Slack operates behind the scene and we use it so often I thought it would be fun to emulate a light version. My app is called, Taut. 
![Imgur](https://i.imgur.com/moSqbZK.png)

The requirements to complete the rails project are as follows.

1.  Use the Ruby on Rails Framework.
2. Models must include at least one has_many, at least on belongst_to, and at least two has_many :through relationships. Include a many-to-many relationship implemented with has_many :through associaties. Join table must include a user-submittable attribute.
3.  Models must include reasonable validations for simple attributes.
4. Must include at least one class level ActiveRecord scope method, and it must be chainable.
5. Must provide standard user authentication, including signup, login, logout, and passwords.
6. Must also allow login from some other service, Facebook, Twitter, etc.
7. Must include and make use of a nested resource with the appropriate RESTful URLs. Must include a nested new route with form that relates to the parents resource. Must include a nested index or show route.
8. Forms should corrently display validation errors. Error messages describing the validation failures must be present within the view.
9. Application must be, within reason, DRY!
10. Do not use scaffolding to build the project.

**Models**

Relationships came first. Using the migration generator I developed similar relationships as in my  [Sinatra](https://medium.com/@derekcerretani/sinatra-portfolio-project-3da11698c794) project between a user and a contact. The difference is that I added groups to this project and let users create group messages. There are six models in total. Below is the relationship between Users, Messages, and Contacts.

![Imgur](https://i.imgur.com/ApQQwOa.png)
![Imgur](https://i.imgur.com/1eKtGTL.png) 
![Imgur](https://i.imgur.com/jQtguXv.png)

The second join table is users_groups which connects the User and Group models. Both users and groups also have many Group Messages.

![Imgur](https://i.imgur.com/J4V2bWx.png)
![Imgur](https://i.imgur.com/Keigx3I.png)
![Imgur](https://i.imgur.com/P9PJh74.png)

_______

Rails 'validate' makes it easy to validate user attributes. The email regex came from [Rails Tutorial](https://www.railstutorial.org/book/modeling_users).

![Imgur](https://i.imgur.com/7xUU8pi.png)

I also added validations to the group model to validate the group name, and the group message model to validate that the group message includes content. 

_______

**Views**

In order for the views to render a conversation between users and contacts I had to use scope methods from the messages model. When a user clicks on a contact the contacts_controller show route finds the contact from params and sets it equal to the instance variable @contact. The route moves on to the #contact_conversation method to find the appropriate messages, using @contact as the argument.

```
def contact_conversation(contact)
    messages = []
    messages << Message.sent_messages(@user, contact)
    messages << Message.received_messages(contact, @user)
    @convo = messages.flatten.sort_by { |m| m.created_at}.uniq { |m| m.content }.drop(1)
    @convo
  end
```

#sent_messages and #received_messages are scope methods defined in the messages model.

```
scope :sent_messages, ->(user, contact) { where(user_id: user.id, contact_id: contact.id) } 
```

```
scope :received_messages, ->(contact, user) { where(user_id: contact.id, contact_id: user.id) }
```

The @convo instance variable gets displayed in the contact view and looks like this. The conversation is happening in the right div. Al is signed in and having a conversation with Dan.

![Imgur](https://i.imgur.com/T5wQPqD.png)

Only the conversation views between users and contacts or amongst those in groups are yielded to the application layout, and change when a contact or group link is clicked. The header and everything on the left side where groups/contacts can be displayed or created are rendered through the application layout at all times so the user always has access.

The login/signup views are simple and show input fields and the app logo, as well as a link to login through facebook.

![Imgur](https://i.imgur.com/LewQ1PI.png)
![Imgur](https://i.imgur.com/hdYsY7x.png)

When a user signs up for the first time they are directed to this page and asked to sign in to their group. This first group dictates which contacts you can access. Everyone who's first group is the same has access to each other. Much like Slack's "Sign In To Your Workspace" page. 

![Imgur](https://i.imgur.com/ZYxOH10.png)
![Imgur](https://i.imgur.com/FXqGEja.png)

Of course all views display error messages when user information is invalid. For example if trying to sign up with an email that's already registered...

![Imgur](https://i.imgur.com/EAWmwMn.png)

______

**Controllers**

There are seven controllers. The controllers implement RESTful routes and more importantly nested routes. Routes are nested when creating messages between users and contacts, and when creating group messages. Because of how views are displayed the nested routes aren't shown in the url, with the exception of the 'edit' message function. Instead nested data from the contact form, in the contact view, is carried to the message controller, a new message is created and the user is redirected back to the contact view where the message is displayed. 

New message form in the view, below.
![Imgur](https://i.imgur.com/z79auwf.png) 

New message form under the hood, below.
![Imgur](https://i.imgur.com/5Ln1iBg.png)

The controllers contain specifically designed route methods that can be explored on [github](https://github.com/derekjcerretani/taut).

_______

This project was really fun to build. I learned a lot and still feel I've only scratched the surface of what is capable in Rails. I also stepped up my CSS game. Implementing the side by side views was difficult and challenged me to be creative to display user information. So much respect for CSS wizards out there. This project was built entirely in rails with CSS and HTML. Next section I learn Javascript and implement it into this project so smooth out transitions and make this thing look even better! 

Check out this project on [github](https://github.com/derekjcerretani/taut).
Follow me on [Twitter](https://twitter.com/rekcera).

Below is a video walkthrough of how a user interacts with Taut.


<iframe width="560" height="315" src="https://www.youtube.com/embed/4voZaO2StFA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>









