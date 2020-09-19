# 1. Editor



Our friends at Cables have done an excellent job at introducing the Cables interface. Watch this full video and follow along. After that we'll add a bit more depth to some of the elements mentioned. Once you're done we'll get into making things straight away.

{% embed url="https://www.youtube.com/watch?v=d3jGof4GSCc&list=PLYimpE2xWgBveaPOiV\_2\_42kZEl\_1ExB0&index=2" %}

{% page-ref page="shortcuts.md" %}



### The Interface explained

![An empty project \(also known as a patch\)](../../../.gitbook/assets/image%20%2858%29.png)

The cables UI consists of three large panes, the light grey section on the left, is where you will create and connect little blocks called OP's \(short for operators\).

On the top right is the preview window, this will show the visual output of your patch.



![](../../../.gitbook/assets/image%20%2853%29.png)

The lower right has a section on the left which will show the properties of any OP you select, and on the right you can choose what to show. The options are visible when you over over each of the icons:

* **Documentation** This will show you the relevant documentation with each selected OP.
* **Code** See the source code \(JavaScript\) of each OP, if you know JavaScript you can create or change your own OP's. Don't worry about this for now.
* **Texture Preview** This shows a thumbnail of any texture \(image\) you select in your patch.
* **Keyframes** Cables also gives access to a timeline, allowing you to change values in a similar way like After Effects. Don't worry about this for now.
* **Variables** Variables are values that you can store and use in multiple places. This is also possible by patching \(the process of connecting OP's\) but without needing lines connected to it, this can be handy in some situations.
* **Patch connection** A feature to stream your output to another browser window
* **History** Shows your recent actions, you can always undo and redo using `CTRL`+`Z` and `CTRL`+`SHIFT`+`Z`

![Filemanager](../../../.gitbook/assets/image%20%2857%29.png)

Under Tools, you can find a filemanager, this enables you to upload assets to use in your patch.

### Console

Since cables is working inside the browser, you actually have access to all the tools that Chrome and other browsers offer to help you develop things. A very important one is the console. This is a place where you can output text and information that helps you to figure out what is going on. Cables has an OP called [ConsoleLog ](https://cables.gl/op/Ops.Debug.ConsoleLog)which you can use to output numbers and text to the console. Bring up the developer tools using `CTRL`+ `SHIFT`+ `I` .

![](../../../.gitbook/assets/image%20%2855%29.png)

{% embed url="https://cables.gl/p/5f6358201f7ca3143b0167c8?s=U0rqYQK2HR7Ijona" %}









{% hint style="info" %}
If you're ever getting something in the UI that isn't behaving as it should, or you're not seeing any changes in the preview pane. Try to save and reload the page.
{% endhint %}



