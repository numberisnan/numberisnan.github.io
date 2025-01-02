---
layout: project
title: UofT Weblogging and Homebrew Website Club
description: A website and RSS pipeline powered by Github Actions and Jekyll
---

This post should serve as some overall intuition for anyone who wishes to work on the pipeline/website since all the relevant repos and entities are loosely coupled. Heres a quick diagram that you should refer to as you read through the guide:

![Diagram](/assets/images/weblogging_club_diagram.png)

## rss-combine ([link](https://github.com/uoftwebloggingclub/rsscombine))

This repo periodically (currently every hour) does the following (in a container):

1. Fetches a list of RSS feeds from [here](https://uoftwebloggingclub.neocities.org/rss)
2. Fetches each of *those* RSS feeds
3. Combines them into a single megafeed (**Note: Not chronologically sorted!!!**)
4. Pushes the resulting feed as ```feed.xml``` to the [website's](https://github.com/uoftwebloggingclub/uoftwebloggingclub.neocities.org) root dir

This may be implemented in a much cleaner fashion in Ruby some day, but as long as we can get along with simple Go patches we will use the current code base. For development, I found the source code for the two feed libraries [gorilla/feeds](https://github.com/gorilla/feeds) and [mmcdole/gofeed](https://github.com/mmcdole/gofeed) quite useful, specifically the ```feed.go``` files with struct definitions for Feed and Item.

## uoftwebloggingclub.neocities.org ([link](https://github.com/uoftwebloggingclub/uoftwebloggingclub.neocities.org))

On push (and possibly periodically to reliably trigger holiday theming), the repo (in a container again):

1. Runs ```generate_feed_includes.rb``` on ```feed.xml``` to generate the ```_recent_feeds``` folder
2. Builds the Jekyll site
3. Uploads the whole thing to Neocities using an API token

### generate_feed_includes.rb

The purpose of this script is because, at the time of its creation, Jekyll did not support RSS or even XML parsing, which was needed to generate a list of recent articles on the website's main page/marquee. Ruby was chosen since it was already integrated in the Jekyll build environment, with dependencies addable by modifying the existing Gemfile. 

The script generates files ```1.html``` and so on, with RSS tags of interest converted to YAML frontmatter, and item content being dumped as the article content. These entries are sorted by the script chronologically, so the most recent entry will always be ```1.html```, and so on. 

For development, the documentation for [feed-normalizer](https://github.com/aasmith/feed-normalizer/) is essential, with [```lib/structures.rb```](https://github.com/aasmith/feed-normalizer/blob/master/lib/structures.rb) being particularly useful for dealing with Feed and Entry classes.

### runlocal.sh

This is the dev script. Note that this is meant for UNIX based systems, though I would imagine WSL would work fine. The dependency checks and call to ```generate_feed_includes.rb``` are self explanitory.

The flag system works by just passing flags to the script. For example, running ```./runlocal.sh browse``` will use ```xdg-open``` to open the browser to the local page. Neat! You can of course pass as many flags as you want.

The reason ```faketime``` is a dependency is because the script also allows us to test time-based holiday themes ahead of schedule. This can be done via flags too like ```./runlocal christmas```.