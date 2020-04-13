# Enhanced radical knitting using JavaScript and the Terminal

{% hint style="success" %}
Written by [Alexander Wallin](https://www.alexanderwallin.com/)
{% endhint %}

Ever wondered how you can use JavaScript and the Terminal to create experimental knitting patterns, and guide us through the actual knitting?

This is a beginner-to-intermediate introduction to programming and  knitting, but the idea is that you don't have to know either to get the gist. The main point is to introduce these topics and try to show ways of combining technology and craft in a way that will inspire you to experiment with whatever you enjoy creating.

## Getting started

If you want to follow along you need the following:

1. Basic programming knowledge.
2. A text editor like [Sublime Text](https://www.sublimetext.com/) or [Visual Studio Code](https://code.visualstudio.com/).
3. [Node](https://nodejs.org/en/), a package manager for Javascript
4. [Ports](https://www.macports.org/) or [Brew](https://brew.sh/) \(recommended\).
5. [JP2A](https://csl.name/jp2a/), a command line image-to-ASCII converter installed via ports or brew.
6. The `npm` packages `chalk`, `date-fns`, `got`, `lodash` and `nodemon`.

{% hint style="info" %}
Visit the [repository](https://github.com/alexanderwallin/knitting) for the full project.
{% endhint %}

### Terminal

The terminal \([guide](https://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line)\) is an interface where you run commands on a command line. We will use it to download things from the Internet, write things to We'll be using the MacOS Terminal, but much of this is also applicable to Windows and Linux environments.

### JavaScript

JavaScript \([introduction](https://javascript.info/intro)\) is a programming language that makes web pages interactive. It can also be run outside browsers, for instance in the terminal using Node.

Building JavaScript programs is easier when you don't have to do everything yourself, so we'll install and use publicly available packages from the Node package manager [npm](https://www.npmjs.com/).

### Knitting

Knitting \([introduction](https://youtu.be/p_R1UDsNOMk)\) is the ancient magic of looping strands of yarn into clothes or other things. While it can get as complex as you like, getting started and making your first scarf is fairly easy and straightforward.

### The Workshop

1. **Get familiar with the terminal** and a few ways of using it. We'll look at downloading things from the Internet, writing files, piping, run JavaScript programs and a few more bits and bobs.
2. **Generate knitting patterns using JavaScript** and define parameters to experiment with \(basic [generative design](https://en.wikipedia.org/wiki/Generative_design)\).
3. **Use external data sources to produce designs.** We'll test things out with imagery and some nature and weather data.
4. Finally, we **create simple interfaces that help us knit**, since knitting is complex, random and/or non-repetitive patterns is hard to do from simply looking at them.

