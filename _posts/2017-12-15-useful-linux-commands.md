---
layout: post
title: "Useful Linux Commands"
description: "A list of useful Linux commands"
category: 
tags: [linux,unix]
---
{% include JB/setup %}


##Running multiple commands in one command

To run multiple commands together in one single command add "&&" inbetween each command.

	$>/home/user/script1.sh &&
	/home/user/script2.sh &&
	echo "DONE"

This will run each command one after another