---
layout: post
title: Installing SubGit
date: 2016-07-15
---

This story is based completely on a personal experience of somebody quite dumb who’ve tried to install SubGit and succeeded. 
It all began when I’ve decided to stop being oldschool and desired to move my humble Python project from SVN to Git.
First thing I did? I googled.

<screenshot with google outcome>

First thing I’ve got was this website. It looked fun and it didn’t look too complicated a story.

<screenshot with a part of site text>

I wandered around a bit and found myself on a ‘Download’ section. It says there.. download.. unzip.. configure.. and it looked like that’s it. So all ready for a new adventure I’ve pressed ‘Download’ and soon enough I’ve got it, as it’s not that big a file.

<screenshot with download bar finished>

I have to mention here that I’m using OS X. So ‘unzip’ part happened without me taking action as soon download was finished. So I’ve got this directory ( my IT friends’re saying that I can’t say folder it’s dumb! So pleasing them I’m going to use ‘directory’ word all over this article, if I do otherwise, please complain!) inside my ‘Downloads’ directory.
Next thing I know I’m opening Terminal and doing

    sudo mv ~/Downloads/subgit-3.2-2.0 /etc/

and then

    sudo ln -s /etc/subgit-3.2-2.0/bin/subgit /usr/local/bin/subgit
    chmod +x /etc/subgit-3.2-2.0/bin/subgit

The first command created symlink from /usr/local/bin to my SubGit executable file, and the second command actually granted this file a right to be executed.

So now I’ll present to you my SVN repository. It lives by the address http://188.213.173.182/svn/test. You can’t see it tho because you don’t have a password. But trust me on that one, it’s there! Until I’m paying the server fee..
Now you know what this link is, you’ll understand the significance of a following command:

    subgit configure --layout auto http://188.213.173.182/svn/test test_git_repo.git

And an error had occurred! It said:

    SubGit is not compatible with this version of Java!
    Java version found         : 1.6.0_65
    Java version required      : 1.7 or newer

A bit of googling took me to the Oracle website, to be precise <a href=http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html>here</a>.
So I’ve choosen the only Mac version there was,

<screenshot of Mac version>

downloaded and installed that as a normal OS X application using graphic interface.
I repeated ‘subgit configure’ command, it asked me for the password of my SVN repository and then.. yay!

<screenshot installation successful>

It said in the output that I can play around with my branches mapping in the main SubGit config file, which lives at ‘subgit’ directory of the test_git_repo.git that had just been created by ‘configure’ command.
But I don’t need to do that at this point, I have only trunk at my SVN repository so far.
Then it said I need to put my credentials to the ‘passwd’ file that stays at the same ‘subgit’ directory, which I did, but I’m not going to post a screenshot here! It’s pretty simple, just a name, couple of spaces and your password to SVN.
There was also something about adding authors there, but honestly nobody wants to commit to my repository apart from me, so I didn’t touch this one.

And at last! It said to run the ‘install’ command.

    subgit install test_git_repo.git  
		
Once again, I’m the happiest girl in the world!

<screenshot installation successful>

The next thing on my plan is to find out how exactly does it work! I’ll keep you updated..:)

 
