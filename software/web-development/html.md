# HTML

Every web experience is built using HTML, or HyperText Markup Language, as it provides the building blocks for content. Just by understanding some of its simple rules a lot of great work can be done. Looking at the _index.html_ file in a new Glitch project is a great starting point. However, for simplicities sake let's make some small changes…

{% tabs %}
{% tab title="Original" %}
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Hello!</title>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    
    <!-- import the webpage's stylesheet -->
    <link rel="stylesheet" href="/style.css">
    
    <!-- import the webpage's javascript file -->
    <script src="/script.js" defer></script>
  </head>  
  <body>
    <h1>Hi there!</h1>
    
    <p>
      I'm your cool new webpage. Made with <a href="https://glitch.com">Glitch</a>!
    </p>

    <!-- include the Glitch button to show what the webpage is about and
          to make it easier for folks to view source and remix -->
    <div class="glitchButton" style="position:fixed;top:20px;right:20px;"></div>
    <script src="https://button.glitch.me/button.js"></script>
  </body>
</html>
```
{% endtab %}

{% tab title="Updated" %}
```
<!DOCTYPE html>
<html>
  <head>
    <title>Hello!</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="/style.css">
    <script src="/script.js" defer></script>
  </head>  
  <body>
    <h1>Hi there!</h1>
    <p>I'm your cool new webpage. Made with <a href="https://glitch.com">Glitch</a>!</p>
  </body>
</html>

```
{% endtab %}
{% endtabs %}

## Tags

HTML is filled with tags, written like this `<body>` with an opening and closing arrow and the name of the tag between. You can get very far just working with the many tags that exist and you are encouraged to always design your site  with semantics in mind. In the example above we see already some of the most prominent, `<h1>`, `<p>` and `<a>`.

### Div

This one is what we call a "block"-element. Actually, many of the tags are block elements meaning they take up a whole block and push other content down. The div is a placeholder which doesn't have any implicit semantic meaning and is often used for grouping and structuring.

### Headings

Whenever you want to include a heading, such as a title, then you can use the heading tags `<h1>` to `<h6>`. Mind you that for SEO reasons it's advised to only use the main heading once per page.

### Paragraphs

For paragraphs use the `<p>` tag. Remember that this tag is by default a block element, which means it will naturally force down content placed after it. Many other tags are not block but inline, meaning they are aligned next to the following or previous tag.

### Anchor

One of the most important tags is the &lt;a&gt; tag and boy does it come packed with goodies. Basically you use it to send the visitor somewhere :\)

{% tabs %}
{% tab title="HREF" %}
```
<a href="https://dn.se/">Visit Dagens Nyheter!</a>
```
{% endtab %}

{% tab title="TARGET" %}
```
<a href="https://dn.se/" target="_blank">Visit Dagens Nyheter!</a>
```
{% endtab %}
{% endtabs %}

### Span

The `<span>` tag is great for applying styles to words or characters within a paragraph, but can be used freely. This is also a tag that has no semantic meaning by itself and is often used in conjunction with a _class._

### Strong, i, b and em

Similar to span, but these come with semantic meaning.

### Marquee

This is just for lols, try it.

{% hint style="info" %}
Essential to know about tags is that they "nest" meaning a tag can have other tags within them.  This is useful for instance when you want a heading to also be a link to a site. Mastering nesting is key to being a great web developer.
{% endhint %}

