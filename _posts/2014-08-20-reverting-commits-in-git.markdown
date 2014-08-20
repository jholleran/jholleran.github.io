---
layout: post
title:  "Revering commits in Git"
date:   2014-08-20
categories: git tips
---

Git revert undoes a single commit. It does not revert back to a previous state of the project by removing previous commits. In git this is called reset.

If you have published work to your origin, you probably don't want to reset the branch since that is effectively rewriting history. In this case you will want to revert the commits. This will create new commits that will reverse the unwanted commits. This way the history is not rewritten.


{% highlight text %}
git revert <commit>
{% endhighlight %} 


#Revert vrs Reset

{% highlight text %}  
     Reverting  
         ----------↘ 
 (A) - (B) - (C) - (B-)

 B- is a new commit that reverses the changes in B commit
{% endhighlight %} 

{% highlight text %}  
     Resetting  
               ↙--- 
 (A) - (B) - (C) - (D)

 D is now removed
{% endhighlight %} 

#Reverts the last two commits
git revert HEAD~2..HEAD

#Reverting a merge commit
git revert -m 1 <merge_commit_sha>