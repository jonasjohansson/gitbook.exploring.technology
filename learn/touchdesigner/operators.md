# Operators

Operators can be seen as tiny programs that can be chained together to build all sorts of things. There are a lot of them, and they come in various types. Most operators have inputs and outputs, expecting data to arrive on the left \(input\), and then present data on the right \(output\), ready to be retrieved.

Press `TAB` to open the list of operators \(OP Create Dialog\), or right-click and **Add operator**. The types of operators are seen in the top, hover their label to see a description at the bottom of the window. Press `TAB` again to cycle between the different operators.

![](../../.gitbook/assets/image%20%2829%29.png)

The four main ones you will likely work with are TOP's, CHOP's, SOP's and DAT's. Lets briefly go into the difference between these types.

![](../../.gitbook/assets/image%20%2812%29.png)

**TOP**

Texture operators are **purple** and handle anything related to pixel data. These are the fastest and most powerful components TouchDesigner has. You will end up using them a lot. They can be used to do all sorts of things, from composing various images streams together, blurring, detecting edges, handling external devices like Kinects and camera's to pointclouds.

**CHOP**

Channel operators are **green** and they are mostly made to do math and logic operations. This way you can program all sorts of behavior which can in turn be placed onto parameters of other operators to automatically control them. 

**SOP**

Surface operators are **blue** and relate to shapes happening in 3D space. Here you can find basic shapes and ways to manipulate their geometry.

**DAT**

Data operators are **violet-red** and can be used to store spreadsheets, as well as do things that are more text and scripting related. DATs often go hand in hand with Python scripting. This won't be essential to start using TouchDesigner, but Python is certainly one of the things that will greatly enhance what you can do in Touch.

