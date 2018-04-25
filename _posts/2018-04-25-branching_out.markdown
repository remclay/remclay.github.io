---
layout: post
title:      "Branching out"
date:       2018-04-25 23:34:27 +0000
permalink:  branching_out
---


I had been looking for an opportunity to peer-program but, to date, the timing just hadn’t quite lined up.

A few weeks ago, I reached the “Rails Amusement Park” lab, posted in the #find-a-partner Flatiron School slack, and found a partner!

I had already set up the database and the models when Stephen and I partnered up. So, from there, we divided the remaining work and got right to it.

Overall, it was a great experience! We had several video conferences, sharing screens and ideas, and constantly chatted back and forth on slack.

It was especially interesting when we were debugging. All of the specs were passing, but we wanted to ensure our app functioned well outside of the tests, too. Hearing Stephen’s approach to finding and fixing bugs was really interesting and  informative.

## Resolving conflicts

We each checked out a GitHub branch and completed our respective work. I hadn’t use GitHub branches before but it was a really straightforward process.

Once we’d both finished, we merged our respective branches with branch ‘master’ to do our final checks on one cohesive version. After making some changes, Stephen accidentally forgot he was in branch ‘master’ and pushed up some changes we hadn’t reviewed.

I’ll be honest - I thought this was the worst news ever, but it actually turned out to be a great learning experience because I spent ages absorbed reading about the numerous ways to resolve the conflicts, chatted with some of the instructors, and ultimately simply had to run

```
git pull
```

from my terminal. I received a handy count of the conflicts, and annotations throughout my code highlighting the conflict and presenting both alternatives.

```
<<<<<<< HEAD

the changes I had made locally

=======

the code introduced by my partner’s commit to master

>>>>>>> 4966e61789f7002ab1b1167bb2607bb63aa0f28b
```

All I had to do was resolve each one (by picking the version we wanted to keep and deleting the other) and ```git push``` my version into master. Voila!

I’m told this was my "first of many many many encounters with 'merge conflicts' you'll have in your career”. I’m glad I got a handle on it early! And really glad I had a chance to peer-program.

[https://github.com/remclay/rails-amusement-park-v-000](http://)

