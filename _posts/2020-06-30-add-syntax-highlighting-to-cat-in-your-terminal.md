---
layout: post
title: Add syntax highlighting to 'cat' in your terminal
date: 2020-06-30 10:31 +0100
category: Tech
---

I use my terminal everyday, and frequently I am way faster with it then navigating around with my mouse in Finder.

Within your terminal the `cat` command is very useful to quickly peek inside a file, but when you're looking at source code, this is a bit difficult to read. I just thought "_Wouldn't there be syntax highlighting for my terminal?_". As it turns out, there is. 🎉

## How to set it up

* With [Brew](https://brew.sh/), install Pygments: `brew install pygments`
* Next, add the following to your .zshrc/.bashrc file: `alias cat="pygmentize -g"`
* Open a new terminal window, or source your .zshrc file: `source ~/.zshrc`

Now, when you e.g. run `cat Dockerfile` on a Dockerfile, things look very neat!
