---
layout: post
title:      "Like a fine wine"
date:       2018-01-25 18:14:06 +0000
permalink:  like_a_fine_wine
---


**The lead up..**

I really did not know what to expect approaching my first CLI Project. There had been a few points throughout the curriculum where I had *thought* I understood everything well, only to come to the final lab in the section and realise that I simply didn’t have the grasp I thought I did. I would go back, review, and attack it again.

Before starting the project, I felt I had a pretty good grasp on OO Ruby, but I was curious (and a little apprehensive) as to whether I would have to go back and review, before moving forward.

Firstly, I should note how incredibly lucky I was, in that the Flatiron NYC Weekend Warrior Workshop relating to OO Ruby and this CLI project took place almost exactly as I was ready to begin my project. It was an incredibly motivating weekend intensive that provided a perfect review of OO Ruby.

**The initial harvest..**

I began my project and, to my surprise and absolute utter joy, I knew what I was doing. I googled a lot, and went back to check on one or two things earlier in the curriculum, but by and large my objects and their relationships came to life from knowledge that I had actually retained. Exhilarated, I smashed out the bulk of my CLI (first draft) in one day.

**Choosing the variety..**

An exciting facet of the project was choosing my own topic! Naturally, I chose something that I have a strong interest in - wine. Australian wine, in particular.

I relocated to the United States late last year and I can now say with certainty that absence really does make the heart grow fonder. The reduced availability and accessibility of quality Australian wine has only heightened my love of it.

James Halliday is a well-known Australian wine writer, critic and winemaker. Each year, he selects his Top 100 Australian red, white and sparkling wines (and a few Champagnes for good measure). My gem retrieves the selected red and white wines and presents them to the user in a list or via the relevant categories.

**Refining the blend..**

Despite this being a relatively smooth process overall, there were some hiccups and a few direction changes along the way.

Each category of wine is presented on a separate web page. My CLI gem scrapes the initial URL containing the categories, then scrapes the individual URL of each category to populate the category with the applicable wines.

A few days into working on my gem I built a ‘List all’ function, and realised that my ‘Top 100 Wines’ list actually contained 87 wines…

I soon discovered that the Champagne category linked to a URL with a completely different HTML structure than the URLs for the other 5 categories. The fix: I built a customer ‘Champagne scraper’.

However, mid-way through that process I decided to scrap it - I don’t even like Champagne that much, and liked the idea of limiting the gem exclusively to Australian wines. I changed the scraper to only retrieve categories relating to red or white wines, and re-jigged my CLI accordingly.

A few days later, an entire category disappeared.. “Best Australian red wines over $25” — my favourite kind! I debugged and scratched my head and ‘pried’ around for far too long before realising that section of the site was down.

This prompted me to incorporate an error message, displayed in the event that the gem cannot scrape categories from the site. There are still a thousand ways my gem could break, but at least the user will be informed if it breaks *that* particular way.

Next, I decided to extent functionality to view by variety and by region. I began building methods to list all varieties and regions and then display the corresponding wines, in response to user input. I also began wondering when to stop..

Thankfully - at this point I had a 1:1 with an instructor. Perfect timing! He gave me some great, feedback on my gem, and some fantastic advice. I stopped extending functionality and polished what I had already created.

**The aging process..**

Like a fine wine, I suspect this gem will age well. I have already thought of 100 ways to improve and extend the gem’s functionality. This could be a project I come back to periodically.

After all, this is only version “0.1.0” and contributors are welcome!

My gem is published on RubyGems.org (halliday_wine_list) and on GitHub (https://github.com/remclay/halliday_wine_list). Please check it out and feel free to contribute.

