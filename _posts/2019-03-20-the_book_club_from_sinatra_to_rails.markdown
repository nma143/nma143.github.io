---
layout: post
title:      "The Book Club: From Sinatra to Rails"
date:       2019-03-20 21:19:04 +0000
permalink:  the_book_club_from_sinatra_to_rails
---


## Background
​
I created a book club app for my Sinatra project. With the User, Book, and Review models - this book club turned out to be a good fit for the Rails project requirements. I decided to stick with it - not for a lack of creativity, but rather to better explore the differences in using Rails vs Sinatra.
​
## Getting started
​
For me, typically setting up the architecture has been the least straightforward part of the projects so far. But I have to say, with Rails, this was quite easy. I had a little trouble with the sqlite3 gem version (which I fixed up in the Gemfile), but besides that the commands `rails new project-name`, `rake db:create`, and `rails s` got me to "YAY! You're on Rails" in no time.
​
## My Approach

I began by creating the models, migrations, and associations. I then created the seed file and populated a list of books into the database.

Next, I created the static controller and view for the root. I then built out the sign up and log in functionality in the sessions ans user controllers. I added validations to the User class so errors would display on the sign up and log in views. 

With the sign up and log in features working, I then got going with Review and Book controllers and views. 
​
Once a user could sign up, log in, create/edit/delete reviews, and see information about the books, I reworked review urls to be nested. I knew I wanted to nest reviews, but since they belonged to both users and books, I mulled this over for a bit. 

In my Sinatra app, a user could create a new review from their user page. The new review form had a book selector so the user could pick which book within the form. This setup made me lean towards nesting reviews under users, but ultimately I chose to nest under books. Since the app always knows the user’s id (login is required), there was more to gain by nesting under books. This was the first big change between the two apps. Now, the user picks a book before they get to the new review form. Also, I made it so the book id for a review can not be changed. In the Sinatra app, the user could change the book for an existing review. 

Also, I often found myself asking “To nest or not to nest?”. For example, there seemed to be no need to nest the review delete route under books. The book id is not required when deleting a review.

After the Review model was set up, I worked on the Book model and added some class methods to allow users to sort book data. Here I really used the command `rails c` often to develop and test the methods.

Next, I added some error handling for nefarious actions such as:
* a user trying to edit a review someone else wrote
* going to a book page or review page that doesn’t exist
* trying to create another review for a book the user has already reviewed


Lastly, I added the log in and sign up via Facebook. When a user is created via a Facebook login, I had to decide what I wanted to happen with the user's username. I wanted it to be a bit more thoughtful than the random number generator for the fake password. The username needs to be unique. It is how the user is greeted and tells other users who wrote a particular review.
​
## The Magic of Rails

I really liked how quickly I could get up and running. I also liked how partials can be used for views and how a form can be used for both creating and editing. It really does feel like a lot less code than my Sinatra app.

On the other hand, looking at the code - I find Sinatra easier to interpret. For example, in Rails - 
`resources :books` sure gets you a lot of routes. Also, when looking at the code for a form, you don’t see the method and action. So although you can get started quickly, and you don't need to write a lot of code, I definitely would say Rails is not for beginners. Looking at the code, there's a lot left unsaid and you'll need to read between the lines to fully understand.

But it is pretty handy, so definitely worth learning and mastering :)

