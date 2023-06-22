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

Table of Contents:
- [URL Wise](#url-wise)
  - [Extracting URLs from a Web Page](#extracting-urls-from-a-web-page)
  - [Extracting URLs using Destructuring (Alternative 1)](#extracting-urls-using-destructuring-alternative-1)
  - [Extracting URLs using the Spread Operator (Alternative 2)](#extracting-urls-using-the-spread-operator-alternative-2)
  - [Extracting URLs using Array.from with Mapping (Alternative 3)](#extracting-urls-using-arrayfrom-with-mapping-alternative-3)
  - [Extracting URLs using a for...of Loop (Alternative 4)](#extracting-urls-using-a-forof-loop-alternative-4)
  - [Find all src URLs](#find-all-src-urls)
  - [Get all URLs (XPath)](#get-all-urls-xpath)
  - [Get all URLs (jQuery)](#get-all-urls-jquery)
  - [Get all URLs (Alternative 7: Regular Expression)](#get-all-urls-alternative-7-regular-expression)
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
  - [Get all URLs from CSS)](#get-all-urls-from-css)
  - [Extract URLs from Inline JavaScript](#extract-urls-from-inline-javascript)
  - [Extracting URLs from HTML Comments](#extracting-urls-from-html-comments)
  - [Extract URLs from SVG](#extract-urls-from-svg)
  - [Extracting Specific Parts of a URL](#extracting-specific-parts-of-a-url)
  - [URL Redirection](#url-redirection)
  - [Add URL parameter](#add-url-parameter)
  - [Remove URL Parameter](#remove-url-parameter)
  - [Extract all URLs from a Website recursive (Separate Lines)](#extract-all-urls-from-a-website-recursive-separate-lines)
  - [Extract all URLs from a Website (Filtered by Domain)](#extract-all-urls-from-a-website-filtered-by-domain)
  - [Extract all URLs from a Website (External URLs Only)](#extract-all-urls-from-a-website-external-urls-only)
  - [Extract all URLs from a Website (Unique URLs Only)](#extract-all-urls-from-a-website-unique-urls-only)
  - [Extract all URLs from Images](#extract-all-urls-from-images)
  - [Extract all URLs from Scripts](#extract-all-urls-from-scripts)
  - [Extract all URLs from Stylesheets](#extract-all-urls-from-stylesheets)
  - [Extract all URLs from AJAX or Fetch Requests](#extract-all-urls-from-ajax-or-fetch-requests)
  - [Extract all URLs from Attachments or Downloadable Files](#extract-all-urls-from-attachments-or-downloadable-files)

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
let unique

URLs = new Set(Array.from(document.links).map(({ href }) => href));
uniqueURLs.forEach(url => console.log(url));
```

### Get all PDF files from a web page

```javascript
Array.from(document.links).filter(a => a.href.endsWith('.pdf')).forEach(({ href }) => console.log(href));
```

### Get all file download links

```javascript
Array.from(document.querySelectorAll('a[download]')).forEach(({ href }) => console.log(href));
```

### Get all mailto links

```javascript
Array.from(document.querySelectorAll('a[href^="mailto:"]')).forEach(({ href }) => console.log(href));
```

### Get all tel links

```javascript
Array.from(document.querySelectorAll('a[href^="tel:"]')).forEach(({ href }) => console.log(href));
```

### Get all URLs having certain text

```javascript
Array.from(document.links).filter(a => a.innerText.includes('text')).forEach(({ href }) => console.log(href));
```

### Get all hashtags from a webpage

```javascript
Array.from(document.querySelectorAll('a[href^="#"]')).forEach(({ href }) => console.log(href));
```

### Get URLs of all open tabs

```javascript
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
Array.from(document.styleSheets).forEach(styleSheet => {
  const cssRules = styleSheet.cssRules || styleSheet.rules;
  if (cssRules) {
    Array.from(cssRules).forEach(rule => {
      const urlMatches = rule.cssText.match(/url\(["']?(.*?)["']?\)/g);
      if (urlMatches) {
        urlMatches.forEach(url => console.log(url.match(/url\(["']?(.*?)["']?\)/)[1]));
      }
    });
  }
});
```

### Extract URLs from Inline JavaScript

```javascript
const regex = /url\s*\(\s*(['"]?)(.*?)\1\s*\)/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[2]);
}
```

### Extracting URLs from HTML Comments

```javascript
const regex = /<!--.*?(\bhttps?:\/\/\S+)\b.*?-->/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[1]);
}
```

### Extract URLs from SVG

```javascript
Array.from(document.getElementsByTagName('image')).forEach(({ href }) => console.log(href));
```

### Extracting Specific Parts of a URL

```javascript
function extractDomain(url) {
  const domainRegex = /^(?:https?:\/\/)?(?:[^@\n]+@)?(?:www\.)?([^:\/\n?]+)/;
  const matches = url.match(domainRegex);
  return matches ? matches[1] : null;
}

function extractProtocol(url) {
  const protocolRegex = /^(https?:\/\/)/;
  const matches = url.match(protocolRegex);
  return matches ? matches[1] : null;
}

function extractPath(url) {
  const pathRegex = /^(?:https?:\/\/)?[^\/]+(\/.*)/;
  const matches = url.match(pathRegex);
  return matches ? matches[1] : null;
}

const url = 'https://www.example.com/path/to/resource?query=string#fragment';

console.log('Domain:', extractDomain(url));
console.log('Protocol:', extractProtocol(url));
console.log('Path:', extractPath(url));
```

### URL Redirection

```javascript
window.location.href = 'https://www.newurl.com';
```

### Add URL parameter

```javascript
function addUrlParameter(url, parameterName, parameterValue) {
  const separator = url.includes('?') ? '&' : '?';
  return url + separator + encodeURIComponent(parameterName) + '=' + encodeURIComponent(parameterValue);
}

const originalUrl = 'https://www.github.com/wuseman';
const modifiedUrl = addUrlParameter(originalUrl, 'param', 'value');
console.log(modifiedUrl);
```

### Remove URL Parameter

```javascript
function removeUrlParameter(url, parameterName) {
  const urlParts = url.split('?');
  if (urlParts.length >= 2) {
    const prefix = encodeURIComponent(parameterName) + '=';
    const parameters = urlParts[1].split(/[&;]/g);

    for (let i = parameters.length - 1; i >= 0; i--) {
      if (parameters[i].lastIndexOf(prefix, 0) !== -1) {
        parameters.splice(i, 1);
      }
    }

    if (parameters.length > 0) {
      return urlParts[0] + '?' + parameters.join('&');
    } else {
      return urlParts[0];
    }
  }
  return url;
}

const originalUrl = 'https://www.somesite.com?param1=value1&param2=value2';
const modifiedUrl = removeUrlParameter(originalUrl, 'param2');
console.log(modifiedUrl);
```

### Extract all URLs from a Website recursive (Separate Lines)

```javascript
// Function to extract the domain from a URL
function extractDomain(url) {
  const domainRegex = /^(?:https?:\/\/)?(?:[^@\n]+@)?(?:www\.)?([^:\/\n?]+)/;
  const matches = url.match(domainRegex);
  return matches ? matches[1] : null;
}

// Function to extract all URLs from a website and return them as separate lines
function extractURLsSeparateLines() {
  const allURLs = [];

  // Retrieve all anchor elements on the page
  const anchorElements = document.getElementsByTagName('a');

  // Extract URLs
  for (let i = 0; i < anchorElements.length; i++) {
    const href = anchorElements[i].href;
    const domain = extractDomain(href);

    // Filter out external URLs if needed
    if (domain !== null) {
      allURLs.push(href);
    }
  }

  return allURLs;
}

// Recursive function to crawl all pages of the website
function crawlWebsite(currentURL) {
  // Create a new XMLHttpRequest object
  const xhr = new XMLHttpRequest();

  // Callback function for handling the response
  xhr.onload = function () {
    if (xhr.status === 200) {
      // Extract URLs from the current page
      const urls = extractURLsSeparateLines();

      // Log the extracted URLs on separate lines in the console
      console.log(`Extracted URLs from ${currentURL}:`);
      console.log(urls.join('\n'));

      // Extract and crawl URLs from child pages
      const domain = extractDomain(currentURL);
      const links = Array.from(new Set(urls.filter(url => extractDomain(url) === domain)));

      links.forEach(link => {
        const absoluteURL = new URL(link, currentURL).href;
        crawlWebsite(absoluteURL);
      });
    }
  };

  // Open the current URL
  xhr.open('GET', currentURL);
  xhr.send();
}

// Call the function to start crawling the website from the current page
crawlWebsite(window.location.href);
```

### Extract all URLs from a Website (Filtered by Domain)

```javascript
// Function to extract the domain from a URL
function extractDomain(url) {
  const domainRegex = /^(?:https?:\/\/)?(?:[^@\n]+@)?(?:www\.)?([^:\/\n?]+)/;
  const matches = url.match(domainRegex);
  return matches ? matches[1] : null;
}

// Function to extract all URLs from a website filtered by a specific domain
function extractURLsByDomain(domain) {
  const allURLs = [];

  // Retrieve all anchor elements on the page
  const anchorElements = document.getElementsByTagName('a');

  // Extract URLs
  for (let i = 0; i < anchorElements.length; i++) {
    const href = anchorElements[i].href;
    const anchorDomain = extractDomain(href);

    // Filter URLs by the specified domain
    if (anchorDomain !== null && anchorDomain.includes(domain)) {
      allURLs.push(href);
    }
  }

  return allURLs;
}

// Specify the domain to filter URLs
const targetDomain = 'github.com/wuseman';

// Call the function to extract URLs filtered by the domain
const filteredURLs = extractURLsByDomain(targetDomain);

// Log the extracted URLs to the console
console.log(`Extracted URLs for domain ${targetDomain}:`, filteredURLs);
```

### Extract all URLs from a Website (External URLs Only)

```javascript
// Function to extract the domain from a URL
function extractDomain(url) {
  const domainRegex = /^(?:https?:\/\/)?(?:[^@\n]+@)?(?:www\.)?([^:\/\n?]+)/;
  const matches = url.match(domainRegex);
  return matches ? matches[1] : null;
}

// Function to extract all external URLs from a website
function extractExternalURLs() {
  const allURLs = [];

  // Retrieve all anchor elements on the page
  const anchorElements = document.getElementsByTagName('a');

  // Extract URLs
  for (let i = 0; i < anchorElements.length; i++) {
    const href = anchorElements[i].href;
    const domain = extractDomain(href);

    // Filter out internal URLs by comparing domains
    if (domain !== null && !domain.includes(window.location.hostname)) {
      allURLs.push(href);
    }
  }

  return allURLs;
}

// Call the function to extract external URLs
const externalURLs = extractExternalURLs();

// Log the extracted external URLs to the console
console.log('Extracted External URLs:', externalURLs);
```

### Extract all URLs from a Website (Unique URLs Only)

```javascript
// Function to extract the domain from a URL
function extractDomain(url) {
  const domainRegex = /^(?:https?:\/\/)?(?:[^@\n]+@)?(?:www\.)?([^:\/\n?]+)/;
  const matches = url.match(domainRegex);
  return matches ? matches[1] : null;
}

// Function to extract all unique URLs from a website
function extractUniqueURLs() {
  const allURLs = [];

  // Retrieve all anchor elements on the page
  const anchorElements = document.getElementsByTagName('a');

  // Extract URLs
  for (let i = 0; i < anchorElements.length; i++) {
    const href = anchorElements[i].href;
    const domain = extractDomain(href);

    // Check if the URL is already in the array
    if (allURLs.indexOf(href) === -1) {
      allURLs.push(href);
    }
  }

  return allURLs;
}

// Call the function to extract unique URLs
const uniqueURLs = extractUniqueURLs();

// Log the extracted unique URLs to the console
console.log('

Extracted Unique URLs:', uniqueURLs);
```

### Extract all URLs from Images

```javascript
// Function to extract all URLs from images on a website
function extractImageURLs() {
  const allURLs = [];

  // Retrieve all image elements on the page
  const imageElements = document.getElementsByTagName('img');

  // Extract URLs
  for (let i = 0; i < imageElements.length; i++) {
    const src = imageElements[i].src;

    // Add the image URL to the array
    allURLs.push(src);
  }

  return allURLs;
}

// Call the function to extract image URLs
const imageURLs = extractImageURLs();

// Log the extracted image URLs to the console
console.log('Extracted Image URLs:', imageURLs);
```

### Extract all URLs from Scripts

```javascript
// Function to extract all URLs from scripts on a website
function extractScriptURLs() {
  const allURLs = [];

  // Retrieve all script elements on the page
  const scriptElements = document.getElementsByTagName('script');

  // Extract URLs
  for (let i = 0; i < scriptElements.length; i++) {
    const src = scriptElements[i].src;

    // Add the script URL to the array
    allURLs.push(src);
  }

  return allURLs;
}

// Call the function to extract script URLs
const scriptURLs = extractScriptURLs();

// Log the extracted script URLs to the console
console.log('Extracted Script URLs:', scriptURLs);
```

### Extract all URLs from Stylesheets

```javascript
// Function to extract all URLs from stylesheets on a website
function extractStylesheetURLs() {
  const allURLs = [];

  // Retrieve all link elements on the page
  const linkElements = document.getElementsByTagName('link');

  // Extract URLs
  for (let i = 0; i < linkElements.length; i++) {
    const href = linkElements[i].href;

    // Add the stylesheet URL to the array
    allURLs.push(href);
  }

  return allURLs;
}

// Call the function to extract stylesheet URLs
const stylesheetURLs = extractStylesheetURLs();

// Log the extracted stylesheet URLs to the console
console.log('Extracted Stylesheet URLs:', stylesheetURLs);
```

### Extract all URLs from AJAX or Fetch Requests

```javascript
// Function to extract all URLs from dynamically loaded resources via AJAX or fetch requests
function extractDynamicURLs(urls) {
  const allURLs = [];

  // Retrieve all AJAX or fetch request URLs
  const requestURLs = [...urls];

  // Extract URLs
  for (let i = 0; i < requestURLs.length; i++) {
    const url = requestURLs[i];

    // Add the URL to the array
    allURLs.push(url);
  }

  return allURLs;
}

// Example array of AJAX or fetch request URLs
const ajaxURLs = ['https://somesite.com/api/data', 'https://somesite.com/api/users'];

// Call the function to extract URLs from AJAX or fetch requests
const dynamicURLs = extractDynamicURLs(ajaxURLs);

// Log the extracted URLs to the console
console.log('Extracted URLs from AJAX or Fetch Requests:', dynamicURLs);
```

### Extract all URLs from Attachments or Downloadable Files

```javascript
// Function to extract all URLs from attachments or downloadable files on a website
function extractAttachmentURLs() {
  const allURLs = [];

  // Retrieve all attachment or downloadable file elements on the page
  const attachmentElements = document.querySelectorAll('a[download], a[href*=".pdf

"], a[href*=".doc"], a[href*=".xls"], a[href*=".zip"]');

  // Extract URLs
  for (let i = 0; i < attachmentElements.length; i++) {
    const href = attachmentElements[i].href;

    // Add the attachment URL to the array
    allURLs.push(href);
  }

  return allURLs;
}

// Call the function to extract attachment URLs
const attachmentURLs = extractAttachmentURLs();

// Log the extracted attachment URLs to the console
console.log('Extracted Attachment URLs:', attachmentURLs);
```
