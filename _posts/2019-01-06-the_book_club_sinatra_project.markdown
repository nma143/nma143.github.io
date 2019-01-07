---
layout: post
title:      "The Book Club Sinatra Project"
date:       2019-01-07 00:32:06 +0000
permalink:  the_book_club_sinatra_project
---


## The idea

The idea for my project was a book club with a pre-loaded library of books. Users can sign up and review any book in the list. They can also see the reviews submitted by other users, along with an average rating for each book. 


## Setting up the architecture

For readers who are following my blog - you'll know, that for me, the toughest part of the previous project was running certain commands in the terminal (eg. `bundle`). At the time, I found a workaround, but for this project, I solved the issue. I needed to install Ruby Version Manager (rvm). Step 7, of [this guide](http://help.learn.co/technical-support/local-environment/mac-osx-manual-environment-set-up) really helped. 

When it came to setting up the config,ru, gemfile, rakefile, environment.rb, and application_controller.rb - [this video](https://www.youtube.com/watch?v=_S1s6R-_wYc) was a great resource. 

Two noteworthy errors:

1. When running shotgun for the first time, the browser showed the following error: **NoMethodError: undefined method 'needs_migration?' for ActiveRecord::Migrator:Class**.
This was fixed by replacing `if ActiveRecord::Migrator.needs_migration?` in config.ru with
`if ActiveRecord::Base.connection.migration_context.needs_migration?`
2. I forgot to add the bcrypt gem for passwords and saw: **LoadError: cannot load such file -- bcrypt**

Again, I would say that installing rvm and setting up the architecture from scratch - to the point where I could get to the route domain and display "Hello World" - was the toughest part for me. It didn't take too long, but this was where I referenced a lot of resources for help. 

I also downloaded and installed [DB Browser for SQLite](https://sqlitebrowser.org/) to easily view the database as I was programming. 

After all this, it was smooth sailing :)


## Adding the extras

Coding the main components of the models, views, and controllers was very straightforward and similar to past labs. I had the most fun incorporating some simple styling to views, adding links for easy navigation, and incorporating error messages with the [sinatra-flash gem](https://github.com/SFEley/sinatra-flash). With these extra features, it really feels like an app that's ready to be used. Pretty cool!

