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

![]https://www.dropbox.com/h?preview=Binge-rater-schema.jpg)
# Getting Started
Building an app from scratch can be extremely difficult, but worth the challenge.  It gives me the opportunity to begin really showcasing my skills!  I've been able to build difficult things due to the Flatiron labs, but knowing that I'll have to point guard this application myself, it will prepare me for my code reviews if I just add comment as I go!

The first thing I decide to do was jot down some schema ideas and walk my brain through the navigation of my application.  What will this user Robert will be able to do on this app?

"I want to be able to post and rate shows for other users to view."

Let's break it down even further. Robert would create his account by signing up, then he will be directed to his dashboard. He would then be able to create a new show that he has "binge-watched.  It would then be displayed on the "shows" show page, he can edit his ratings, description, etc.,  if needed. He can alsow view other "show" by other users, but cannot edit/delete them.  The schema was primarily focused around shows.

Lets think about the Ruby classes: Users, Shows, and maybe Ratings. The associations would be important as I would need to incorporate my database to correctly use the belongs_to, has_many, macros.

This was primarily my schema built with illustrator:


-----my schema photo here-----

https://www.dropbox.com/h?preview=Binge-rater-schema.jpg


This schema is a very simple schema, however, I didn't find myself even needing a star class.  I primarily wanted to break up the rating into stars, but I thought that would be too complicated.  I also thought about separating the categories, since they would be collected in the required dropdown list, and users could view shows by category, but that also would be overkill for this application.  I may use all of my weapons when its time to tackle React. 

The technical plan from is that a User has_many Shows, A Show belongs_to a User, and has many Ratings, or maybe categories. The schema still need a little work, however I was so excited to get started and I knew that I would make the necessary changes once I began working through the project.



# Using the Corneal gem
I thought It would be easier to set up my app if I had a way to set up a blueprint of the necessary files for my app.  Thats where Corneal comes in.  Corneal is an app generator for Sinatra that sets up your necessary folders, files, and dependencies to get you started with a simple "corneal new APP-NAME."  Once my files were in place, I added and deleted necessary gems, views, and folders to complete the layout.  I also set up the github repository and created my first git commit..... -m"first commit"
# Learning with clean code
---------coming soon-------------
Seperation of concerns.  Adding that along with comments and meaningful commits allowed me to focus on a sequential system to plan out my code.
# Incorporating AR and Associations

In order to primarily connect my app with a database, I have to establish a connection within your environment folder.  This folder holds the information you will require to run your application.
```
#Connecting our database
ActiveRecord::Base.establish_connection(
  :adapter => "sqlite3",
  :database => "db/#{ENV['SINATRA_ENV']}.sqlite"
)
```
You want to create association models that corresponds with your tables
Model example
```
class User < ActiveRecord::Base

has_many :shows

end
```
Table example
```
class CreateUsers < ActiveRecord::Migration
  def change
    create_table :users do |t|
      t.string :username
      t.string :email
      #password digest is for the bcrypt gem, keeps it secured to store encrypted version
      t.string :password_digest
    end
  end
end
```
Having ActiveRecord::Base gives you access to methods such as has_many, belongs_to, and many more to associate your models with one another.

Now I can begin to construct my tables by using 'rake create_migration NAME="name-of-table"'.
This will generate a .rb file with a class using inherited my ActiveRecord::Migration, which gives you access to certain methods, such as change, up, down, create_table, etc.  It does the SQL queries for us.

# Using Bootstrap/Ruby Gems

Now, its time to beautify my code!  Well, at least make it look a little cleaner.  I decided to create my custom logo will illustrator, along with a few custom pictures that fit the project name.  Also, I used a cool unsplash link that used custom photos during the log-in refresh, sign-up, and the dashboard.  I noticed I spent a lot of time working on making sure that the user experience wasn't sloppy or inefficient.

I was also able to create custom error messages using the Sinatra Flash gem.  It allowed me to control the messages during the refeshing of a user log-in/Sign-up error, and a success alert when a user created a show successfully. 

There were many other gems such as bcrypt, which help with the encription of user password by using the sinatra gem.  This allowed me to control the user's session as long as they were logged in.

Tux and Pry were mainly used for testing purposes.  Tux allowed my to test out my tables before migrating them into the database, and Pry was used for testing out my params, to make sure I was obtaining the key/value pairs needed in my .erb forms.
# DRY
----coming soon----

# Getting Feedback
Getting Feedback was important since I wanted to make sure the user experience was manageable. So I allowed a few of my peers to navigate through the app as we tested for any hiccups or errors that would occur. Also, I created a seeds.rb file that I created Users and Shows.
```
User.destroy_all
Show.destroy_all

kenny = User.create(username: 'KennyP', email: "kenny@gmail.com", password_digest: 12345678)
erica = User.create(username: 'Ericawhite', email: "erica@gmail.com", password_digest: 12345678)

show =Show.create(name: "Ozark", category: "Suspense", seasons: "8", description: "just another show", rating: 5)
new_show2 =Show.create(name: "Fresh Prince", category: "Comedy", seasons: "8", description: "just another show", rating: 5)

```
# Completing the checklist
The specs for completing my project was extremely helpful.  It kept me from straying too much down the wrong path.  

Specs:

 x Use Sinatra to build the app
 x Use ActiveRecord for storing information in a database
 x Include more than one model class (e.g. User, Post, Category)
 x Include at least one has_many relationship on your User model (e.g. User has_many Posts)
 x Include at least one belongs_to relationship on another model (e.g. Post belongs_to User)
 x Include user accounts with unique login attribute (username or email)
 x Ensure that the belongs_to resource has routes for Creating, Reading, Updating and Destroying
 x Ensure that users can't modify content created by other users
 x Include user input validations
 o BONUS - not required - Display validation failures to user with error message (example form URL      e.g. /posts/new)
 x Your README.md includes a short description, install instructions, a contributors guide and a link to the license for your code
 
Confirm

 x You have a large number of small Git commits
 x Your commit messages are meaningful
 x You made the changes in a commit that relate to the commit message
 x You don't include changes in a commit that aren't related to the commit message

