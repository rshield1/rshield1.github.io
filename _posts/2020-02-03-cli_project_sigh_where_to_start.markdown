---
layout: post
title:      "CLI Project?  *Sigh* Where to Start! "
date:       2020-02-03 05:29:11 +0000
permalink:  cli_project_sigh_where_to_start
---


As I continue to stare at my windows terminal, I reflect on the times I spent learning how to "cd" into folders, check the "directory", and "delete" files, I started to have a mild mental breakdown.  Then, I remember to just write down my tasks, and break them up into smaller, managable "components." 

I begin with my easiest step.  Step 1: Create my project folder using "mkdir" in the windows terminal.  Luckily I've spent a lot of time going through Youtube, and Avi's videos to obtain more clarity on testing/developing techniques. 

The next step is to set up my bundle files.  Lets run - bundle gem "name" - so I can have a standard boilerplate.  This gives me an opportunity to browse the files created to get an insight of what to expect when I clone repositories on Github. I thank the developers that made coding efficient for future developers. 

My task was to first write down the actual goals for my program; to let the user interact with the command line to figure out their body type, get standard information about their type, then obtain training techniques to help them train accordingly.  I also want to scrape links from the website based on their goals.  I needed to locate a site I wanted to scrape the information.  I chose scraping for additional practice, since I wasn't fully confident on my ability to efficiently scrape.

Let’s begin!!!


Every class should have one job:

Run <=  This file will run my Cli.rb file, which contains my Cli.new.call method -- bin/run

Scraper.rb <= This file will hold all of the scraping that will be implemented on the site -- lib/scraper.rb

Cli.rb, <= It is responsible for interacting with the user using puts/gets. --lib/Cli.rb

Body_Type.rb <= Will hold the various body types. --lib/Body_Type.rb

Environment file <= Holds all require/require_relative files needed to link the files and gems. --lib/environment.rb

Module.rb <= Used to consolidate and structure my code for a clean feel. --lib/module.rb 


* In my run file located in the bin directory, I first require my environment.rb file needed to run the application, then I call on the Cli object by typing "Cli.new.call" so it could run when the file is executed.  My "call" instance method has the appropriate methods needed to run the application.

* In my environment file, I load all of my linked files here, such as modules, scraper, Nokogiri, pry, and other gems.

* My Cli.rb file has the Cli class that "includes" the module BodyType, which I used to consolidate and move most of my created methods over to the BodyType module.  I just needed a clean feel to the application.

* When the user inputs a body type, it creates a Body_Type.new object, which will take the input as name.  It initializes with the name of the bodytype.

* The Body_Type have a few instance methods which will be based on the name of the body type. Once instantiated with the appropriate name, It obtains that instance method, which will collaborate with the Scraper class, by instantiating a new Scraper.  This class holds the methods for the document that will require scraping.

* Using Nokogiri and Open-URI, I can load the url and inspect the page elements to locate the items to scrape beginning with   "@@doc = Nokogiri::HTML(open("https://www.bodybuilding.com/fun/becker3.htm"))"
* So when the user requests information/training techniques, the url will scrape the paragraphs associated with the body type of the user.  I created this as a class method, so all methods have access to the url. It helps with the continuous calls to scrape the website. 


I had to locate many different ways to scrape out the appropriate paragraphs that were associated with the website.  I was able to recall using the array range to group the paragraphs needed.  Oh, and this is where I HAD to become even better at using 'pry', which is now a big part of me debugging massive lines of intimidating code.  If I have 'pry', I can’t lose!

((ectomorph_info = puts "#{@@doc.search("#DPG p").children[4..8].text}")) <= "I FIGURED IT OUT"

You search the document and pull the children elements, which are the "<p>" tags.  I grab the text from the 5th through 9th paragraphs.  This scraping technique was used throughout the entire application.  Once I was able to do a little research on StackOverflow, my workload seemed smaller and smaller.  I didn’t realize how much code I've learn after I was forced to code without internet on a 3.5 hour flight to and from Costa Rica.

When I returned home, I also ran into another issue; How can I scrape all of the a tags that were located in the paragraphs?  Iterate over each tag, and grab certain elements, such as the name & website associated with that name?
I had to continue using pry to see what information I received from certain inputs.  It helped me grab those elements needed to use an enumerable to receive a cluster of information using block formatting.

INFORMATION RECEIVED THROUGH 'PRY'

#(Element:0x43e3c18 {
        #name = "a",
        #attributes = [ #(Attr:0x446b0dc { name = "href", value = "https://www.bodybuilding.com/content/how-to-gain-weight.html" })],
        #children = [ #(Text "gaining muscular weight")]
        #})

USING AN ENUMERABLE TO SCRAPE THE INFORMATION NEEDED

def all_links
        links = @@doc.search("#DPG p a")
        links.each do | link |
            puts "#{link.children.text.capitalize}:"
            puts "#{link.attributes["href"].value}"
            puts "________________________________"
        end
    end

I was able to create and init my Git local repository along with all of the other prerequisites to push my files to my Github repository. Making frequent commits to keep track of my changes helps me remember the process before the push.  Everything is slowly beginning to come together.  I'm finishing up the final touches to my CLI project to tidy up my code.  This project literally took only a few days of endless coding to get the concepts embedded to the point it's starting to come together!

I'll get additional feedback from my instructor and review a few lessons to make sure I'm still on the correct track to become a better and efficient developer.  Maybe even add to my program!!

