# Chromeos-Logs
Bugs from chromeos 

# Docs
https://docs.google.com/document/d/1OwQmhHgXSHYIVOWZ-SdAESnPzJn2sFt7y6L5EV2hqY8/edit?usp=drivesdk

# Logs

These are all reproducible!
## Log #1

Issue : Dev mode boot loop

Day : 2/12/2026
Time : 10:50 AM
Details : A boot loop of the recovery indicating “Your system is repairing”
Who : Me and my friend
Object : His Chromebook
Feelings after : This is way too easy to reproduce

### Log : 

I went into the recovery screen and did ctrl-d, this brought me to it being rejected, I then returned to secure mode and on the returning to vboot mode I did an EC reset. This brought me to the repair screen. After this I re-entered recovery mode and did ctrl-d once more, then I returned to secure mode, but it said it was being repaired. I proceeded to try entering the VT-3 shell (don’t ask why). The screen reset, I didn't know why, I thought it was my key binds, but it was unnaturally timed, I then removed my hands from the keyboard then discovered it kept boot looping. Saying “repairing” then closing the screen and reopening it to the same message over and over. I found out that re-entering developer mode or doing an EC or matter of fact any key bind that resets your chrome would lead to the same thing. This intrigued me because it could potentially be a brick or another way to unenroll. Currently, I am doing internet recovery (old) to prevent a Kernver update (I think).
After recovering with internet, I logged in and went through… enrollment… as normal, but when putting our password, we got the bug of “could not mount cryptohome”. Now I've gotten this before, but then I was a gigantic skid. I know now that “could not mount cryptohome” is a tpm error or such, which made me happy.

-LOG END

Problems : Infinite true boot loop, recovery might fix it.

What I hope to achieve out of this : An opportunity to bug out ChromeOS and bring forward code exec or such.

Extra : Honestly this was kind of funny, I guess it made me think, can I do this on my Chromebook ?






## Log #2

Issue : Weird powerwash

Day : 2/14/2026
Time : 6:30 PM
Details : Powerwash and revert option available in oobe and glitches when trying to use it
Who : Me
Object : My chromebook
Feelings after : Yeah ts is hard to reproduce, I was surprised a crosbreaker dev never saw that

### Log : 

Alright, to start. After messing around in recovery mode for like a good 30-45 minutes I exited and went back to OOBE. I wanted to try sh1ttyexec on v144 k7 (I know ok? Don't question my antics) I proceeded and it didn't work, so I went to the recovery screen and did a devmode powerwash. After that I went back to secure mode and tried a standalone powerwash, one remark was my ability to powerwash and revert, I was quite intrigued because it wasn't in my book to see something like this. Normally you’d only be able to powerwash and revert while in demo mode. Next best thing? Try it, and that followed quite unexpectedly too, ngl it took a while to actually “powerwash”. Once it was gonna powerwash and revert I was told that an error had happened and it just couldn’t? The button following this error was just a cancel so I retried to powerwash and revert and it worked, surprisingly… Oh you know I was kinda hoping this meant something broke and my incessant messing with recovery mode caused it. Steps to reproduce are literally unknown to me, mb gng.

-LOG END

Problems : Powerwash does not fully complete and returns to a partially broken OOBE state

What I hope to achieve out of this : Honestly at first I was hoping this would be it but, nah, my first thought were that this could hopefully render OOBE in an incomplete state and allow further bugs to occur

Extra : This felt less shocking and scary than the boot loop but somewhat more promising, having this happen to me felt like a wake up call. After so long chromeos gave out and gave me another bug (like 2 days apart 💀)




## Log #3

Issue : Ui freeze ?

Day : 2/14/2026
Time : 9:46 PM
Details : ChromeOS ui just gave out on me and became completely unresponsive
Who : Me
Object : My chromebook
Feelings after : Never in a million years will this happen again (It did literally the next day)

### Log : 

Ok, this one's gonna be really short because there isn't much to talk about. While messing in recovery mode, I entered internet recovery (old) and somehow, someway the entire ui just froze and became unresponsive. Now this is probably your typical ChromeOS bug. I was actually worried when trying to reenter recovery mode (via keybinds) didn’t work. Doing an EC reset sealed the deal tho. Now to reproduce this would be to pray for 100k to appear on your bed, this is completely random and mostly has nothing to do with my shenanigans. Simply a visual bug right? Well not quite, I opened the debug logs and found out my TPM had failed?! 1/200 lol… well that was quite the revelation I don't really think that was just a normal ui freeze tho I couldn't tell much more about it. 

-LOG END

Problems : Total UI freeze, required a measly EC reset.

What I hope to achieve out of this : For the actual bug I was just shocked but there wasn't much I could build off of, most of the keybind did absolutely nothing, the only one working was EC reset. But for the second part of the TPM failing that made me smile and now I hope this “revelation” reveals any possible exploit.

Extra : This literally was only a 3 hour difference from my last encounter, I am really a magnet for troubles huh? I wonder what happens when the TPM reaches 200 failed tries 🤔
I saw on reddit some guy got absolutely cooked after 200 tries 😦









## Log #4

Issue : Managed Icon crashing

Day : 2/15/2026
Time : 6:15 PM
Details : When clicking the managed by (school) icon it crashes and loads after ~1s
Who : Me
Object : My chromebook
Feelings after : Pretty cool, has a few results that can happen from this

### Log : 

Ok my first feelings about this was like… just a simple crash. But when repeated multiple times it can give a variety of results, like when you do it a lot of times it might stay fully black and the screen just doesn't respond but the backlight stays on. Another might be when it does an ec reset, somehow… Well I figured this out a long time ago but I brought it up now and now I'm logging it! Since there isn't much to talk about this “bug” , I'll cut to the part where I explain how to reproduce. This has a 100% consistency to get to it, first is to do the first part of sh1ttyexec on a newer version (144≥) specifically the powerwash part. If done correctly there shouldn't be any managed by icon at first glance. But if you look in the bottom right corner and press the menu, the managed by… icon should appear. This icon is really buggy, because if you press it then it would crash and appear a few seconds later. If repeated a few times, varying results can occur.

-LOG END

Problems : This isn't really a problem other than when the ui stays closed and it's just the backlight (until your screen closes naturally)

What I hope to achieve out of this : I honestly just wanted to log this for fun, but If repeated even more times it could give more results.

Extra : This is neat. I love finding small insignificant bugs like these, like each day is something new to log










## Log #5

Issue : Special Enrollment error

Day : 2/16/2026
Time : 8:43 PM
Details : Unknown error caused by ruining oobe
Who : Me
Object : My chromebook
Feelings after : Literally no use and not even a bug lol, ok maybe.

### Log : 

Yeah this is not even a bug, well why not talk about it? First of all this is basically incorporating the personal account feature and the first part of sh1ttyexec. Actually, do log 4 to get here. So this was kinda cool. I was hoping to get more out of it, but who am I kidding literally nobody ever saw this bug. Welp.. steps to reproduce, first powerwash then get to the get started screen. After that, powerwash (don't actually)  right when it says enrolling. If done correctly you enter the bugged oobe, steps after that is to enrol again but disable wifi right as it says enrolling, this is very hard to do and has a short window of time, to restart just click the managed icon. If done correctly you can now go to a personal account. Do that and enroll with your personal account and the bug should appear !

-LOG END

Problems : Uh I guess not being able to enroll onto a personal account?

What I hope to achieve out of this : When the idea came to mind I was like what if this lets me bypass whatever they put, by confusing the enrollment because I was already enrolled

Extra : Pull some stuff from log 4 and boom, the error margin is actually small lol.
