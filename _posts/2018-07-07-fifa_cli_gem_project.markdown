---
layout: post
title:      "FIFA CLI Gem Project"
date:       2018-07-07 23:07:25 +0000
permalink:  fifa_cli_gem_project
---

The approach, struggles, and surprises ... 

#### 1. Find a site to scrape

* This was my first step. I needed the idea before I could decide how to name the gem files. 
* I knew picking a well-built site to scrape would make the project much easier, so I was expecting to take a lot of time trying to find one. 
* Luckily, it actually only took a few minutes. There was a lot of FIFA buzz in the air, so I explored the tournament's site, and it was great! 
* I used the **inspect** tool in Google Chrome and saw the site was well-built. 
* I confirmed I could scrape it by running the `curl url` command in my terminal. 
* Phew! Step 1 - which I thought would take a while, was super quick :) On to step 2!

#### 2. Create a gem using bundler

* This was the toughest part of the project for me. I wasn’t able to run the `bundle gem` command in my terminal. I did some troubleshooting, but eventually decided not to waste more time here.  So I used the Learn IDE to run the command. I then copied the project folder from the temporary location of the IDE to my desktop.
* Although I’m glad I didn’t let this error gobble up my programming time, having to use the IDE at all was disappointing for me. I was looking forward to programming the project without the comforts of the IDE. Seeing that I am capable of developing a complete project with just a basic editor would have been empowering. 
* I will have to make time to solve the bundler issue.

#### 3. Initial push to GitHub

* Along with bundler, pushing to GitHub also did not work in my terminal as it does in the IDE.
* The workaround would have been to use the IDE for coding the project, but I was not willing to do that. So I did spend quite some time here getting this fixed.
* I needed to create an SSH key. This was the [guide]( https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) I used.
* The key git commands used throughout this project were:
```
git init
git remote add origin remote-repository-URL
git status
git add .
git commit -m "description of changes made"
git push origin master
```


#### 4. Set up dependencies, environment, and CLI file

* Setting up the *require* and *require_relative* statements, and also the files required for running the CLI from the bin directory using the command `./fifa` took some trial and error. 
* I found the example project on GitHub very helpful.
* Ultimately, I never used the `./fifa` command, because while in the terminal, I always stayed in the project folder (one level up from bin). This was because it made pushing to GitHub faster.
* While in the project folder, the command needed to run the CLI was: `./bin/fifa`
* For these commands, execute permission needed to be granted. Using the terminal, and navigating to the bin folder of the project, the following commands were required:
```
ls -lah
chmod +x fifa
```
* Also worth noting, the `require ‘pry’` line threw an error. I just removed it and didn’t waste time troubleshooting this one. I was confident using `puts` statements strategically would work fine for debugging my code.
* Getting pry working in my terminal as it does in the IDE is something I will also need to make time to solve. 

#### 5. Get coding!

* After getting a simple `puts` statement to print from the cli.rb file, the program came together very quickly. None of the CLI requirements were unfamiliar from labs, so it was smooth sailing. 
* I started with writing the core of the cli.rb file. Then I wrote the team and player classes. I just hard-coded fake team and player data to make sure methods were working as desired. 
* When the app was functioning well with fake data, I wrote and integrated the scraper class.

#### 6. Record walkthrough 

* Admittedly, this took a few takes to get it right, but it was fun.
* I used QuickTime Player (File > New Screen Recording).
* Imagine if all developers provided a full demo of their software/app. That would be amazing. 

#### 7. Blog

* I saved this blog requirement for last. 
* I’m new to blogging, and don’t like it much at this point, so my progress came to a standstill when this was the last submission requirement. 
* I do understand the importance of writing about coding, but for me, a blank page is much more daunting than a blank script file. I think that's because I find direction quickly when I have a clear goal to achieve by the end. Hopefully with more practice, the blogging will become easier. 

#### Final thoughts

* This was a really good exercise. I look forward to the feedback!






