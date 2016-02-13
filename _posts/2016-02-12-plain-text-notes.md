---
layout: post
title: "Plain Text Notes"
date: 2016-02-12 19:48:00 -0800
updated: 2016-02-13 10:15:00 -0800
---

After bouncing between various note-keeping apps, I finally settled on a very simple solution that is flexible, cross-platform, freely available, and will surely stand the test of time: plain text.

<!--more-->

Journal entries. Recipes. Work log. Grocery lists. Things I need to quickly pull up on my phone when I'm on the go. Ideas for gifts I want to buy my wife and kids. Anything, and everything. Digital notes have been an absolutely essential part of my personal and professional life. What I use to *manage* the notes essentially serves as my secondary brain[^1].

Without putting a lot of thought into it initially, I started out using the stock Notes app on iOS and the OS X, which worked until I took a [detour]({% post_url 2015-07-11-my-desktop-july-2015 %}) into the land of Linux[^2] and it suddenly became annoyingly painful to access my notes[^3]. In my frustration, I began thinking about my mobile needs. If I were to move away from iOS in the future, even if temporarily (be it Android or something else), what would I do then? I often need to access my notes when I'm on the go, so this was a big concern.

It was clear that I needed a cross-platform solution that could withstand my (admittedly erratic) computing habits over time. I don't think vendor lock-in is an acceptable option for me.

## Runner-ups

### Evernote

[Evernote](http://evernote.com) was the first contender, but I ultimately decided against it because, like Apple Notes, it stores notes as [Rich Text](https://en.wikipedia.org/wiki/Rich_Text_Format). I really dislike WYSIWYG[^4] editing, and that is the bread and butter of Evernote. Not necessarily a bad thing, but not for me. I'll admit that being able to embed media and adding attachments to notes is really nice though.

### Simplenote

[Simplenote](http://simplenote.com) was next in line, and I almost went with it as it was very similar to what Apple offers, but notes are plain text and the service is cross-platform due to being web-based. However, there were some concerns that kept me at bay.

**3rd-party app selection**. I don't like being tied to the web app[^5] and wasn't completely happy with the available 3rd party clients (I did like the first-party iOS app, however). There is a [script](http://fletcherpenney.net/other_projects/simplenotesync/) that can be used to sync notes to a local folder, but I didn't really want to have to go through that, and more importantly, I wasn't confident enough that the script wouldn't wipe my notes on accident, or be maintained long enough to withstand any API changes that Simplenote might introduce in the future.

**Limited ways to organize my notes**. I really want better organization for my notes, such as a "Work" folder for work-related notes, a "Journal" folder for journal entries, and so on. I know I could use tags instead of folders, but that leads me to my next point...

**Is it future-proof?** What happens if Simplenote shuts down before I no longer need to keep notes (in other words, before I die)? Simplenote *does* have an export option, but it gives each note a crazy, random filename and the tags don't seem to be preserved (there goes any work I put into tag-based organization).

Evernote was pretty great about being able to organize notes into separate "Notebooks", and I'm sure there are other services that do something similar, but the other two points mentioned could easily apply to just about any third-party note-keeping service.

The thought of relying on my chosen note-keeping service to outlive me makes me a little uncomfortable, so the only remaining option seemed to be manually handling the notes myself via locally saved, old-fashioned plain text.

## The Setup

All of my notes live in a single, top-level folder on my computer's hard drive. I have sub-directories for Work, Personal, Journal, Projects, Media and Attachments. The notes themselves are just plain text files, saved as [Markdown](https://daringfireball.net/projects/markdown/).

### Sync and backup

Since I need to be able to access my notes from multiple devices (my laptop, desktop, and phone), syncing is a huge requirement for me. I already use [Dropbox](http://dropbox.com), so my top-level "Notes" folder lives in my Dropbox folder. Any changes I make to notes are automatically synced (and backed-up online).

If Dropbox ever goes away, or I want to stop using it, I can just turn my notes folder into a [Git](https://git-scm.com) or [Mercurial](https://www.mercurial-scm.org) repository and host it privately on [GitHub](http://github.com) or [Bitbucket](http://bitbucket.org). I'm tempted to go this route *now* for the ability to track changes and revert notes to an older state (if necessary), but what's holding me back from this approach is mobile. While there are many great mobile apps for viewing and editing Markdown files in a Dropbox folder, I haven't yet found the same for a hosted repository[^6].

### Editing and viewing

This is where "everything as plain text" really shines. I spend most of my day in a text editor ([BBEdit](http://www.barebones.com/products/bbedit/)), so it's just comfortable for me to edit my notes in the same app. BBEdit also has a nice Projects feature, so all I need to do is open *Notes.bbprojectd* and all my notes are there, nicely organized in the sidebar. I can now take advantage of BBEdit's robust search capabilities for all of my notes, which is a huge plus.

As far as mobile goes, all I needed was a text editor that could link to Dropbox. I'm pretty happy with [iA Writer](https://ia.net/writer), but there are other options as well (some of which are free). My requirements for mobile aren't that extensive, however, as I rarely do any significant editing of notes on my phone, but I often need to view them.

### Media and attachments

This is something that was good about Evernote, and is surprisingly easy to duplicate with my current setup. In my top-level folder, I have sub-folders for Media and Attachments. Since I save my notes as Markdown, I can easily embed images and links as I would when writing a blog post.

    ![My Image](../Images/2016-02-12-my-image.jpg)

In fact, if I really want to get fancy, I could turn my notes into a private [Jekyll](https://jekyllrb.com) blog, but I digress (that's probably overkill anyway). In any case, BBEdit has a Markdown previewer (as well as iA Writer), so I can just use the built-in viewers when I want to see embedded media and links.

All in all, this plain text setup has been working out really well for me, and I don't feel like I'm missing out on any features by not going with a dedicated app or service. If you're in search of a note-keeping service, or feel like a change, I recommend giving the plain text approach a shot!

[^1]: Although, having a "second brain" doesn't seem to make me any smarter for some reason. Weird.

[^2]: It was a short detour. I'm back on OS X now.

[^3]: No, [iCloud.com](http://icloud.com) doesn't do it for me. Does that site even work on Linux browsers?

[^4]: WYSIWYG = "What you see is what you get"

[^5]: I'm a web developer, but for something I access and use as frequently as my notes, I like to have a dedicated app with a first-class dock icon on my Mac.

[^6]: It occurs to me that in the meantime, I can still use Git or Mercurial for my notes while still on Dropbox. Noted!
