---
layout: post
title:      "Friends who make you laugh and pry"
date:       2017-12-08 04:44:39 +0000
permalink:  friends_who_make_you_laugh_and_pry
---


To begin with I did **not** like using ‘pry’. Why? In short, because I had no idea what I was doing. I felt safe within the confines of IRB (Interactive Ruby). Yes, there was a lot of copying and pasting involved, but I know how to copy and paste.

IRB served me well most of the time and if I ever really got myself into a bind I’d jump onto repl.it and copy and paste some more.

I understood the basics of pry (the Learn IDE makes it nice and easy). I could require pry and start a pry session; I just couldn’t derive any useful information from it! I tried it out once or twice and simply walked away feeling more confused.

As the weeks went on, pry popped up more and more. I’d be watching a lecture or be in the middle of a 1:1 screen share and ‘pry’ would rear its ugly head. I knew this was a tool I needed to start using – it was a non-negotiable.

A few weeks ago, exacerbated, I threw a `binding.pry` into the method I simply could not get to work. I checked the value of a few variables and – to my surprise – the location of the bug became obvious. I had it fixed it no time. That was my ‘lightbulb’ moment. Simple as that. All that build up and using ‘pry’ was that easy.

I couldn’t remember why I was making such a fuss. My biggest barrier to learning how to use pry was my reluctance to learn how to use pry!

My favourite feature? (Coincidentally the only feature I have properly explored) Runtime invocation. Debugging has become 100x easier and faster.

The need for copying and pasting is eliminated, there is syntax highlighting (unlike IRB), the output is visually simple and easy to interpret. The pry gem is already installed, I can pop `require ‘pry’` at the top of my .rb file, throw in a binding where needed and away I go. Not only does pry have access to all of the code in the .rb file in question, it also has access to the spec files (thank you, IDE!). The days of spending time coming up with artist’s names and pet species are over. I can ‘pry’ around in my method using input from the spec file. 

Surprisingly, the initial learning curve was very manageable. Emphasis on initial! I’ve only just scratched the surface with pry – the list of features is long and impressive, and it is customizable…but so far, within the realm of OO Ruby, pry and I have made friends. 

The larger take home for me has been to stop putting off giving a new tool/resource/feature a proper try. Maybe I’ll like it maybe I won’t, maybe I’ll be good at it, maybe I won’t, but putting off trying it out isn’t getting my anywhere!


NB: To date I have only used pry within the Learn IDE, so that’s what I'm speaking to, but the differences are not huge (the IDE does some of the leg work for you and cuts out a few steps).


