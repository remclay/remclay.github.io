---
layout: post
title:      "Making jQueries"
date:       2018-06-06 04:31:57 +0000
permalink:  making_jqueries
---

There were some real ups and downs during this project. It wasn’t necessarily that I struggled to get things working, rather that I didn’t do them the most efficient way the first time around.

The upside of this is that I learnt a lot during this project - as much about persevering through times of slow (read no) progress as about ajax and jQuery in general.

A real breakthrough moment was when I was introduced to the possibility of having my serializer provide the return value of a method on my model, in addition to providing serialized model attributes.

Prior to implementing this, I was relying on my ActiveRecord associations and using a different serializer for each associated class.

It looked something like this:

```
class ListItemSerializer < ActiveModel::Serializer
  attributes :id, :list_id, :dish_id
  belongs_to :dish, serializer: ListItemDishSerializer
end
```

```
class ListItemDishSerializer < ActiveModel::Serializer
  attributes :name
  belongs_to :restaurant, serializer: ListItemRestaurantSerializer
end
```

```
class ListItemRestaurantSerializer < ActiveModel::Serializer
  attributes :name, :location
  has_many :dishes
end
```

(NB: I was using specific ListItem serializers over my existing DishSerializer and RestaurantSerializer to avoid grabbing attributes I didn’t need for this particular request).

My RESPONSE, was a monstrosity with the following structure:

```{data: Array(7), included: Array(29), jsonapi: {…}}```

The “data” array contained the seven list_items I expected to see. The “included” array contained the associated dish names, restaurant names and locations, incredibly nested, mixed in with one another, along with some additional data I didn’t want or need.

Now, I could have fixed whatever bugs existed, iterated over the arrays and ‘zipped’ the relevant attributes back together. Sure. But at this point I knew there had to be a better way.

Queue revelation. Define some additional methods on the model, and tell the serializer to serialize the return value of those methods, along with the object’s attributes.

I wrote three new methods in my ListItem class, that simply expose the list_items dish name, restaurant name and restaurant location. 

I deleted the unnecessary ListItemDishSerializer and ListItemRestaurantSerializer and modified my ListItemSerializer as follows:

```
class ListItemSerializer < ActiveModel::Serializer
  attributes :id, :list_id, :dish_id, :dish_name, :restaurant_name, :restaurant_location
end
```

The response was *significantly* more manageable.

``` {data: Array(8), jsonapi: {…}}```

Most importantly, the list_item and it’s associated attributes were grouped together as one object in the “data” array, eliminating the potential for errors associated with ‘stitching’ the response together.

```
attributes: {list-id: 6, dish-id: 6, dish-name: "Mac & Cheese", restaurant-name: "W&C", restaurant-location: "Denver"}
id: "23"
type: "list-items"
```

While I love the red, green, refactor mantra, I’ll be wary of doing a little more research next time, before spending too long implementing a process that feels like there ‘must be a better way’.

[https://github.com/remclay/dish-list](http://)
