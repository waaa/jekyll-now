---
layout: post
title: Installing SubGit
date: 2016-07-15
---
This story is based completely on a personal experience of somebody quite dumb who’s tried to install SubGit and succeeded. 
It all began when I’ve decided to stop being oldschool and desired to move my humble Python project from SVN to Git. I heard about SubGit so I googled.

![Picture 1]({{ http://waaa.github.io }}/assets/google.png)

All in all I really liked this website. It looked fun to me and didn’t seem too complicated a story.

![Picture 2]({{ http://waaa.github.io }}/assets/website.png)

I wandered around a bit and found myself on a ‘Download’ section. It says there.. download.. unzip.. configure.. and it looked like that’s it. So all ready for a new adventure I’ve pressed ‘Download’ and soon enough I’ve got it, as it’s not that big a file.

![Picture 3]({{ http://waaa.github.io }}/assets/download.png)

I have to mention here that I’m using OS X. So ‘unzip’ part happened without me taking action as soon as download was finished. So I’ve got this directory inside my ‘Downloads’ directory (my IT friends’re saying that I can’t say 'folder' anymore it’s considered unprofessional! So pleasing them I’m going to use ‘directory’ word all over this article, if I do otherwise, please complain!).
Next thing I know I’m opening Terminal and doing:

    sudo mv ~/Downloads/subgit-3.2-2.0 /etc/

and then:

    sudo ln -s /etc/subgit-3.2-2.0/bin/subgit /usr/local/bin/subgit
    chmod +x /etc/subgit-3.2-2.0/bin/subgit

The first command created symlink from **/usr/local/bin** to my SubGit executable file, and the second command actually granted this file a right to be executed.

So now I’ll present to you my SVN repository. It lives by the address http://188.213.173.182/svn/test. You can’t see it because you don’t have a password. But trust me it’s there! For as long as I’m paying the server fee..
Now when you know where this link leads, you’ll understand the significance of a following command:

    subgit configure --layout auto http://188.213.173.182/svn/test test_git_repo.git
    
Basically it says to SubGit to connect to my SVN repository and using standard **auto** layout create for it a **test_git_repo.git** repository just there, where the command is being executed.

And an error had occurred! It said:

    SubGit is not compatible with this version of Java!
    Java version found         : 1.6.0_65
    Java version required      : 1.7 or newer

A bit of googling took me to the Oracle website, to be precise <a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html">here</a>.
So I’ve choosen the only Mac version there was:

![Picture 4]({{ http://waaa.github.io }}/assets/macversion.png)

I downloaded and installed that as a normal OS X application using graphic interface.
After repeating **subgit configure** command it asked me for the password of my SVN repository and then.. yay!

![Picture 5]({{ http://waaa.github.io }}/assets/configsuccess3.png)

It said in the output that I could play around with my branches mapping in the main SubGit config file, which lives at **test_git_repo.git/subgit**, the repository that has been just created by **configure** command.
But I don’t need to do that at this point, I have only trunk at my SVN repository so far.
Then it said I need to put my credentials to the **passwd** file that stays at the same **subgit** directory, which I did, but I’m not going to post a screenshot here! It’s pretty simple, just a name, couple of spaces and your SVN password.
There was also something about adding authors there, but honestly nobody wants to commit to my repository apart from me, so I didn’t touch this one.

And at last! I ran the **install** command:

    subgit install test_git_repo.git

Once again, I’m the happiest girl in the world!

![Picture 6]({{ http://waaa.github.io }}/assets/installsuccess.png)

The next thing on is to figure out how does it all work. I'll keep you posted:)

 
