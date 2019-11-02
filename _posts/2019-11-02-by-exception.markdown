---
layout: post
title: "By Exception"
date: "2019-11-02 10:23:42 +0000"
---

Over the last few months I've been working to eliminate exceptional circumstances from the codebase and surrounding
processes. It's a simplification process, in essence, trying to reduce the cognitive complexity of the application's
building blocks and therefore the application as a whole.

When it comes to process there is always, correctly, a desire for lightweight process. However, I think the weight of a
process is more related to that cognitive load rather than the steps involved. What does it matter how many hoops are
being jumped through if all I need to do is press a button? If I need to know the hoops, I can read the code that's
linked to that button.

Lightweight process falls down when it's manual and more agreement than contract. If your process is "submit code
through PR unless it's small in which case just push it" then you have an exception to handle. How small is small? Can a
small change break the build?

Or perhaps you always get code reviewed and then merge to `develop` unless you're doing a release, in
which case manually reconcile the `master`/`develop` differences and bypass the review process. More exceptions and
cognitive load.

When I advocate for what some see as "more process", I'm really arguing for less thinking and more automation. I don't
want to follow a checklist, I want the checklist to be encapsulated in code and held in version control. It's the same
principle we apply to our code, keeping it simple and DRY.
