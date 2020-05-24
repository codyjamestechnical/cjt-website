+++
categories = ["Mac OS"]
date = 2020-05-21T16:43:24Z
description = "Tips and useful extension to make Finder in Mac OS more useful."
featuredImage = "/images/screen_shot_2020-05-21_at_1-41-48_pm.jpg"
hiddenFromHomePage = false
lastmod = 2020-05-21T16:43:24Z
lightgallery = true
subtitle = ""
tags = ["Tips & Tricks", "Mac OS", "Finder"]
title = "Finder Tips & Extensions"
toc = true

+++
<!--more-->

### Highlight Temporary Data

Temporary files such as app downloads, receipts, and screenshots have a way of multiplying in number super fast. Yes, you need to keep them for a while, but they often get in the way. Mark such future junk files with a _temp_ (“temporary”) tag.

{{< image src="/images/finder-temporary-tag-670x340.jpg" caption=""  src-l="/images/finder-temporary-tag-670x340.jpg" linked=true  >}}

### Highlight Task-Related Data

Setup an "_Action_" tag for files that need relatively quick action. Like renaming, sharing, organizing, and the like.

### Install Quick Look Extensions

#### Markdown Preview

Install [QLMarkdown](https://github.com/toland/qlmarkdown) extension:

```shell
brew cask install qlmarkdown
```

To enable text selection in [QLMarkdown](https://github.com/toland/qlmarkdown), run:

```shell
defaults write com.apple.finder QLEnableTextSelection -bool TRUE; killall Finder
```

#### Video Thumbnail Preview

[QLVideo](https://github.com/Marginal/QLVideo) adds support for more video types.

```shell
brew cask install qlvideo
```

#### Add Support for More Text Files

[QLStephen](https://github.com/whomwah/qlstephen) will allow quick look to show more file types.

```shell
brew cask install qlstephen
```