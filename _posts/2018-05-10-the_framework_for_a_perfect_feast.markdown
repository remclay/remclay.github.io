---
layout: post
title:      "The framework for a perfect feast!"
date:       2018-05-11 01:51:13 +0000
permalink:  the_framework_for_a_perfect_feast
---


## Appetizer

In keeping with the theme of building portfolio-projects involving things I love…Dish-List is a Ruby on Rails app to track your ‘must-eat’ restaurant dishes .

Users can view most-popular dishes and the restaurants where you can find them, view all dishes or restaurants or view a specific user’s Dish-List. It’s easy to create new dishes and restaurants, add or remove dishes from your list, or mark them as tasted.

## Entree

It didn’t take long to construct the database, set up the relationships, map out the basic routes and views and have the app generally up and running. It was satisfying to see how quickly it came together using Rails over Sinatra.

I set up nested routes, created a ‘complex form’ utilizing ActiveRecord class method ```accepts_nested_attributes_for```, implemented an ActiveRecord scope method ```most_popular``` within the Dish class. I feel as though I am significantly more across the Ruby on Rails documentation.

I implemented validations for both the User and Dish models. I also created custom validators for the Dish model, ```unique_dish``` and ```unique_restaurant```, to prevent an existing dish or restaurant from being created a second time.

## Room for Dessert..?

I experienced a similar difficulty in regards to refactoring. I still feel as though my views could contain less logic, and the app would benefit if I create and render more partials. I think my controllers could be thinner and a few of my methods contain too many nested if/else statements.

Numerous intelligent people advised me to stop working on the app (for now) and continue with the curriculum, reminding me that I can always come back to it in future. Ultimately, that’s what I did.

## Wish-List

I created a Dish-List ‘Wish-List’ (todo.md) where I outline the features and functionality I would like to build out in the future. Jotting down all of these ideas made it easier to leave things as they are, for now.

One big change I want to implement in future is reducing the number database queries, most probably using action caching (expiring on add or create).

This project was a fantastic learning experience. It cemented my understanding of OO Ruby and made me realize how far I’ve come in the past few months.

GitHub repo: https://github.com/remclay/dish-list
Walkthrough: https://drive.google.com/drive/folders/12TcvkwPXB5i7dzP3pCWrGpsd8j4sjgyP


