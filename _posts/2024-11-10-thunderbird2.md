---
layout: post
title: Thunderbird RSS Hack
---

Final Thunderbird post for a while, I promise

## The problem

So for my RSS reader, I use Thunderbird since I already use it for email and, like I demonstrate in my previous post, OpenPGP as well. I actually use it for CalDAV as well, all in all its a featureful organisation software.

The biggest flaw for me is the fact that settings cannot be synced between clients. So for example, since Thunderbird is on my desktop, when I add a feed to my reader on it, it doesn't show up on the Thunderbird on my laptop. Furthermore, what if I want to read on my phone? Do I need to maiantain 3 lists of the same thing manually?

One solution is a web based one. That is, your RSS feed sits on a server somewhere and you run a web application that lets you access it from anywhere with an internet connection and browser. In most cases however, this would require such a person to learn system administration, which while valuable knowledge serves as a significant barrier to entry. One could use someone else's instance, but in my search I found it really difficult to find anyone else offering this.

My solution was somewhat born out of an idea: what if we could apply Thunderbird's mail filters to RSS feed entries? I'm not really sure what I expected to happen, but apparently it was actually possible! Thunderbird seems to treat your entire "Blogs and News Feeds" section as one mail folder, and treats each incoming feed entry as an incoming email. Neat!

## The solution

We can use mail filters to move RSS entries as they come in to a specific subfolder in your mailbox.

> What? Can articles and blogposts really be uploaded to a mailbox?

Thunderbird appears to store feed entries as emails, or somehow converts entries to emails (with metadata becoming email headers) during handling of our rules. It strangely works, though you may see some missing info if you view it from another client like K9 Mail. Here are the rules. Recall that the message filter window can be opened by clicking the top-left hamburger menu then going to Tools -> Message Filters.

### On 'Blogs and Feeds'

![First set of rules](/assets/images/thunderbird/rules1.png)

Some email addresses are redacted for privacy, but really it should be the email address you want to upload the feed entries to. It first tags them as RSS, then moves them to your inbox.

> But why not move it to your 'RSS' subfolder directly?

We also want to mark all entries in our email copies of the feed items as read, while maintaining the 'unreadness' in our main reader. It would be annoying having to mark 2 entries as read every time you read an article, so we don't bother

### On Email Inbox

![Second set of rules](/assets/images/thunderbird/rules2.png)

Once an RSS tagged entry is detected, it marks the entry as 'Read' then moves it to the corresponding folder, without messing with any of the original feed entries. Neat! If you open this folder on another Thunderbird client, most of the metadata you are used to seeing like the "Website" tag is still there surprisingly, allowing you to read your feeds anywhere you choose.