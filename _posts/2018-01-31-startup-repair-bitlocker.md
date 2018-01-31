---
title: Fixing a Machine stuck in Startup Repair with Bitlocker
date: 2018-01-31 00:00:00 Z
categories:
- tech
tags:
- stories
layout: post
section-type: post
---

I work on computers on daily bases.  I was extremely suprised on how many machines came back in for the startup repair at the office.  A lot times it would require us to reimage Windows.  However, I found this solution out and has saved me a lot of time in the process.  It mixture off stuff that I do, but the sucess rate is fairly good. 

1.	Boot into Advance Options > Click Command Prompt

2.	Type Diskpart, then press Enter

3.	Type List Vol, then press Enter

4.	Find which Volume contains Windows on it and Remember the Drive Letter

5.	Type exit to exit diskpart

6.	Type manage-bde -unlock *DRIVE LETTER*: -recoverypassword YOUR-BITLOCKER-RECOVERY-KEY (you can skip this step if you already put recovery password in blue screen window)

7.	Type manage-bde -protectors -disable *DRIVE LETTER*:

8.	Do the following command by typing each one. one by one.
	    Bootrec /fixmbr
        Bootrec /fixboot
	    Bootrec /rebuildbcd

9.	Type Copy *DRIVE LETTER*:\windows\system32\config\RegBack\* *DRIVELETTER*:\windows\system32\config

    Note use the Drive letter that you were using above.  

10.	Type all

11.	Type chkdsk /f *DRIVE LETTER*:

11.	Type exit

12. Turn off windows 10.
