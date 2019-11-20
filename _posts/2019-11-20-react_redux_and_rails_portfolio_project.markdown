---
layout: post
title:      "React, Redux, and Rails Portfolio Project"
date:       2019-11-20 19:57:19 +0000
permalink:  react_redux_and_rails_portfolio_project
---


My final Flatiron School assignment was to build a React app. I think the idea is a good one and while I’ve met the requirements to pass my assessment the app is far from being finished.

Here are the requirements…

    1. Use the create-react-app generator to start your project.
    2. Your app should have one HTML page to render your react-redux application
    3. There should be 2 container components
    4. There should be 5 stateless components
    5. There should be 3 routes
    6. The Application must make use of react-router and proper RESTful routing
    7. Use Redux middleware to respond to and modify state change
    8. Make use of async actions to send data to and receive data from a server
    9. Your Rails API should handle the data persistence. 
   10.  Your client-side application should handle the display of data with minimal data manipulation
   11. Your application should have some minimal styling

I’m calling the app ‘Divvy’. Users with a Divvy profile can log in and list books (aka items) to their personal ‘shelf’ and set a modest rental price, ideally free. They can then browse other users ‘shelves’ and add books to their cart as rentals.

I split the app into two folders, React and Redux on the client side, and rails as an API.

The Rails API is straightforward. Divvy revolves around three models; Shelf, Item, and Cart. Shelves and Carts have many items and Items belong to Shelves and Carts. Since Items join the models together almost all of the data persistence happens in the Items Controller.

Using React I created matching containers on the client side that each contain child components in order to display data. The containers are connected to actions through a Redux store and the actions make RESTful fetch() requests to the Rails API. The data returned is dispatched using Redux Thunk middleware to corresponding reducers for handling CRUD actions.

The trickiest part of React was separation of concerns and making sure that each component only did what was necessary. Initially I felt that the amount of components was getting out of hand but as the project developed and became more complicated I began to see the patterns and understand the way React projects should be organized.

Redux is a whole other beast that at the get-go seemed unnecessary but now I know I couldn’t get by without it. Top level state organization is critical to even a medium size React app and I plan on this growing exponentially over the next few months as I start my job search.

Follow these links for the [API repo](https://github.com/drkjc/rental-app-api) and [Client repo](http://https://github.com/drkjc/rental-app-client) on [github](https://github.com/drkjc/).

Also, check out the short video walk-through below.

<iframe width="560" height="315" src="https://www.youtube.com/embed/yngR9xrMqN4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





