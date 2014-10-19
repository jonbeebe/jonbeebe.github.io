---
layout: post
title: "Back to BBEdit"
date: 2014-10-19 15:43:00-0700
---

> It doesn’t suck.®

BBEdit originally debuted on Macintosh System Software 6[^1], and while it may have been surpassed&mdash;feature-wise&mdash;by other text editors in recent years, it's actually one of the only OS X text editors that can meet the following criteria (and meet it well):

1. Truly native Mac software; feels "at home" visually and works as you would expect a Mac app to work. In other words, it's very "Mac-like".
2. Has a history that can provide assurance that it'll most likely be sticking around and actively developed for many more years to come.
3. It is fast.

We're getting to a time where text editor speed is almost taken for granted, but point 1 is often difficult to meet because of cross-platform requirements, and unless your vim or Emacs, there's really no competing with BBEdit's history. [Bare Bones][barebones] as a company is up there with [The Omni Group][omni] and [Panic][panic] as far as the respect it has among Mac software enthusiasts.

[Sublime Text][sublime] is blazing fast, but it has a somewhat spotty development history and correct me if I'm wrong, it looks like it's created and maintained by a sole developer (Jon Skinner). Out of the box, as a Mac app, it's ugly as sin. You can customize it to look better, but that doesn't make everything else about it any more "Mac-like". Really the one true thing I love about Sublime Text is the way it does multi-word selection via `CMD+D`, and that's by no means a deal-breaker.

[Chocolat][chocolat] definitely hits points 1 and 3. Visually, it looks very nice, and while I've seen some users complain of its speed with some text files, it's fast enough on my machine and for my particular usage (I'm not editing any megabyte-or-larger sized text files). It doesn't currently have anything that makes me want to use it over BBEdit, however.

### Why I'm switching at all

I'm a developer, so I'm obviously switching "back" to BBEdit from something. Well in my case, it's two somethings. I'm a web developer by day (Backbone + Marionette) and my company's workflow is heavily dependent on [IntelliJ IDEA][intellij] (lots of servlets and such).  On my "own" time, I still do lot of contracting work developing [Corona][corona] apps, and for that I've been using Sublime Text (version 3 beta).

I want to change things for the following reasons:

1. IntelliJ can be dog slow on my machine. I use it for web development with a late-2012 Mac mini. It has a 2.3 GHz Intel Core i7 with 16 GB of DDR3 RAM and a 250 GB solid-state drive, so there's no reason why my development environment should ever feel like it's crawling. It does. Often. I even limit my number of open editor tabs to 10, and I followed all the optimization tips I could find. I want to use something faster than IntelliJ, period.

2. As previously mentioned, Sublime Text is fast. Really fast. But it's only used for some of my work. It's also jarring to have to switch between using two different editors. I want one programming environment to rule them all (even if I'm still bound to IntelliJ in some ways, more on that later).

3. I love BBEdit, and I miss it. I've been dying for a reason to dust off my license and make it my full-time text editor again. I used [TextWrangler][textwrangler] for a while back in 2010 to do all of my work at Ansca and then I purchased a BBEdit license when version 10 launched. I continued to use BBEdit for a while until I started working at [Lanica][lanica], where we used [Titanium Studio][tistudio] (Eclipse rebranded&mdash;yuck) and I eventually jumped onto the Sublime Text bandwagon based on recommendations from some colleagues. I began using it and got very used to it, but I never loved it.

So dust off my BBEdit 10 license I did, and I'm now using it as my full-time editor for all things programming (and writing for that matter, this blog post was happily written in BBEdit). How did I do it?

### Replacing IntelliJ with BBEdit

I have to use IntelliJ because of there are servlets combined with a Tomcat Run/Debug configuration we use at my company that are required for me to do my work. Once those are running, however, 100% of what I'm doing in IntelliJ is editing text. Why can't I use an external text editor of my choice and just have IntelliJ do it's thing separately without me needing to be _in it_ to do my actual work?

There's a big problem I ran into with this approach, however. If a file is modified outside of IntelliJ, it being a Java app (not a native Mac app), you have to click "Synchronize" on the toolbar (or `CMD+OPT+Y`) for it to pick up the changes (which it needs in order for the servlets to serve the proper stuff). I refuse to do that.

Every time I have a change I need to test in the browser, the last thing I want to do is click the IntelliJ window and "synchronize" before clicking away _again_ into the web browser. It's bad enough I already have to do that whenever I pull in changes from SourceTree (my Mercurial client of choice). My goal is to make my development environment more pleasant, not less.

Then, I remembered BBEdit's excellent AppleScript support. There's even an AppleScript menu, _and_ you can assign hotkeys to individual scripts. Perfect. The only problem is, I don't know AppleScript. Fortunately, a lot of folks on the internet do, so after some Googling, I was able to shamble together a script that does the following:

* Activate IntelliJ and invoke the keyboard shortcut to "synchronize" files.
* Put BBEdit back in front of IntelliJ, for easier access when I need to go back to programming.
* Launch and/or activate Google Chrome

So now I can do my programming in BBEdit, and when I'm ready to test my changes, I can simply invoke a keyboard shortcut that will synchronize the files in IntelliJ, and Google Chrome is activated (thus updating assets and resources due to "frame deactivation"). I'm all set.

Here's the AppleScript (bound to `CMD+OPTION+Y`, same as IntelliJ synchronize):

    -- Store reference to BBEdit in a variable, for later activation
    set currentApp to path to frontmost application
    
    activate application "IntelliJ"
    tell application "System Events"
        delay 0.1
    
        -- Invoke IntelliJ's keyboard shortcut for "synchronize"
        keystroke "y" using {option down, command down}
    end tell
    
    -- Give IntelliJ a couple of seconds to refresh files
    delay 2

    -- Put BBEdit back in front of IntelliJ
    activate currentApp
    delay 0.5

    -- Launch and/or activate Google Chrome
    tell application "Google Chrome"
        if it is running then
            activate
        else
            open application "Google Chrome"
        end if
    end tell
    
So with minimal fuss (an added keyboard shortcut to my workflow), I get to use a (much faster) text editor I'm very comfortable with. Reasonable trade-off.

### Replacing Sublime Text with BBEdit

So that takes care of my IntelliJ workflow. What about my work that I use Sublime for? That one's an even easier AppleScript. I just need it to launch/activate the Corona Simulator (also bound to a keyboard shortcut):

    activate application "Corona Simulator"
    tell application "System Events"
        -- Relaunch the Corona Simulator
        keystroke "r" using command down
    end tell
    
And that's it. Just two AppleScripts and my workflow completely lends itself to BBEdit.

### Favorite Features

Here are some of my favorite things about BBEdit (and yes, I'm well aware Sublime either has all of the following, or has a package that can do it, but I much prefer the BBEdit approach in overlapping features):

* This is one of the few text editors that has a default syntax color scheme I actually like (good thing too, because BBEdit's online color scheme selection is admittedly pretty weak).
* Awesome searching capabilities.
* Cmd + R symbol search, just like Sublime (meaning I don't have to get used to a different keyboard shortcut). I think this must have been added fairly recently (I'm using version 10.5.13 currently), because I don't remember this being available last time I used BBEdit around the time version 10.0 was released.
* Projects are easy to create and re-open.
* The AppleScript menu + custom key bindings to individual scripts.
* Very well-presented Preferences pane. No more editing a JSON file (Sublime), and no more dealing with IntelliJ's horrendous implementation.
* Scratchpad. I used to have to open a TextEdit window when I needed this functionality. Now it's built-in.
* Clippings.

### Wishlist

I'm pretty happy with BBEdit, but of course it doesn't have everything I could possibly hope for. I plan on submitting the following items as feature requests to Bare Bones, and if I'm lucky, maybe one (or more?) will be included in a future update:

* Per-project AppleScripts with their own keyboard shortcuts. Remember the AppleScripts I mentioned earlier? It would be nice to assign them both to the same keyboard shortcut, and have the correct script run depending on the project I'm currently working in.
* Multiple selection/cursors implemented _exactly_ as Sublime Text does it.
* Git and Mercurial as first-class citizens, on par with BBEdit's Subversion features (which I currently have no use for).

And that's really it. BBEdit is almost perfect for my needs, and I plan on sticking with it for the long haul. If you're in the same boat as me and want to switch to BBEdit but are tied to other tools, see if an AppleScript can't do most of the heavy lifting for you.

[^1]: Read more about its history on the [BBEdit Wikipedia page][bbedit-wikipedia].

[barebones]: http://www.barebones.com
[omni]: http://www.omnigroup.com
[panic]: http://www.panic.com
[sublime]: http://www.sublimetext.com
[chocolat]: https://chocolatapp.com
[intellij]: https://www.jetbrains.com/idea/
[corona]: http://coronalabs.com/products/corona-sdk/
[textwrangler]: http://www.barebones.com/products/textwrangler/
[lanica]: http://lanica.co
[tistudio]: http://www.appcelerator.com/titanium/titanium-studio/
[bbedit-wikipedia]: http://en.wikipedia.org/wiki/BBEdit