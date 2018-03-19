---
layout: post
title:      "Adopting Sinatra"
date:       2018-03-19 01:40:04 -0400
permalink:  adopting_sinatra
---


[https://github.com/remclay/adopt-a-dog](http://)

Approaching my first portfolio project, I was slightly apprehensive, having never created something from conception to publication. Approaching my second, I was excited.

Picking a topic was a no-brainer. The Sinatra Portfolio Project overview read “The app should be a custom app that is created to track something important to you.“ I decided to make a web app for tracking dogs available for adoption.

Setting up the models and routes were easy enough, having had plenty of practice in the labs leading up to the project. I decided to make the different breeds objects rather than strings, to practice utilizing has_many :through relationships and extend the app’s functionality. I added Breed and DogBreed classes, created a DogBreeds join table and added the relevant ActiveRecord associations to my models.

Users can easily associate (or disassociate) dogs with certain breeds by checking (or unchecking) boxes, or opt to create a new breed altogether while creating a new dog post or editing an existing one. I ultimately decided not to put any CRUD actions in my BreedsController, as it didn’t make sense to allow a user to edit or delete a breed which other users may have already assigned to other dogs.

## Beware of the bad data

An important lesson I learned about working with databases is not to be fooled by bad data.

```
NoMethodError at /dogs
undefined method `username' for nil:NilClass
```

This error is the perfect example of bad data (which I created!) breaking my app. I used pry, I used tux. Calling ‘user’ on an instance of ‘dog’ definitely returns the user! Prying around in my DogsController confirmed that a dog never gets created without a user. So why is ‘username’ being called on NilClass!? A simple look at all of my current dog objects revealed that one was, in fact, created without a user. How? By me. In a pry session.

I tested out my controller’s logic for creating or assigning breed, depending on whether said breed already exists. I saved the dog I had created, but never assigned it a user. I exited my pry session, happy in the knowledge that my logic was sound and completely unaware of the incomplete dog instance I had inserted into the database.

It was hours later, logged in as a different test user, that I discovered the error. I was so confident that my DogController would never allow a dog to be created without a user, that I looked in several other places before simply checking the data.

Time poorly spent, lesson learned!

## Drop those tables!

Deleting my database tables and starting again proved invaluable. It was a sound reminder to build out logic and views for when there is no data in the database - a situation I otherwise may have overlooked. Creating seed data also saved me a lot of time, and is a simple but convenient feature for future users testing the app.

## Branch out

One feature of GitHub I wish I had utilized is using branches when building out a new feature. By the time I added my additional functionality, I was relatively confident I knew what I was doing and that it was a feature I wanted to keep, so branching did not even cross my mind. However, it’s a habit I want to get into. It’s good practice and will me prepare for working on projects with others. Next time!

## Teaching an old dog new tricks

Now that my models, views and controllers are set up, adding additional content (such as dog location, gender, price, etc.) is relatively quick and easy.

In future, I would like to add further, cleaner validation to my app. The use of the Helpers class methods in both the DogsController and UsersController, for example, is fairly repetitive. 

For this project, I decided to use bootstrap and implement some styling, but nothing too crazy. I plan on delving further and further into HTML and CSS on each project. Plus, I can always come back and improve this one!

I have added some basic logic into the DogsController to ensure a new breed does not get created if one by the same name already exists (if, for example, the user has accidentally opted to create a new breed rather than selecting the relevant checkbox for that breed). In future, this functionality should be extended to cover capitalization, etc, and could potentially be moved into a helper method or into the BreedsController.  In the interim, the Breeds class will still require some periodic manual intervention.

