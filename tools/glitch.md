# Glitch

Welcome to Glitch, a creative and expressive platform that everyone can use to create the web. In short it's a full web development package that allows for writing cool code, collaboration, easy sharing \(everything is live\), HTTPS and custom domain names.

## Setup

Visit [Glitch](https://glitch.com/) and login with your [Github](https://github.com) account or create a new account. Then choose **New Project** and choose the _hello-webpage_ option.

![](../.gitbook/assets/screenshot-2019-09-23-at-22.47.33.png)

Once done you will see an editor similar to this. On the left menu you see some files, and on the right the contents of the _README.md_ file — let's see what it says!

![](../.gitbook/assets/screenshot-2019-09-23-at-22.51.39.png)

A few quick ones… You can change the domain name in the top left by clicking the current title. By clicking Show you can choose to view the public version of the site as a new window, or inline with your editor.

### Help tidy code

~~When coding it's easy to make things messy. Use the~~ [~~Prettier Glitch Bookmarklet~~](https://prettier-new.glitch.me/) ~~to help maintain sanity!~~

Glitch now uses the fabulous [Prettier](https://prettier.io/) library for this, and have the default options applied. Use a .prettierc [JSON configuration file](https://prettier.io/docs/en/configuration.html#basic-configuration) in your project if you want to set your own preferences.

### Force HTTPS

When using secure services such as camera, GPS and device API you will need visitors to use HTTPS and not HTTP \(which is the standard protocol on Glitch\). You can either explicitly mention to add 'https://' or include this script:

```markup
<script>
  if (location.protocol != "https:") {
    location.href =
      "https:" +
      window.location.href.substring(window.location.protocol.length);
  }
</script>
```

## Domain

At some point the Glitch domain will not suffice. At this point it would be natural to look for a new domain! To connect a custom domain to Glitch you must be **thanked twice**, then follow [this guide](https://glitch.com/help/custom-domain/). 

