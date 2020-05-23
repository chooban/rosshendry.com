---
layout: post
title: "Untangling yarn dependencies"
date: "2020-05-23 12:09:09 +0100"
---

Keeping dependencies reasonably up to date is a good thing, right? Best not to let things languish and have a whole
bunch of hellish upgrades to do at once. I've had one hanging over my head for a while now, which I think I've finally 
solved, and it's led me to some fun with yarn and transitive, or indirect, dependencies. 

A package in our workspace uses ProseMirror and it's been stuck on one version for a while. Whenever we attempt to
update it we got an omninous runtime error that the <code>Schema is missing its top level node</code>. Try as we might,
we just couldn't figure it out. It was minor version bumps, the code was staying the same, everything looked good, but
it refused to work.

Debugging wasn't too difficult. By breaking on uncaught exceptions it was easy to verify that the object being inspected
for the top level node was indeed missing what was needed. In fact, what it was looking through was nothing to do with
what it wanted; it seemed to be looking through the object properties of a map, rather than the contents. Very strange.

Turns out our code was fine, it was a minor bump and everything worked just fine, so long as everything was updated at
once. Here's what I think went wrong;

ProseMirror has many packages which you can pick and choose from in order to build your editor, so your application may
end up with a number of PM packages in it dependencies. Some of the PM packages also rely on other PM packages. When
first installed, it looks like those indirect dependencies are locked down in the lockfile. So when I upgraded the
application's dependencies, yarn did its best to hoist the best version into place, but left conflicting versions
around. Somewhere in that tangle, we had versions that didn't work well together. 

According to a [long issue thread](https://github.com/yarnpkg/yarn/issues/4986#issuecomment-395036563), the fix is to
edit the lockfile to remove the entries to do with the offending package, then rerun `yarn`. At that point, it decides
that the latest package can satisfy all demands and only installs one.

I'm now going to be going through all `node_modules` directories in the workspace, trying to find out if any packages
that haven't been hoisted to the root are problems in waiting, thanks to indirect dependencies not updating.
