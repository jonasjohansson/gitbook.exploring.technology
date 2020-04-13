# Enhanced radical knitting using JavaScript and the Terminal

This article is introduction and preparation for [the live streamed workshop with the same name](https://www.twitch.tv/exploringtechnology).

In this workshop we are going to look at ways of using the MacOS terminal environment together with JavaScript programming to create experimental knitting patterns and later make simple interfaces to guide us through the actual knitting.

We'll be doing intermediate level programming and lightweight knitting, but the idea is that you don't have to know either to follow along. The main point is to introduce these topics and try to show ways of combining technology and craft in a way that will inspire you to experiment with whatever you enjoy creating.

### Introductions

If you want to do a bit of prep reading, here are some introductory links.

#### The Terminal

The Terminal is an interface where your run commands on a command line. We'll be using the MacOS Terminal, but much of this is applicable to Windows and Linux environments too.

{% embed url="https://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line" %}

#### JavaScript

JavaScript is a programming language that makes web pages interactive. It can also be run outside browsers – i.e. on a server and in the terminal – using Node.js.

Building JavaScript programs is easier when you don't have to do everything yourself, so we'll install and use publicly available JavaScript packages from the Node.js package manager [npm](https://www.npmjs.com/).

{% embed url="https://javascript.info/intro" %}

#### Knitting

Knitting is the ancient magic of looping strands of yarn into clothes or other things. While it can get as complex as you like, getting started and making your first scarf is fairly easy and straightforward.

{% embed url="https://www.youtube.com/watch?v=p\_R1UDsNOMk" %}

### What we'll be doing

1. **Getting familiar with the terminal** and a few ways of using it. We'll look at downloading things from the Internet, writing things to files, piping, running JavaScript programs and a few more bits and bobs.
2. **Generating knitting patterns using JavaScript** and defining parameters to experiment with \(basic [generative design](https://en.wikipedia.org/wiki/Generative_design)\).
3. **Using external data sources to produce designs.** We'll be testing things out with imagery and some nature/weather data.
4. Finally we'll **create simple interfaces to help us knit**, since knitting complex, random and/or non-repetitive patterns is quite hard to do from simply looking at them.

### Preparation

Even though this workshop is mostly inspirational, you are very welcome to follow along or use the code afterwards. For this you'll need a few things:

* A text editor, perhaps one that's made for coding, like [Sublime Text](https://www.sublimetext.com/) or [Visual Studio Code](https://code.visualstudio.com/).
* [Node and `npm`](https://nodejs.org/en/) – The JavaScript server-side runtime and package manager.
* `ports` \(shipped with MacOS\) or [`brew`](https://brew.sh/) – Package managers to install packages or programs directly from the command line.
* [`jp2a`](https://csl.name/jp2a/) – A command line image-to-ASCII converter installable via ports or brew.
* We'll also be using the JavaScript packages `chalk`, `date-fns`, `got`, `lodash` and `nodemon` which we'll install using `npm`.

