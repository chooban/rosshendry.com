---
layout: post
title: Tagging a docker image on CircleCI
date: 2018-03-07 17:42 +0000
categories: docker node
---

Today's lesson is on tagging and versions. I wanted to be able to automatically increment the version number
of a node project when I push to master, and have that tag be used when building and pushing the updated
Docker image.

My idea was that I'd change the package file manually, push it up, get Circle to read that and tag accordingly.
Turns out that reading the current version number isn't really a thing in either `npm` or `yarn`, unless you
want to start using grep.

Instead, I went with using [`npm version
patch`](https://github.com/chooban/ace-previews-api/blob/master/.circleci/config.yml#L17) and a read/write
deployment key to get those changes back into github.

Not quite there yet, as this has led to an infinite loops of pushing to master, getting notified of a change,
incrementing the patch number, pushing to master, and so on.

Luckily, there is a [very handy](https://circleci.com/docs/2.0/skip-build/) option to skip a build. All is well again.
