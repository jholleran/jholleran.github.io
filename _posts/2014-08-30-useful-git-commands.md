---
layout: post
title: "Useful Git Commands"
description: "A list of useful Git commands when working with Git"
category: 
tags: [git]
---
{% include JB/setup %}


##Prints out the commit log history

**git log --oneline --graph --decorate --all**

	$ git log --oneline --graph --decorate --all
	* a9b9907 (HEAD, master) added tags
	*   accf567 (origin/master) Merge remote-tracking branch 'origin/master'
	|\  
	| * 265a68b Added a todo list
	* | 093da29 Added site description.
	* | 41662d1 changed copyright year in footer
	* | 0aa79b4 Fixed bug in page header
	* | 845ed47 configured details and changed index page
	* | 6ee414c Moved example posts to drafts
	* | 7383bea Changed to use new theme
	* | 0a52f59 Upgraded
	|/  
	* 330c932 Added post content
	* 342f8b2 Changed header and footer styling
	* 496e128 Changing base url


##Remove all untracked files from repo

**git clean -f**

This will remove all new untracked files that were added to the repo. After this command is run you will no longer be able to retrieve back the files. You can run the following command that will only print the file that will be removed with the -f flag.

**git clean -n**

##Revert a commit

**git revert \<commit\>**

	$ git log --oneline
	d563b11 added a new file
	ff80c82 a bug added in this commit
	ad186b0 first change

	$ git revert ff80c82
	[master f338fc5] Revert "a bug added in this commit"
	 1 file changed, 1 deletion(-)

	$ git log --oneline
	f338fc5 Revert "a bug added in this commit"
	d563b11 added a new file
	ff80c82 a bug added in this commit
	ad186b0 first change

The change set that was in included in commit ff80c82 has be reverted in commit f338fc5
