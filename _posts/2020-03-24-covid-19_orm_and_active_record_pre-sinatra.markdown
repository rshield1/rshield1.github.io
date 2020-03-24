---
layout: post
title:      "COVID-19, ORM & Active Record (Pre-Sinatra)"
date:       2020-03-24 06:38:00 +0000
permalink:  covid-19_orm_and_active_record_pre-sinatra
---


This has been a tough month for focusing.  Being in the airline industry, we've taken a huge hit due the COVID-19 pandemic.  I'm sure you all are aware of the "social distancing" term and how important it is, however being isolated in my apartment with my thoughts has been extremely difficult.  I've allowed myself to lose focus due to the everyday struggle of not knowing if I'd have a job when I returned to work. We still have to fly during this crisis, so sometimes I don't even feel safe being around my family.  I can honestly think this is another calling for me to pursue my software engineering career.  Having skills that nobody can take away from me is vital, and makes me irreplacable in the tech industry!

ORM?

Object Relational Mapping  is a design that maps ruby programs to connect to databases.  In OOP, think of  class = database table, and instances = Rows.  First you'd Initialize your database with a connection; 

"database_connection = SQLite3::Database.new()"

You can then use SQLite3 in your code using built in methods associated with SQLite3.  Now SQLite3 syntax can be used in your methods, such as; 

def self.create_table
    sql = <<-SQL
    CREATE TABLE students (id INTEGER PRIMARY KEY,
    name TEXT,
    grade ID)
    SQL
    DB[:conn].execute(sql)
end
		
 It's taking a little longer to grasp the class to connection relationship in ORM, however when I'm able to build my personal project, I'll continue to revisit these lessons.  I hope I don't fall too far behind.

Now for Active Record.  What is this thingy?

Active Record is a Ruby gem thats an easier form of connectivity between your database and objects.  Similar to ORM, you'll need to establish your connection with your database, such as "ActiveRecord::Base.establish_connection". This is where inheritance comes in, where you're able to access all of the methods available in the AR gem to use in your objects. 

class Object < ActiveRecord::Base
end

It's a bit easier fo me to digest, since it follows the (CRUD) Mechanics of programming; Create, Read, Update, & Delete.
For example;

Object.create(name: 'Rob')
is saying "INSERT INTO objects (name) VALUES ('Rob')"

Now thats making things a bit easer to understand. Even if I feel lost, I always check the documentation and/or github page to make sure I'm utilizing the methods correctly.

In conclusion, this month has been a roller-coaster.  I've had moments where I thought I'd have to just take a break and resume in a later date, however having the accountability and support of my cohort lead and peers has been helpful.  I've slacked long enough, but now its time to start moving and focusing a bit differently.


I'll get there!
