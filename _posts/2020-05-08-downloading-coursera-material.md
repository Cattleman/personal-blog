---
toc: true
layout: post
description: blog_post
categories: [markdown]
title: Downloading Coursera Learning Material
---


# Downloading Coursera Learning Material


## Coursera Power User

I've been taking a ton of Coursera courses focuses on GCP during the lockdown. 
I really appreciate all the material that Coursera provides including pdfs, transcripts and of course all their videos. 
However, I was getting anoyed that I had to download each transcript one at a time and thought there must be a better way!?

## `coursera-dl` - There is a better way!

[coursera-dl](https://github.com/coursera-dl/coursera-dl)

**Coursera-dl** is a quick cli to help semi-automate downloading all the course material at once!

## Steps
1. `pip install coursera-dl`

2. **In your browser navigate to where your cookies are stored.**

**For Chrome:** 

 To navigate to this you can paste this in your brower: [chrome://settings/siteData](chrome://settings/siteData)

Settings > Privacy and Security > site settings > Cookies and site data > See all cookies and site data > Coursera.org

You will see: `CAUTH` listed, you will need the content later
<br>

3. **Quick bash script**

`coursera-dl` has many arguments. `--help` and look at what you might want.

I only wanted the transcripts/ txt and pdfs so I used the `--ignore-formats mp4` argument to ignore the videos. 

you can make a bash script by copy/paste this into a file like: `coursera_material_download.sh`

You will need to populate the various arguments. 

```
#!/bin/sh
# Quick script to grab course materials
​
​
USER=<COURSERA_USERNAME>
PASS=<COURSERA_YOUR_PASSWORD>
​
CAUTH=<your cookies for coursera>

COURSES=<course-name-from-URL>
​
# ignore the videos
coursera-dl -u $USER -p $PASS --ignore-formats mp4 -sl en -ca $CAUTH $COURSES

```

**To run it:** 

```!Bash
$ coursera_material_download.sh
```
