---
layout: post
title:      "Take-a-hike"
date:       2018-08-16 16:31:12 +0000
permalink:  take-a-hike
---


Take-a-hike is a basic CRUD web application for finding, adding, editing, deleting hiking trails. The app consists of a Rails API and a React/Redux front-end. Users can browse hikes, search via name or location and filter via difficulty level. Hikes can be created and edited without user sign in.

Deciding how to structure and set up this app was incredibly interesting. All of the skills I had learnt in isolation were finally coming together to create a stand alone web app. Exciting stuff!

For this project, I decided to focus on fully understanding React and Redux - unidirectional data flow, updating state, component structuring - and how the front and back ends of my app interacted.

I read and re-read the React and Redux documentation, watched several of Dan Abramov’s awesome Egghead Redux tutorials, played around with different component structures and component declarations. By the time I wrote my last component, I felt a proper understanding of mapStateToProps and mapDispatchToProps.

Switching my focus to the above meant that (for once) I cut out a lot of additional functionality I had initially planned to build out. I justified this to myself with reminders that I had built these things out in my previous Rails/jQuery app.

For example, I wrote custom user authentication and authorization for Dish-list so I left that out (for now). I explored Active Record in all it’s glory, implementing numerous relationships and custom validation, in Dish-list. So my initial (very complex) schema also went out the window.

As always, I have a ‘todo’ list of functionality I’d like to add in the future. But, for now, I’m leaving it as is. Another small step toward toning down my litigation lawyer OCD.

I thoroughly enjoyed building this app. Working with React was a joy, and the satisfaction of building and utilizing my own Rails API was second to none.

Check it out [here](https://github.com/remclay/take-a-hike).
