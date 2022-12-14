# CS1-Bookmarklets

I'm feeling very clever. I've got this sweet line of javascript that replaces "Elon" with "Spamton". 

A **bookmark** normally takes you to a new web page. A **bookmarklet** is a bookmark that runs javascript on the current page instead of taking you to a new page. To declare that it is a bookmarklet, the "location" it points to starts with `javascript:`.

This guide will walk you through creating your first bookmarklet. For a more thorough guide check out the great website [Bookmarklets - Browser Power](http://subsimple.com/bookmarklets/index.php).

Some bookmarklets are pretty cool.  Make pages rainbow and sparkly with [Cornify](http://www.cornify.com/).

## Goal
Take a short javascript script and put it into a bookmarklet.


## Try One Out

Install this bookmarklet

Make a new bookmark in your browser (right-click on the [bookmarks bar](https://support.google.com/chrome/answer/95745?hl=en) and click `Add Page...`)
  - For the "Name" you might put "Pinker".
  - Copy the code block below, paste this into the "Location" of a new bookmark.

```
javascript:(function(){document.body.style.background = 'pink';})();
```


Navigate to Google and click the bookmarklet. Voila!



## Let's Make Our Own!

To make a bookmarklet we have three steps:

1. Write some javascript code that you want in a bookmarklet (using the console)
2. Put `javascript:` in front of the code
3. Wrap everything in an [IIFE](http://en.wikipedia.org/wiki/Immediately-invoked_function_expression) so the page doesn't freak out

Here is our Elon to Spamton function:
```
document.body.innerHTML = document.body.innerHTML.replace(/Elon/g, "Spamton");
```

Try just putting `javascript:` in front of it
```
javascript:document.body.innerHTML = document.body.innerHTML.replace(/Elon/g, "Spamton");
```

> You can debug bookmarklets much faster if you use the Location bar - see "Quicker Debugging" below for caveats.

Partway there! The page did SOMETHING but it seemed to refresh and then the CSS/images didn't load! :(

We can get around this by putting this in an [Immediately Invoked Functional Expression](http://en.wikipedia.org/wiki/Immediately-invoked_function_expression). You don't have to understand this completely to be a bookmarkleteer. Using an IIFE is one way to avoid having a return value, see [Rules for Bookmarklets (Browser Power](http://subsimple.com/bookmarklets/rules.php) and [Tips - Encapsulation (Browser Power)](http://subsimple.com/bookmarklets/tips.php#Encapsulation).

Here are two example ways to write a standard IIFE:
```javascript
(function(){})();
// or
function(){}();
```

Here's the general template I always use:
```
javascript:(function(){CONTENTGOESHERE})();
```

Try it with your Elon to Spamton code!
```
javascript:(function(){
  document.body.innerHTML = document.body.innerHTML.replace(/Elon/g, "Spamton");
})();
```



## Quicker Debugging
Editing the bookmarklet "location" every time you have a code change can be tedious. You can save some time while debugging if you use the Location bar. If it works when you paste into the location bar, it should work as a saved bookmarklet.

Try pasting this:
```
javascript:(function(){
  document.body.innerHTML = document.body.innerHTML.replace(/Elon/g, "Spamton");
})();
```

> You'll have to retype `javascript:` at the front of what you paste.

The trouble with the location bar is that it strips "javascript:" from the front of whatever you paste. This probably keeps most people safe from copy-pasting code from the internet willy nilly, but you're writing your own. Hopefully you trust yourself :)



## Editing bookmarklets
When you save a bookmarklet, the browser will remove newlines. If you want to edit a bookmarklet it might be really ugly. You have at least two options:

1. Save a copy of the bookmarklet in a text file on your computer (and in github!)
2. Use a tool like [JSBeautifier](http://jsbeautifier.org/) to make it look nice again. It will put in new lines, indentation, and syntax highlight for you. (but be careful! If you press back in your browser the code is lost. I recommend using this to beautify your code, then that you edit it in a text editor.)

## References & More Resources
- [Bookmarklets - Browser Power](http://subsimple.com/bookmarklets/index.php)
