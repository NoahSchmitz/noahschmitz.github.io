---
layout: post
published: false
title: Weirdness in Windows 10
---


## This Is Why We Use Linux. 
 
Recently for kicks and giggles I installed Windows 10. I was pleasantly surprised with a much more desktop oriented system (compared to 8) and a few nice features Windows has been lacking (like multiple desktops). 
 
However, since the product was made by Microsoft, there is some weirdness. When you open file explorer it is supposed to take you to the "Home" screen which looks something like this: 
 
![Not Too Bad I Suppose](http://winaero.com/blog/wp-content/uploads/2014/10/windows-10-libraries-in-Home-folder.png) 
 
But for some reason mine looks like this after the latest update: 
 
![Fail.PNG](/_posts/Fail.PNG) 
 
I don't _think_ I did anything to break it, but broke it is. After messing around in the registry trying to get something (or anything) to show up in my home, I gave up. I never use the "Home" anyway. However it was really annoying having it default to something useless. 
 
##This Is Where Things Get Complicated 
 
So I set out to have it default to "This PC" which is slightly more usefully than my empty "Home" 
 
###NOTE: DO NOT do anything I do past this point if you are worried about messing with things that shouldn't be messed with. That being said, Windows 10 is in beta anyway, so lets mess with stuff! 
 
I typically launch Explorer from the Start Bar (not to be confused with the screen or Menu) It is always visible, and very convenient. So _technically_ I should just be able to change the shortcut on my bar right? 
 
![properties.png](/media/properties.png) 
 
Nope. 
 
![Failure.PNG](/_posts/Failure.PNG) 
 
For some unfathomable reason, Microsoft has made the box I need unclickable (the Target box) 
 
Well what if I just remove that and make my own that I then re-pin? 
 
I just make a shortcut

![Shorty.png](/_posts/Shorty.png)
 
and point it at:

![Dat Link.png](/media/Dat Link.png)

>C:\Windows\explorer.exe shell:::{20D04FE0-3AEA-1069-A2D8-08002B30309D} 

^That madness is just a fancy way of linking right to "This PC"^
 
and pin that to my bar! 
 
##Success? 
 
Well. No. For some reason every window you spawn of that link will open up (correctly) bot they won't do that usefully stack thing. Instead, it opens up next to all you pinned apps, and any other windows opened (from that icon) will obviously take you "Home" 
 
##This Is Where Things Get Really Complicated 
 
I went back and looked at the properties of the original shortcut a little better and you can see (I can't show pictures of this bit because I already messed with it) that the shortcut doesn't just link to Explorer.exe (as one would assume) but rather to: 
 
>C:\Users\Noah\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\System Tools\File Explorer.lnk 
 
A link that links to a copy of itself? um. wat? Upon deleting that link it seems to instead link to another copy here: 
 
>C:\Users\Noah\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\StartMenu\File Explorer.lnk 
 
At this point I really don't understand what black magic is happening, but I intend to purge it from my system. 
 
So I deleted both of those two .lnk files (the .lnk may not show, but that's what they are) and I replaced the one in: 
>C:\Users\Noah\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\System Tools\ 
 
With my own "File Explorer.lnk" (that shortcut I made before). I can now pin that to my bar and everything seems to be working (as of writing this) 
 
Comments, Questions, or Criticisms? Put it in the comments. 