# Basics

## [Editor](http://ledoux.io/bitsy/editor.html) ****

![](../../../.gitbook/assets/bitsy1.png)

* **Top**: Edit the name of your Bitsy project
* **Room:** The level editor which your player will move in.
* **Preview:** A preview of the code, triggered by clicking **play** or ticking **Auto-refresh**. It is possible to change the size of this window by hovering just where the code and preview meet, then click-and-drag.
* **Colors**: Bitsy uses only 3 colors; Background, tile and sprite, but can have multiple palettes.

All windows can be rearranged and closed. Click on Tools to see a list of windows available! Hovering over anything brings up a description.

In the **room** window, hit the play button. You should be able to move the character around with the arrow keys. Walk over to the cat!

![](https://lh3.googleusercontent.com/9wId48Ut16eMSSqX4phjeNIcgySVJMsVfLTFBHqMnEOJ1TirfrqzVKS3pt4TMo1z6PVE9pTZzkwl9IvTxDg7d0MAPd_Hwo6YtYx-zxUyqkvxxBXQ7vFdSYI8na1R2G3BCf8Hmwuo)

{% hint style="info" %}
This is currently a heavy copy & paste from a [guide](https://docs.google.com/document/d/11pfwuJ8GR1RViwL1nkvbD7pEqokDH9RLtamzxrsJuEc) written by [Everest Pipkin](https://twitter.com/everestpipkin).
{% endhint %}

## Dialog

![](https://lh3.googleusercontent.com/CpMZa8VTqGZeiLjNruEdWxJEJr3Dd9XT9D52rX9gvJrurXGjX4W7Cz3Qza1VkNC78yAu2rPXoq59Eax2Elp9Br9-Jz_ZHOauSZQvKfYrj9CJVIlgl2_jOXjlsBwrlKgT6ZlNLaUC)

**When you make an item or sprite in bitsy, you can set their dialog in the paint window. But if you need more complicated dialog options, you can open the dialog window for further abilities.**   


**Select a sprite in the paint window to edit its dialog.**  


**Long dialog:**  


**Adding additional dialog windows means that your characters keep talking. They can talk as long as you have material for them to say.**   


**Text effects in dialog:**

**There are 6 built-in options. Clicking one sticks the code block in your text. Your text needs to be wrapped between the two curly bracket delimiters for it to show up styled- like so:**

**{wvy}my text{wvy}**  


**You can have multiple styles of text in one dialog! They stack!**  


**Lists in dialog:**  


**Lists let you have lots of different things for your characters to say. The three options are sequence, cycle, and shuffle. They’re pretty self explanatory, but:**  


 **Shuffle - picks randomly between the lines of dialog.**

 **Cycle - runs through each line of dialog in order, repeats.**

 **Sequence - runs through each line of dialog exactly once, doesn’t repeat.**  


**Important: If you are not seeing changes you are making, refresh the page. If you try to change the dialog while the game is running, sometimes it stops saving changes and you will have to refresh to have it start again.**   


**🌿 Part 6: Items & conditionals**  


**You’ll need to use both the ‘inventory-&gt;items’ and ‘dialog-&gt;conditional’ windows.**   


**In the inventory window, you will see a list of all the items in your game. \(You make these in paint - the example was a cup of tea.\)**  


**Items are collectables. When you walk over them, they disappear with an optional line of dialog. Bitsy keeps track of how many of each item you have collected. You can see the number next to your item increase as you walk over them in your game.**   


![](https://lh4.googleusercontent.com/kxJ59A7YwQ-nk0dOphQQnQjmaDIH0rXHvIhuL5BmlaFkdvcEfZzyNWh9ItW4MWTL1O65QXmTeByXtUw7QSC2XJWuAIPFsW4YMc82fv1bRkkdbuhANh3-p-sxQcC4hjA6m1fMtzwl)

**In the conditional window, you can set the dialog to be different depending on how many items of which type you have picked up.**  


![](https://lh4.googleusercontent.com/iVBHOufDBet8WqG_BPPelY4N4TSX9SJENFctRHFICrwU09nY-jb__nYAduxXEKqqGlwuDCT-BdJXxQF6D9m_hKqdBbVXyd2D3u6HyADJsoBbX0Q4bEkulH9yW6CmCqtdHyBdMkxx)

**Setting the above statements in the “conditional” of the dialog window changes my dialog to this:**   


![](https://lh3.googleusercontent.com/bNBkLGC-gTY4KMQPdqCPBUHRWgyeeDiAHjykhQXeCOt4np7EAh69bctlMGmuneob09h222pBu6-e1ahOF_MzTfd3HicfW3qIoXMitC6a9ewVSltAk-izeaHjI6Kei01z4L9LE--l)

**You may write your if/else statements out, or simple generate them via the “conditional” interface.**   


**\(On “Fetch quests” -- &gt;** [**https://youtu.be/gVbPHgsO2S0?t=53**](https://youtu.be/gVbPHgsO2S0?t=53) **\)**  


**🌿 Part 7: Variables & conditionals:**  


**You’ll use the ‘inventory-&gt;variables’ and ‘dialog-&gt;conditional’ windows.** 

**A variable is essentially a place for your game to store information. Think of it like an empty box we can put values in, to check what those values are later. This lets us do logical operations like “did we already talk to this person”?**   


**Here are the basics:**  


**You can define a variable from the inventory window.**   


**You can then use this variable in the ‘conditionals’ section of the dialog window.**  


**Curly brackets- {} - define code blocks in Bitsy.**  


**You can set a variable from inside of dialog like this:**

**{variableName = 1}**  


**You can use basic math operators in conjunction with variables.**

**{variableName = variableName + 2}**  


**The operators you are allowed to use are +, -, /, and \***  


**You can also set variables to strings \(text\), with quotes:**

 **{variableName = "our variable is text”}**  


**If your variable is a string \(text\), the only operation you can do is adding:**

 **{variableName = "our variable” + “ is text”}**  


**Variables can be added to dialog using curly braces and ‘say’:**

**“Did you find the {say variableName} yet?”**  


**Math CAN’T be used on variables inside of a conditional, but you can define variables in conditionals.**  


**Each conditional can only evaluate one variable.**  


**If you want to do anything more than slightly complicated with conditionals and scripting in bitsy, you’ll probably need to get used to looking at the &lt;show code&gt; view of the dialog. It will be useful in showing you how your logic flows from one state to another.**  


**A bitsy scripting caveat:**  


**Often there are clever ways to make it feel like you have programmed in variables without actually having to. For instance, we could write a check that sees if you have talked picked up a key before someone tells you a secret. OR, we could put a one-way room exit under a key to an identical looking room with a person with different dialog in it, so that when you pick up the key you get teleported there and they tell your their secret.**   


**It takes a bit to get your head wrapped around thinking that way, but it definitely counts as a solution. And sometimes it is easier to just do it like that! \(I fully support clever design over bad programming.\)**  


**🌿 Continued: More resources, Bitsy hacks and cool things:**  


**A note- these are all pretty fun, but they are often made and maintained by one person and are sometimes buggy, confusing, require some coding, or are under-documented. I’ve listed their “difficulty” to implement by each one.**  


**Add audio \(super easy\):**

[**https://candle.itch.io/bitsy-audio**](https://candle.itch.io/bitsy-audio)  
****

**Upload jpg and png images, get bitsy data \(fairly easy\):** 

[**https://ruin.itch.io/image-to-bitsy**](https://ruin.itch.io/image-to-bitsy)  
****

**A big collection of hacks on Github \(medium to advanced\):**

[**https://github.com/seleb/bitsy-hacks**](https://github.com/seleb/bitsy-hacks)   
****

**“Borksy”, a tool to help implement hacks \(easy to medium\):**

[**https://ayolland.itch.io/borksy**](https://ayolland.itch.io/borksy)  
****

**Random palette generator \(super easy\):**

[**https://zenzoa.itch.io/palettsy**](https://zenzoa.itch.io/palettsy)  
****

**Multiframe sprite animation with Spritesy \(medium easy\):**

[**https://pansandpots.itch.io/spritesy**](https://pansandpots.itch.io/spritesy)   
****

**“Bitsy HD”, a bitsy at twice the scale \(caution- data not translatable from one to the other. just as easy as bitsy, but twice the drawing work\):**

[**https://vonbednar.itch.io/bitsy-x2**](https://vonbednar.itch.io/bitsy-x2)  
****

**“Full screen animation” using rooms \(easy but a lot of work to implement\):**

[**https://zetef.itch.io/full-animation-in-bitsy**](https://zetef.itch.io/full-animation-in-bitsy)   
****

**And here is a link to a FAQ that answers the following questions:**

* **How do I have a locked door that opens once the player finds the key?**
* **How do I have more than three colours in the palette?**
* **How do I have more than two colours per tile?**
* **How do I change the background colour of the text box?**
* **How do I change my game’s title in the game data \(without using the Bitsy editor\)?**
* **What do I do if the Bitsy editor isn’t working?**
* **What do I do if my game looks blurry?**
* **What do I do if the title of my game keeps disappearing?**

[**https://docs.google.com/document/d/1jRz3wgkQU3kZN\_LGChw4UlMWhVoc145J-euBtkr7NeE/**](https://docs.google.com/document/d/1jRz3wgkQU3kZN_LGChw4UlMWhVoc145J-euBtkr7NeE/edit)

**A custom font tool \(medium to hand\):**

[**https://seansleblanc.itch.io/fontsy**](https://seansleblanc.itch.io/fontsy)  
****

**A few advanced writeups on how their games work \(called post-mortems\):**

[**https://blog.seans.site/post/157692325676/how-it-works-holt**](https://blog.seans.site/post/157692325676/how-it-works-holt)

[**https://paolojcruz.itch.io/anon/devlog/22949/anon-post-mortem-notes-on-using-variables-in-bitsy**](https://paolojcruz.itch.io/anon/devlog/22949/anon-post-mortem-notes-on-using-variables-in-bitsy)  
****

**A few really useful breakdowns of dialog and variables in Bitsy, if you want deeper examples:** 

[**https://cephalopodunk.itch.io/bullshit-fish-names/devlog/23122/time-for-some-rambling-about-dialog**](https://cephalopodunk.itch.io/bullshit-fish-names/devlog/23122/time-for-some-rambling-about-dialog) ****

[**https://ayolland.itch.io/trevor/devlog/29520/bitsy-variables-a-tutorial**](https://ayolland.itch.io/trevor/devlog/29520/bitsy-variables-a-tutorial)   
****

**Plus:**

[**https://bitsy.fandom.com/wiki/Bitsy\_Wiki**](https://bitsy.fandom.com/wiki/Bitsy_Wiki) **\(very in-depth wiki of tips, hacks, tutorials, and examples\)**

[**https://twitter.com/bitsypcs**](https://twitter.com/bitsypcs) **\(a twitter account that tweets new games and resources\)**

[**https://itch.io/games/made-with-bitsy**](https://itch.io/games/made-with-bitsy) **\(a repository of thousands of bitsy games\)**

[**https://twitter.com/adamledoux**](https://twitter.com/adamledoux) **\(the creator of bitsy, tweets news and game jam announcements\)**

[**https://color.adobe.com/create/color-wheel/**](https://color.adobe.com/create/color-wheel/) **\(color palette picker\)**  


