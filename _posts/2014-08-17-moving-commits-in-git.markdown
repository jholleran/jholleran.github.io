---
layout: post
title:  "How to move last commits to between branches in Git"
date:   2014-08-17 12:45:48
categories: git tips
tags : [tutorial, git]
---

If you have accidently made commits onto a branch and now want to move them commits to a new branch or and existing branch here is how to do it.

#Scenario
Here is an scenario where we have made three commits onto master but now want ot move them last three commits on to a new branch.
{% highlight text %}
Go from:
master A - B - C - D - E

To:
newbranch      C - D - E
             /
master A - B
{% endhighlight %}


#Moving commits to a new branch
First create a new branch. The new branch will now point to latest commit (E). Then reset the original branch back to the original commit (B). Then change on to the new branch. The C, D, & E commits are now only on the new branch.

{% highlight text %}
git branch newbranch
git reset --hard HEAD~3 # Go back 3 commits. You *will* lose uncommitted changes
git checkout newbranch
{% endhighlight %}


#Moving to an existing branch
The C, D, & E commits will first need to be moved onto the existing branch. To do this checkout the existing branch and then merge the changes from the master in to the existing branch. Then reset the master branch back to commit B. The C, D, & E commits are now only on the existing branch.

{% highlight text %}
git checkout existingbranch
git merge master
git checkout master
git reset --hard HEAD~3 # Go back 3 commits. You *will* lose uncommitted work.
git checkout existingbranch
{% endhighlight %}


** Be very careful with the git reset --hard command as you can lose work **