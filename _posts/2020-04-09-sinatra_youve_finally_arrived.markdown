---
layout: post
title:      "Sinatra, You've Finally Arrived"
date:       2020-04-09 21:06:10 -0400
permalink:  sinatra_youve_finally_arrived
---



# What to do?

In completion of my Sinatra Ruby application, I wanted to wrap-up my project and reflect on the earlier days where I didn't have a clue on the direction I wanted to take in building my app.  After browsing a few websites for ideas, I wanted to make my project usable, and I wanted to gear from utilizing anything fitness related, since my CLI project was aimed in that direction.  For practice purposes, I went through a couple of app ideas that could be useful to someone, such as an expense tracker, a calendar, a meme generater, a blog engine, an a show rating app.


# Getting the idea
During these challenging days due to COVID-19, I decided to stick with something we would be doing, "binge watching."  Maybe people would like to give a great rating and description to shows before others decide to binge watch the show. Sounds simple, right?   People's problems during this time are uncertain, I'll continue to think of new app ideas that will catapult my skills into another statosphere, but until then....

My Sinatra app- Binge Rater is here!!

----------photo of the appp--------------


# Getting Started
Building an app from scratch can be extremely difficult, but worth the challenge.  It gives me the opportunity to begin really showcasing my skills!  I've been able to build difficult things due to the Flatiron labs, but knowing that I'll have to point guard this application myself, it will prepare me for my code reviews if I just add comment as I go!

The first thing I decide to do was jot down some schema ideas and walk my brain through the navigation of my application.  What will this user Robert will be able to do on this app?

"I want to be able to post and rate shows for other users to view."

Let's break it down even further. Robert would create his account by signing up, then he will be directed to his dashboard. He would then be able to create a new show that he has "binge-watched.  It would then be displayed on the "shows" show page, he can edit his ratings, description, etc.,  if needed. He can alsow view other "show" by other users, but cannot edit/delete them.  The schema was primarily focused around shows.

Lets think about the Ruby classes: Users, Shows, and maybe Ratings. The associations would be important as I would need to incorporate my database to correctly use the belongs_to, has_many, macros.

This was primarily my schema built with illustrator:


-----my schema photo here-----

![](https://www.dropbox.com/h?preview=Binge-rater-schema.jpg)


This schema is a very simple schema, however, I didn't find myself even needing a star class.  I primarily wanted to break up the rating into stars, but I thought that would be too complicated.  I also thought about separating the categories, since they would be collected in the required dropdown list, and users could view shows by category, but that also would be overkill for this application.  I may use all of my weapons when its time to tackle React. 

The technical plan from is that a User has_many Shows, A Show belongs_to a User, and has many Ratings, or maybe categories. The schema still need a little work, however I was so excited to get started and I knew that I would make the necessary changes once I began working through the project.



# Using the Corneal gem
I thought It would be easier to set up my app if I had a way to set up a blueprint of the necessary files for my app.  Thats where Corneal comes in.  Corneal is an app generator for Sinatra that sets up your necessary folders, files, and dependencies to get you started with a simple "corneal new APP-NAME."  Once my files were in place, I added and deleted necessary gems, views, and folders to complete the layout.  I also set up the github repository and created my first git commit..... -m"first commit"
# Learning with a friend 
----coming soon----


# Incorporating AR and Associations

----coming soon----
# Using Bootstrap

----coming soon----
# DRY
----coming soon----

# Getting Feedback

----coming soon----
# Completing the checklist
----coming soon----

