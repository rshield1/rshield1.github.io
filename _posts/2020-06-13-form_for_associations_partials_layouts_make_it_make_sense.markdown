---
layout: post
title:      "Form_For, Associations, Partials/Layouts; MAKE IT MAKE SENSE!!"
date:       2020-06-13 15:23:51 +0000
permalink:  form_for_associations_partials_layouts_make_it_make_sense
---


Initially when I began learning rails, it was a bit of a blur.  Dealing with <%= Form_tag %>, then transitioning to <%= Form_for %> was a bit confusing.  To make it even more challenging, lets add in NESTED FORMS and give you a <%= Fields_for %> form to build it within your form.  Learning this was a nightmare!  However I will say that as I made it to the end of the rails amusement park section, It began to start coming together! I never thought I would be able to understand the associations, scope methods, nor the nested forms so well.  Up to this point, I still struggle with the hidden_input and filters.  Ill continue to revisit the lessons to it an understanding.  Lets break down what I've learned....

#Form for vs Form tag.

The only major difference between thes two is that form_for is used when there is a model attached, and form_tag doesnt require the model.  Also, form_for uses field helper methods.  I've utilized both in my social fitness application.  All of my form_for forms have models attached to them.  

`<%= form_for(@workout) do |f| %>
    <div>
        <%= f.label :title %>
        <%= f.text_field :title %>
    </div>

    <div>
        <%= f.label :description %>
        <%= f.text_field :description %>
    </div>

    <div>
        <%= f.label :time %>
        <%= f.number_field :time, min: 1, max: 120 %>
    </div>

    <div>
        <%= f.label :difficulty %>
        <%= f.number_field :difficulty, min: 1, max: 5 %>
    </div>

        <%= f. submit %>
<% end %>`

Workout has a model and I use the builder methods such as f.text_field and f.number_field to build this form. 
I used the form_tag to create my filter because I wanted to capture custom filters.  I wouldn't be able to do this in form_for, since it specifically ties in with the model attributes.  Theres more flexibility with the form_tag

```
<h3>Filter posts:</h3>
                   <%= form_tag("/workouts", method: "get") do %>
                    <%= select_tag "date", options_for_select(["Today", "Old News"]), include_blank: true %>
                     <%= submit_tag "Filter" %>
                     <% end %>
            
```

I'm not sure if that describe the difference between the two.  Both can be used in specific situations.

#Associations

Now with associations, there has been a bit of confusion dealing with has_many_through association setting up my models.  For example, I know that whatever has many through, must first has many of that model.  In my model, I wanted my comments table to belong to a user and belong to a workout.  This was an indication that I needed comments to be my join table! So with this knowledge, I knew that a USER has_many comments, and a USER has_many workouts_through comments.  Also a WORKOUT has_many comments, and a WORKOUT has_many users_through comments.  Now dealing with the relationships were challenging, primarily, however I started to make it make sense when I was ble to create an actual model I could visually comprehend.


#Partials/Layouts

Now the snytax for partials and layouts can still be a challenge, so I decided to download an extension that would help out with code snippets! I've used both layouts and partials.  Ill give an example where i used a multiple layouts and partials.  If I used a form more than once, I wanted to be able to DRY my code, so I decided to use the workout form as a partial, since I'd be using it in my new/edit views.  The first order of business was to figure out where to begin my partial. I started from the beginning of the form.  <%= form_for (@workout) %> and created its own view using this syntax "form.html.erb" as the view.  The ""  allows rails to find the view when you use <%= render 'form' %> in your "new" and "edit" views.  Dealing with that was relatively easy.  What about dealing with circumstances where the object could be different?  

WELL, there's a partial for that!
```
<%= render partial: 'layouts/errors', locals: {obj: @workout} %>
```

Let me explain.  I have a partial called _errors, which is located in the layouts folder.  In my errors.html.erb, I have this layout 
```
<% if obj.errors.any? %>
  <div id="error_explanation">
    <h2><%= pluralize(obj.errors.count, "error") %> prohibited this from being saved:</h2>
 
    <ul>
    <% obj.errors.full_messages.each do |msg| %>
      <li><%= msg %></li>
    <% end %>
    </ul>
  </div>
<% end %>
```

So where "obj" exists, I want to substitute with the instance variable @workout.  Thats it!  I've created an error page where I can render in my workout form!  It looked harder than it actually was.  All this was located in the rails guide.

#One more thing....Source

Using source to help filter through my category, and workout database was a bit of a challege at first.  So I did my resarch on how to implement them.  Scope methods are defined in your models, which you can call on self within your controllers
Category
```scope :filter_duplicates, -> { group(:name).having("count(*) >= 1")}```
This scope was implemented before customizing my own custom 'accepts_ nested_attributes' method.  Filtering through duplicates is inefficient, due to the duplicates existing in the database to begin with.  How about lets find a way to iterate through the database to find a duplicate BEFORE it even hits the database!

```    def category_attributes=(hash)
      category = Category.find_or_create_by(name: hash[:name])
      #push it into workout
      self.category = category
    end
		```
		Essentially, we use the .find_or_create_by method given to us within rails to search through the database to check if the category even exist before placing it into the database. The category will be assigned to Workout.category (self).
		
		
Workout
```scope :order_by_comments, -> { left_joins(:comments).group(:id).order("id asc")}```

In my Workout model, I created a scope method I can use to group the user's workouts based on the amount of comment associated with them.  Left_joins make a join table with a single query into the database, then order that group using the comments.  Now I can call this method on "self", which is on the Workout model within my controller to filter Workouts by comments.


