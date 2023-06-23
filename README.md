# JavaScript - Newbie Cheatsheet | Hacking

### Where Legends Emerge, Leaving No Room For Two! Just one can be Nr1 💜

***

 Welcome, fellow coding enthusiasts, to the JavaScript Newbie Cheatsheet Hacking repository! I'm just a JavaScript newbie, bumbling and stumbling my way through the mesmerizing maze of coding. Along the way, I've managed to bungle into some pretty handy tips and tricks, and in the spirit of sharing, I've decided to spill all my beans right here!

 Over time, as a dedicated tinkerer, I've embraced the wild and wonderful world of JavaScript, using it to poke and prod my own websites, tickle my routers (with their express consent, of course), and more. My syntax? Far from perfect. My code? A delightful hot mess of "wuziduzi world" meets "wuseman's spaghetti that just somehow works". And yet, the discoveries I've made have been astonishing.

 I'm no expert in JavaScript. Heck, I wouldn't even know where to start. But these haphazardly stumbled-upon techniques have served me well, and I reckon there might be a few nuggets of wisdom to be found in my "accidentally-on-purpose" explorations. Hence, the birth of this repository.

This mish-mash of tips and tricks spans across various topics, without any particular focus on a specific level of expertise. They are simply based on my own exhilarating journey of eureka moments and facepalms. I won't be giving detailed lectures here - just quick, practical, ready-to-use snippets that you can plug into your own adventures in code.

 A note of caution though - these tips and tricks may not play nice with unauthorized or not-owned-by-you websites. They've been exclusively tested and tailored to my own online playgrounds. If you choose to release them into the wild, please be responsible and respectful of others' digital territories. I sternly discourage any and all forms of unauthorized activities.

 So, without further ado, enjoy this hotchpotch of JavaScript tips and tricks, handpicked from my personal adventures. If you'd like to contribute, that's great! Just make sure to add your bits in the right order. Spotted a bug? Let me know! I'm always up for a good bug hunt.

***

Remember my dear comrades: hack to learn, **NOT** learn to hack! - **Happy hacking!**

***

## URL Wise

<details>
  <summary>Extracting URLs from a Web Page</summary>

```javascript
Array.from(document.links).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Extracting URLs using Destructuring (Alternative 1)</summary>

```javascript
Array.from(document.links, ({ href }) => href).forEach(console.log);
```

</details>

<details>
  <summary>Extracting URLs using the Spread Operator (Alternative 2)</summary>

```javascript
[...document.getElementsByTagName('a')].forEach(a => console.log(a.href));
```

</details>

<details>
  <summary>Extracting URLs using Array.from with Mapping (Alternative 3)</summary>

```javascript
Array.from(document.getElementsByTagName('a'), a => a.href).forEach(url => console.log(url));
```

</details>

<details>
  <summary>Extracting URLs using a for...of Loop (Alternative 4)</summary>

```javascript
var urls = Array.from(document.getElementsByTagName('a'));
for (var url of urls) {
    console.log(url.href);
}
```

</details>

<details>
  <summary>Extracting All Emails from a Web Page</summary>

```javascript
const regex = /\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[0]);
}
```

</details>

<details>
  <summary>Get all image URLs from a web page</summary>

```javascript
Array.from(document.images).forEach(({ src }) => console.log(src));
```

</details>

<details>
  <summary>Get all CSS File URLs</summary>

```javascript
Array.from(document.styleSheets).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all internal URLs from a web page</summary>

```javascript
Array.from(document.links).filter(a => a.hostname === location.hostname).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all external URLs from a web page</summary>

```javascript
Array.from(document.links).filter(a => a.hostname !== location.hostname).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all unique URLs from a web page</summary>

```javascript
let uniqueURLs = new Set(Array.from(document.links).map(({ href }) => href));
uniqueURLs.forEach(url => console.log(url));
```

</details>

<details>
  <summary>Get all PDF files from a web page</summary>

```javascript
Array.from(document.links).filter(a => a.href.endsWith('.pdf')).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all file download links</summary>

```javascript
Array.from(document.querySelectorAll('a[download]')).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all mailto links</summary>

```javascript
Array.from(document.querySelectorAll('a[href^="mailto:"]')).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all tel links</summary>

```javascript
Array.from(document.querySelectorAll('a[href^="tel:"]')).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all URLs having certain text</summary>

```javascript
Array.from(document.links).filter(a => a.innerText.includes('text')).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get all hashtags from a webpage</summary>

```javascript
Array.from(document.querySelectorAll('a[href^="#"]')).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Get URLs of all open tabs</summary>

```javascript
chrome.tabs.query({}, function(tabs) {
  tabs.forEach(tab => console.log(tab.url));
});
```

</details>

<details>
  <summary>Get URLs of all iframes on a page</summary>

```javascript
Array.from(document.querySelectorAll('iframe')).forEach(({ src }) => console.log(src));
```

</details>


<details>
  <summary>Find all src URLs</summary>

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

</details>

<details>
  <summary>Get all URLs (XPath)</summary>

```javascript
const xpathResult = document.evaluate('//a', document, null, XPathResult.ANY_TYPE, null);
let node = xpathResult.iterateNext();
while (node) {
  console.log(node.href);
  node = xpathResult.iterateNext();
}
```

</details>

<details>
  <summary>Get all URLs (jQuery)</summary>

```javascript
document.querySelectorAll('a').forEach(function(a) {
  console.log(a.href);
});
```

</details>

<details>
  <summary>Get all URLs (Alternative 7: Regular Expression)</summary>

```javascript
const regex = /<a\s+(?:[^>]*?\s+)?href=(["'])(.*?)\1/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[2]);
}
```

</details>

<details>
  <summary>Get all URLs (Fetch API)</summary>

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

</details>

<details>
  <summary>Get All API Endpoints from JavaScript Files</summary>

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

</details>

<details>
  <summary>Get all URLs from CSS</summary>

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

</details>

<details>
  <summary>Extract URLs from Inline JavaScript</summary>

```javascript
const regex = /url\s*\(\s*(['"]?)(.*?)\1\s*\)/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[2]);
}
```

</details>

<details>
  <summary>Extracting URLs from HTML Comments</summary>

```javascript
const regex = /<!--.*?(\b

https?:\/\/\S+)\b.*?-->/g;
const html = document.documentElement.innerHTML;
let match;
while ((match = regex.exec(html))) {
  console.log(match[1]);
}
```

</details>

<details>
  <summary>Extract URLs from SVG</summary>

```javascript
Array.from(document.getElementsByTagName('image')).forEach(({ href }) => console.log(href));
```

</details>

<details>
  <summary>Extracting Specific Parts of a URL</summary>

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

</details>

<details>
  <summary>URL Redirection</summary>

```javascript
window.location.href = 'https://www.newurl.com';
```

</details>

<details>
  <summary>Add URL parameter</summary>

```javascript
function addUrlParameter(url, parameterName, parameterValue) {
  const separator = url.includes('?') ? '&' : '?';
  return url + separator + encodeURIComponent(parameterName) + '=' + encodeURIComponent(parameterValue);
}

const originalUrl = 'https://www.github.com/wuseman';
const modifiedUrl = addUrlParameter(originalUrl, 'param', 'value');
console.log(modifiedUrl);
```

</details>

<details>
  <summary>Remove URL Parameter</summary>

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

</details>

<details>
  <summary>Extract all URLs from a Website recursive (Separate Lines)</summary>

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

  //

 Retrieve all anchor elements on the page
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
</details>

<details>
  <summary>Extract all URLs from a Website (Filtered by Domain)</summary>

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

</details>

<details>
  <summary>Extract all URLs from a Website (External URLs Only)</summary>

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

</details>

<details>
  <summary>Extract all URLs from a Website (Unique URLs Only)</summary>

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

    // Check if the URL is already in the

 array
    if (allURLs.indexOf(href) === -1) {
      allURLs.push(href);
    }
  }

  return allURLs;
}

// Call the function to extract unique URLs
const uniqueURLs = extractUniqueURLs();

// Log the extracted unique URLs to the console
console.log('Extracted Unique URLs:', uniqueURLs);
```

</details>

<details>
  <summary>Extract all URLs from Images</summary>

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

</details>

<details>
  <summary>Extract all URLs from Scripts</summary>

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

</details>

<details>
  <summary>Extract all URLs from Stylesheets</summary>

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

</details>

<details>
  <summary>Extract all URLs from AJAX or Fetch Requests</summary>

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
const

 dynamicURLs = extractDynamicURLs(ajaxURLs);

// Log the extracted URLs to the console
console.log('Extracted URLs from AJAX or Fetch Requests:', dynamicURLs);
```

</details>

<details>
  <summary>Extract all URLs from Attachments or Downloadable Files</summary>

```javascript
// Function to extract all URLs from attachments or downloadable files on a website
function extractAttachmentURLs() {
  const allURLs = [];

  // Retrieve all attachment or downloadable file elements on the page
  const attachmentElements = document.querySelectorAll('a[download], a[href*=".pdf"], a[href*=".doc"], a[href*=".xls"], a[href*=".zip"]');

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
</details>

<details>
  <summary>Locate Users by ID Without Overloading the Website</summary>

This approach is designed to efficiently find the highest user ID when we do not have a clear starting point. It aims to avoid putting excessive load on the server, thus preventing a potentially negative impact on the site's performance.

```javascript
async function crawlUsersById(startId, endId) {
  for (let id = startId; id <= endId; id++) {
    const url = `https://somewebsite/api/v1/users/${id}`;

    try {
      const response = await fetch(url, {
        headers: {
          "accept": "application/json, text/plain, */*",
          "sec-ch-ua": "\"Not.A/Brand\";v=\"8\", \"Chromium\";v=\"114\", \"Google Chrome\";v=\"114\"",
        },
        referrer: `https://somewebsite.org/user/${id}/edit`,
        referrerPolicy: "strict-origin-when-cross-origin",
        method: "GET",
        mode: "cors",
        credentials: "include"
      });

      if (response.ok) {
        const userData = await response.json();
        console.log(userData);
        // Process the userData as needed
      } else {
        console.error(`Error retrieving user data for ID: ${id}`);
      }
    } catch (error) {
      console.error(`Error fetching user data for ID: ${id}`, error);
    }
  }
}

// Usage: crawlUsersById(startId, endId);
crawlUsersById(1, 999999);
```
</details>

<details>
  <summary>Optimized Search for the Last User ID on a Website</summary>

This method uses a balanced approach to discover the largest user ID on a website when there is no initial indication of its value. The strategy aims to minimize the potential strain on the website by avoiding excessive requests.

```javascript
async function findLastUser() {
  let startId = 10000;
  let endId = 12000;
  let lastUser = null;

  while (startId <= endId) {
    const midId = Math.floor((startId + endId) / 2);
    const url = `https://somewebsite/api/v1/users/${midId}`;

    try {
      const response = await fetch(url, {
        headers: {
          "accept": "application/json, text/plain, */*",
          "sec-ch-ua": "\"Not.A/

Brand\";v=\"8\", \"Chromium\";v=\"114\", \"Google Chrome\";v=\"114\"",
        },
        referrer: `https://somewebsite/user/${midId}/edit`,
        referrerPolicy: "strict-origin-when-cross-origin",
        method: "GET",
        mode: "cors",
        credentials: "include"
      });

      if (response.ok) {
        lastUser = midId;
        startId = midId + 1;
      } else if (response.status === 404) {
        endId = midId - 1;
      } else {
        console.error(`Error retrieving user data for ID: ${midId}`);
        break;
      }
    } catch (error) {
      console.error(`Error fetching user data for ID: ${midId}`, error);
      break;
    }
  }

  console.log(`Last user found with ID: ${lastUser}`);
}

// Usage: findLastUser();
findLastUser();
```

</details>


## Crawling 
