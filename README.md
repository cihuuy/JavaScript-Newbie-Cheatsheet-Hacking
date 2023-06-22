# JavaScript - Newbie Cheatsheet | Hacking

Welcome, fellow coding enthusiasts, to the JavaScript Newbie Cheatsheet Hacking repository! I'm just a JavaScript newbie, bumbling and stumbling my way through the mesmerizing maze of coding. Along the way, I've managed to bungle into some pretty handy tips and tricks, and in the spirit of sharing, I've decided to spill all my beans right here!

Over time, as a dedicated tinkerer, I've embraced the wild and wonderful world of JavaScript, using it to poke and prod my own websites, tickle my routers (with their express consent, of course), and more. My syntax? Far from perfect. My code? A delightful hot mess of "wuziduzi world" meets "wuseman's spaghetti that just somehow works". And yet, the discoveries I've made have been astonishing.

I'm no expert in JavaScript. Heck, I wouldn't even know where to start. But these haphazardly stumbled-upon techniques have served me well, and I reckon there might be a few nuggets of wisdom to be found in my "accidentally-on-purpose" explorations. Hence, the birth of this repository.

This mish-mash of tips and tricks spans across various topics, without any particular focus on a specific level of expertise. They are simply based on my own exhilarating journey of eureka moments and facepalms. I won't be giving detailed lectures here - just quick, practical, ready-to-use snippets that you can plug into your own adventures in code. 

A note of caution though - these tips and tricks may not play nice with unauthorized or not-owned-by-you websites. They've been exclusively tested and tailored to my own online playgrounds. If you choose to release them into the wild, please be responsible and respectful of others' digital territories. I sternly discourage any and all forms of unauthorized activities.

So, without further ado, enjoy this hotchpotch of JavaScript tips and tricks, handpicked from my personal adventures. If you'd like to contribute, that's great! Just make sure to add your bits in the right order. Spotted a bug? Let me know! I'm always up for a good bug hunt.

Let's say it once again, my dear comrades: hack to learn, **NOT** learn to hack!

**Happy hacking!**

***

## Table of Contents:

- [URL Wise](#url-wise)
  - [Extracting URLs from a Web Page](#extracting-urls-from-a-web-page)
  - [Extracting URLs using Destructuring](#extracting-urls-using-destructuring-alternative-1)
  - [Extracting URLs using the Spread Operator](#extracting-urls-using-the-spread-operator-alternative-2)
  - [Extracting URLs using Array.from with Mapping](#extracting-urls-using-arrayfrom-with-mapping-alternative-3)
  - [Extracting URLs using a for...of Loop](#extracting-urls-using-a-forof-loop-alternative-4)
  - [Find all src URLs](#find-all-src-urls)
  - [Get all URLs (XPath)](#get-all-urls-xpath)
  - [Get all URLs (jQuery)](#get-all-urls-jquery)
  - [Get all URLs (Regular Expression)](#get-all-urls-alternative-7-regular-expression)
  - [Get all URLs (Fetch API)](#get-all-urls-fetch-api)
  - [Get All API Endpoints from JavaScript Files](#get-all-api-endpoints-from-javascript-files)
  - [Extracting All Emails from a Web Page](#extracting-all-emails-from-a-web-page)
  - [Get all image URLs from a web page](#get-all-image-urls-from-a-web-page)
  - [Get all CSS File URLs](#get-all-css-file-urls)
  - [Get all internal URLs from a web page](#get-all-internal-urls-from-a-web-page)
  - [Get all external URLs from a web page](#get-all-external-urls-from-a-web-page)
  - [Get all unique URLs from a web page](#get-all-unique-urls-from-a-web-page)
  - [Get all PDF files from a web page](#get-all-pdf-files-from-a-web-page)
  - [Get all file download links](#get-all-file-download-links)
  - [Get all mailto links](#get-all-mailto-links)
  - [Get all tel links](#get-all-tel-links)
  - [Get all URLs having certain text](#get-all-urls-having-certain-text)
  - [Get all hashtags from a webpage](#get-all-hashtags-from-a-webpage)
  - [Get URLs of all open tabs](#get-urls-of-all-open-tabs)
  - [Get URLs of all iframes on a page](#get-urls-of-all-iframes-on-a-page)
  - [Get all URLs from CSS](#get-all-urls-from-css)
  - [Extract URLs from Inline JavaScript](#extract-urls-from-inline-javascript)
  - [Extracting URLs from HTML Comments](#extracting-urls-from-html-comments)
  - [Extract URLs from SVG](#extract-urls-from-svg)
  - [Extracting Specific Parts of a URL](#extracting-specific-parts-of-a-url)
  - [URL Redirection](#url-redirection)
  - [Add URL parameter](#add-url-parameter)
  - [Remove URL Parameter](#remove-url-parameter)
  
***

# URL Wise

### Extracting URLs from a Web Page

```javascript
Array.from(document.links).forEach(({ href }) => console.log(href));
```

### Extracting URLs using Destructuring (Alternative 1)

```javascript
Array.from(document.links, ({ href }) => href).forEach(console.log);
```

### Extracting URLs using the Spread Operator (Alternative 2)

```javascript
[...document.getElementsByTagName('a')].forEach(a => console.log(a.href));
```

### Extracting URLs using Array.from with Mapping (Alternative 3)

```javascript
Array.from(document.getElementsByTagName('a'), a => a.href).forEach(url => console.log(url));
```

### Extracting URLs using a for...of Loop (Alternative 4)

```javascript
var urls = Array.from(document.getElementsByTagName('a'));
for (var url of urls) {
    console.log(url.href);
}
```

### Find all src URLs

```javascript
// Select all relevant HTML elements that may have src attributes
var elementsWithSrc = document.querySelectorAll('img, script, iframe');

// Iterate through the elements and retrieve the src URLs
for (var i = 0; i < elementsWithSrc.length; i++) {
  var element = elementsWithSrc[i];
  var src = element.getAttribute('src');
  if (src) {
    console.log(src);
  }
}
```

### Get all URLs (XPath)

```javascript
const xpathResult = document.evaluate('//a', document, null, XPathResult.ANY_TYPE, null);
let node = xpathResult.iterateNext();
while (node) {
  console.log(node.href);
  node = xpathResult.iterateNext();
}
```

### Get all URLs (jQuery)

```javascript
document.querySelectorAll('a').forEach(function(a) {
  console.log(a.href);
});
```

### Get all URLs (Alternative 7: Regular Expression)

```javascript
const regex = /<a\s+(?:[^>]*?\s+)?href=(["'])(.*?)\1/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[2]);


}
```

### Get all URLs (Fetch API)

```javascript
fetch(document.location.href)
  .then(response => response.text())
  .then(html => {
    const regex = /<a\s+(?:[^>]*?\s+)?href=(["'])(.*?)\1/g;
    let match;
    while ((match = regex.exec(html))) {
      console.log(match[2]);
    }
  });
```

### Get All API Endpoints from JavaScript Files

```javascript
fetch(document.location.href)
  .then(response => response.text())
  .then(html => {
    const scriptUrls = html.match(/<script src="(.*?)"/g);
    scriptUrls.forEach(url => {
      fetch(url)
        .then(response => response.text())
        .then(js => {
          const matches = js.match(/\/api\/\w+/g);
          if (matches) {
            matches.forEach(endpoint => console.log(endpoint));
          }
        });
    });
});
```

### Extracting All Emails from a Web Page 

```javascript
const regex = /\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[0]);
}
```

### Get all image URLs from a web page

```javascript
Array.from(document.images).forEach(({ src }) => console.log(src));
```

### Get all CSS File URLs

```javascript
Array.from(document.styleSheets).forEach(({ href }) => console.log(href));
```

### Get all internal URLs from a web page

```javascript
Array.from(document.links).filter(a => a.hostname === location.hostname).forEach(({ href }) => console.log(href));
```

### Get all external URLs from a web page

```javascript
Array.from(document.links).filter(a => a.hostname !== location.hostname).forEach(({ href }) => console.log(href));
```

### Get all unique URLs from a web page

```javascript
let uniqueURLs = [...new Set(Array.from(document.links).map(({ href }) => href))];
console.log(uniqueURLs);
```

### Get all PDF files from a web page

```javascript
Array.from(document.links).filter(a => a.href.endsWith('.pdf')).forEach(({ href }) => console.log(href));
```

### Get all file download links

```javascript
Array.from(document.links).filter(a => a.download).forEach(({ href }) => console.log(href));
```

### Get all mailto links

```javascript
Array.from(document.links).filter(a => a.href.startsWith('mailto:')).forEach(({ href }) => console.log(href));
```

### Get all tel links 

```javascript
Array.from(document.links).filter(a => a.href.startsWith('tel:')).forEach(({ href }) => console.log(href));
```

### Get all URLs having certain text

```javascript
Array.from(document.links).filter(a => a.textContent.includes('example')).forEach(({ href }) => console.log(href));
```

### Get all hashtags from a webpage

```javascript
Array.from(document.links).filter(a => a.href.includes('#')).forEach(({ href }) => console.log(href));
```

### Get URLs of all open tabs

```javascript
// You need to run this in browser console not in the page
chrome.tabs.query({}, function(tabs) { 
  tabs.forEach(tab => console.log(tab.url)); 
});
```

### Get URLs of all iframes on a page

```javascript
Array.from(document.querySelectorAll('iframe')).forEach(({ src }) => console.log(src));
```

### Get all URLs from CSS 

```javascript
const stylesheets = [...document.styleSheets];
stylesheets.forEach(sheet => {
  const rules = [...sheet.cssRules];
  rules.forEach(rule => {
    const matches = rule.cssText.match(/url\((.*?)\)/g);
    if (matches) {
      matches.forEach(url => console.log(url));
    }
  });
});
```

### Extract URLs from Inline JavaScript 

```javascript
const scripts = Array.from(document.scripts).filter(script => !script.src);
scripts.forEach(script => {
  const matches = script.textContent.match(/http[s]?:\/\/[^"',\s)]+/g);
  if (matches) {
    matches.forEach(url => console.log(url));
  }
});
```

### Extracting URLs from HTML Comments 

```javascript
const comments = [];
const walk = document.createTreeWalker(document, NodeFilter.SHOW_COMMENT, null, false);
let node;
while ((node = walk.nextNode())) {
  comments.push(node.data);
}
comments.forEach(comment => {
  const matches = comment.match(/http[s]?:\/\/[^'",\s)]+/g);
  if (matches) {
    matches.forEach(url => console.log(url));
  }
});
```

### Extract URLs from SVG

```javascript
Array.from(document.querySelectorAll('svg')).forEach(svg => {
  const matches = svg.outerHTML.match(/http[s]?:\/\/[^'",\s)]+/g);
  if (matches) {
    matches.forEach(url => console.log(url));
  }
});
```

### Extracting Specific Parts of a URL


```javascript
// Extract the domain from a URL
const extractDomain = () => {
  const url = window.location.href;
  const urlObject = new URL(url);
  return urlObject.hostname;
};

const domain = extractDomain();
console.log(domain);

// Extract the path from a URL
const extractPath = () => {
  const url = window.location.href;
  const urlObject = new URL(url);
  return urlObject.pathname;
};

const path = extractPath();
console.log(path);
```


### URL Redirection


```javascript
// Perform a URL redirect with a delay
const redirectToURL = (url, delay = 2000) => {
  setTimeout(() => {
    window.location.href = url;
  }, delay);
};

redirectToURL('https://github.com/wuseman', 3000);
```


### Add URL parameter


```javascript
const addOrUpdateURLParameter = (key, value) => {
  // Function to add or update a URL parameter with the provided key and value
  // Returns the updated URL with the modified parameter
  const url = window.location.href;
  const urlObject = new URL(url);
  urlObject.searchParams.set(key, value);
  return urlObject.href;
};

const updatedURL = addOrUpdateURLParameter('param2', 'value2');
console.log(updatedURL);
```


### Remove URL Parameter

```javascript
const removeURLParameter = (key) => {
  // Function to remove a URL parameter with the provided key
  // Returns the updated URL with the parameter removed
  const url = window.location.href;
  const urlObject = new URL(url);
  urlObject.searchParams.delete(key);
  return urlObject.href;
};

const modifiedURL = removeURLParameter('param2');
console.log(modifiedURL);
```
