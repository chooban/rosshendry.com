---
layout: post
title: Operational Changes
date: 2019-10-20 15:00 +0000
categories: development
---

I've learned a lot in the 18 months since I started messing a little bit with CircleCI. Back then, I wrote [a quick
post](/devops/2018/03/08/circle-ci-workflows.html) about getting a few jobs running in parallel on a personal project.
Since then, I've taken my interest in automation further and implemented a CI/CD pipeline that involves parallelised
test runs, browser testing, and code analysis.

Humble and Farley's [Continuous
Integration](https://www.amazon.co.uk/Continuous-Delivery-Deployment-Automation-Addison-Wesley/dp/0321601912) book has
been on my to-finish list for a while, but that's mostly because every time I pick it up I find something new to
re-engineer for efficiency. There are still parts of the pipeline that I'd like to overhaul; there's repetition in there
that I'd like to eliminate, test runs to analyse for better parallelisation, and custom containers to be built.

We'll be starting on some new projects soon, and my plan is to ramp up use of [Terraform](https://www.terraform.io) at
this point. If we do it right, no-one should need to copy and paste any database URLs , and we should
be able to encapsulate all the configuration in version control.
