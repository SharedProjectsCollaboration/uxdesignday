UX Design Day
=============
[uxdesignday.org](http://uxdesignday.org)

Source code for uxdesignday.org - static HTML, CSS, and a little bit of JS. Founded, designed, and predominantly built by Benjamin Humphrey with some help from Sam Tran, and Dave Strydom for the resources list.

### TODO

### For UXDD Wellington

* Update intro text, location, price, etc.
* Update metadata for Facebook / Twitter sharing
* Update the link to purchase tickets
* Update list of speakers and their images (at 2x for retina)
* Update list of sponsors and their logos (at 2x for retina)

#### General

* Add new resources
* Make the splash / home page responsive for mobile
* Install Node on the server to do server-side compiling
* Set up hooks instaed of using a cronjob to deploy
* Set up Github Issues for tracking global problems / feature requests
* Refactor all the things

### Structure

So for now, the structure is a little bit crap but until I have some more time, this is what we have. Basically the server has some subdomains set up for each conference, eg. dunedin.uxdesignday.org and wellington.uxdesignday.org.

These subdomains are hooked up to a cronjob which pulls down the corresponding branch every few minutes and looks into the /public directory. So wellington.uxdesignday.org will reflect whatever is in the /public folder of the branch 'wellington'.

This hasn't happened yet, but eventually master will simply be global styles and layout, and a splash page pointing people towards the individual conference pages. The idea is that you will occaisonally merge master back into your individual conference-specific branches.

Global changes should be tested in the 'beta' branch first (beta.uxdesignday.org) before being deployed to master (uxdesignday.org).

FYI - uxdesignday.com just redirects to .org.

### Dependencies

Uses [Coffeescript](http://coffeescript.org/) and [Stylus](http://learnboost.github.com/stylus/), and it's compiled using Node.js, so you'll need to install that on your computer. Also install npm (node package manager). More on that below.

IMPORTANT: The server doesn't yet compile anything, so you will need to compile locally into the /public directory and push that up to Git. Don't ignore that folder. Also, don't delete it - there are some assets in there that don't get automatically generated when you compile.

### Running locally with Grunt (recommended)

* [gruntjs.com](http://gruntjs.com/)
* [nodejs.org](http://nodejs.org/)
* [npmjs.org](https://npmjs.org/)

A Gruntfile with a 'dev' task is available for development.

#### Install grunt-cli (may need to use sudo)

    npm install -g grunt-cli

#### Install the node prerequisites

    npm install

#### Run 'grunt dev' to watch for changes in the Coffeescript and Stylus files.

    grunt dev

#### Rebuilding JS and CSS from scratch

    grunt build

### Deploying

Anything you push to the master branch will be live on uxdesignday.org and uxdesignday.com within 10 minutes of pushing it. Only merge your working branch into master (after merging master into your local branch first, of course) when you're confident everything is looking peachy! 

You will need to compile locally using 'grunt build' before pushing, since the server simply points to the /public directory and does not compile the code on its own.

Then simply push up master, and the server will pull down the latest changes within 10 minutes.


### Questions?

Email me at benjamin@uxdesignday.org.
