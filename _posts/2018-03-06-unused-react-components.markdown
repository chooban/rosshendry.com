---
layout: post
title:  "Finding unused components in a React project"
date:   2018-03-06 08:12:32 +0000
categories: programming react
---

I've been doing some refactoring of a React project and inevitably some of the components will no longer be required.
Having been used to Java IDEs highlighting these issues for me, I wasn't sure how to go about automating the process of
finding unused files.

There are a couple of webpack plugins available for doing just this:
* [unused-files-webpack-plugin](https://github.com/tomchentw/unused-files-webpack-plugin)
* [unused-webpack-plugin](https://github.com/MatthieuLemoine/unused-webpack-plugin)

The first gave me a list of all files in the project, which isn't so helpful. I imagine all I needed to do was configure
an entry point for it, but a quick switch to `unused-webpack-plugin` gave me what I needed.
