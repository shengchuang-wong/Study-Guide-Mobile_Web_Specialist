# mobile-web-specialist-study-guide

## Sections
- [Basic website layout and styling](#basic-website-layout-and-styling)
- [Front end networking](#front-end-networking)
- [Accessibility](#accessibility)
- [Progressive Web Apps](#progressive-web-apps)
- [Performance optimization and caching](#performance-optimization-and-caching)
- [Testing and debugging](#testing-and-debugging)
- [Mobile web forms](#mobile-web-forms)

## Basic website layout and styling
Users expect responsive and visually engaging websites regardless of the device. A web application's layout and styling must respond to the current display, while continuing to provide intuitive functionality. You'll be asked to show you can use HTML, CSS, and JavaScript to build a web application’s responsive layout and style that includes:

- DOM elements that are accessed and manipulated using only JavaScript without the overhead of libraries or frameworks (such as jQuery)
- Appropriate document type declaration and viewport tags
- A responsive grid-based layout using CSS
- Media queries that provide fluid breakpoints across different screen sizes
- Multimedia tags to display video or play audio
- Responsive images that adjust for the dimensions and resolution of any mobile device
- Touch and mouse events that contain large hit targets on the front end and work regardless of platform

### Resources:
1. [Codelabs -> Responsive design](https://codelabs.developers.google.com/codelabs/pwa-responsive-design/index.html?index=..%2F..dev-pwa-training#0)

#### Viewport meta tag
- `<meta name="viewport" content="width=device-width, initial-scale=1">`

#### Media query
```css
@media screen and (max-width: 48rem) {
  .container .col {
    width: 95%;
  }
}
```

#### Flex and css prefix
[What CSS to prefix](http://shouldiprefix.com/#flexbox)
```css
.container {
  display: -webkit-box;  /* OLD - iOS 6-, Safari 3.1-6 */
  display: -ms-flexbox;  /* TWEENER - IE 10 */
  display: flex;         /* NEW, Spec - Firefox, Chrome, Opera */
  background: #eee;  
  overflow: auto;
}

.container .col {
  flex: 1;
  padding: 1rem;
}
```

#### No Flexbox - fallback support
[Modernizr](https://modernizr.com/docs)

2. [Codelabs -> Responsive images](https://codelabs.developers.google.com/codelabs/pwa-responsive-images/index.html?index=..%2F..dev-pwa-training#0)

#### Responsive image
- `sizes` value matches the image's `max-width`
```html
<img src="images/sfo-500_small.jpg" srcset="images/sfo-1600_large.jpg 1600w, images/sfo-1000_large.jpg 1000w, images/sfo-800_medium.jpg 800w, images/sfo-500_small.jpg 500w" sizes="50vw" alt="View from aircraft window near San Francisco airport" />
```

```css
@media screen and (max-width: 700px) {
  img#sfo {
    max-width: 90vw;
    width: 90vw;
  }
}

html
sizes="(max-width: 700px) 90vw, 50vw"
```
#### Picture ELement
```html
<figure>
    <picture>
    <source media="(min-width: 750px)"
            srcset="images/horses-1600_large_2x.jpg 2x,
                    images/horses-800_large_1x.jpg" />
    <source media="(min-width: 500px)"
            srcset="images/horses_medium.jpg" />
    <img src="images/horses_small.jpg" alt="Horses in Hawaii">
    </picture>
    <figcaption>Horses in Hawaii</figcaption>
</figure>
```

3. [Web Fundamentals -> Video](https://developers.google.com/web/fundamentals/media/video)

#### Video Element Tag
```html
<video controls>
  <source src="https://storage.googleapis.com/webfundamentals-assets/videos/chrome.webm" type="video/webm">
  <source src="https://storage.googleapis.com/webfundamentals-assets/videos/chrome.mp4" type="video/mp4">
  <p>This browser does not support the video element.</p>
</video>
```

#### Speficy video start and end time
`<source src="video/chrome.webm#t=5,10" type="video/webm">`

#### Include a poster image for video
```html
<video poster="poster.jpg" ...>
  ...
</video>
```

#### Track element for accessibility
```html
<video controls>
  <source src="https://storage.googleapis.com/webfundamentals-assets/videos/chrome.webm" type="video/webm" />
  <source src="https://storage.googleapis.com/webfundamentals-assets/videos/chrome.mp4" type="video/mp4" />
  <track src="chrome-subtitles-en.vtt" label="English captions"
         kind="captions" srclang="en" default>
  <p>This browser does not support the video element.</p>
</video>
```
- [Mobile Web Video Playback
](https://developers.google.com/web/fundamentals/media/mobile-web-video-playback)
- [Control fullscreen](https://developers.google.com/web/fundamentals/media/video#control_fullscreening_of_content)

4. [https://developers.google.com/web/fundamentals/design-and-ux/responsive/](https://developers.google.com/web/fundamentals/design-and-ux/responsive/)
5. [Web Fundamentals -> Add Touch to Your Site](https://developers.google.com/web/fundamentals/design-and-ux/input/touch/)

## Front end networking
Because user engagement depends on reliable and effective network requests, you'll be asked to show you can use JavaScript to set up reliable front end networking protocols by:

- Requesting data using `fetch()`
- Checking response status, then parsing the data into usable format
- Rendering response data to a page
- Configuring `POST` requests to a database with `method` and `body` parameters
- Using correctly configured cross-origin resource sharing protocol (CORS) `fetch` requests, depending on the server’s response headers
- Handling `fetch()` request errors with promise chaining
- Diagnosing network issues using debugging and development tools

### Resources:
1. [Codelabs -> Fetch API](https://developers.google.com/certification/mobile-web-specialist/study-guide/networking)

#### Fetching a resource
```js
function fetchJSON() {
  fetch('examples/animals.json')
    .then(logResult)
    .catch(logError);
}
```

#### Fetch an image
```js
function fetchImage() {
  fetch('examples/fetching.jpg')
    .then(validateResponse)
    .then(readResponseAsBlob)
    .then(showImage)
    .catch(logError);
}
```

```js
function readResponseAsBlob(response) {
  return response.blob();
}
```

```js
function showImage(responseAsBlob) {
  const container = document.getElementById('img-container');
  const imgElem = document.createElement('img');
  container.appendChild(imgElem);
  const imgUrl = URL.createObjectURL(responseAsBlob);
  imgElem.src = imgUrl;
}
```

#### Using HEAD requests
```js
function headRequest() {
  fetch('examples/words.txt', {
    method: 'HEAD'
  })
  .then(validateResponse)
  .then(readResponseAsText)
  .then(logResult)
  .catch(logError);
}
```

## Accessibility
Web pages and applications should be accessible to all users, including those with visual, motor, hearing, and cognitive impairments. Using HTML, CSS, JavaScript, you'll be asked to show you can integrate accessibility best practices into your web pages and applications by:

- Using a logical tab order for tabbed navigation
- Using skip navigation links to bypass navbars and asides
- Avoiding hidden content on the page that impedes tab navigation
- Using heading tags that provide a logical page structure
- Using text alternatives to visual content, such as `alt`, `<label>`, `aria-label`, and `aria-labelledby`
- Applying color contrast to all elements and following accessibility best practices
- Sending timely alerts for urgent messages using `aria-live`
- Using semantic markup to keep content and presentation separate when appropriate

### Resources:
1. [Web Fundamentals -> Introduction to Focus](https://developers.google.com/web/fundamentals/accessibility/focus/)

tabindex="0": Inserts an element into the natural tab order. The element can be focused by pressing the Tab key, and the element can be focused by calling its focus() method
`<custom-button tabindex="0">Press Tab to Focus Me!</custom-button>`


tabindex="-1": Removes an element from the natural tab order, but the element can still be focused by calling its focus() method
```html
<button id="foo" tabindex="-1">I'm not keyboard focusable</button>
<button onclick="foo.focus();">Focus my sibling</button>
```

2. [Web Fundamentals -> Introduction to Semantics](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/)
- The element's role or type, if it is specified (it should be).
- The element's name, if it has one (it should).
- The element's value, if it has one (it may or may not).
- The element's state, e.g., whether it is enabled or disabled (if applicable).

3. [Web Fundamentals -> The Accessibility Tree](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/the-accessibility-tree)
4. [Web Fundamentals -> Text Alternatives for Images](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/text-alternatives-for-images)

On the other hand, it's not always useful to describe an image. For example, consider a magnifying glass image inside a search button that has the text "Search". If the text wasn't there, you would definitely give that image an alt value of "search". But because we have the visible text, the screen reader will pick up and read aloud the word "search"; thus, an identical alt value on the image is redundant.

However, we know that if we leave the alt text out, we'll probably hear the image file name instead, which is both useless and potentially confusing. In this case you can just use an empty alt attribute, and the screen reader will skip the image altogether.

`<img src="magnifying-glass.jpg" alt="">`

To summarize, all images should have an alt attribute, but they need not all have text. Important images should have descriptive alt text that succinctly describes what the image is, while decorative images should have empty alt attributes — that is, `alt=""`.


5. [Web Fundamentals -> Aria Labels and Relationships](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/aria-labels-and-relationships)
6. [Web Fundamentals -> Accessible Styles](https://developers.google.com/web/fundamentals/accessibility/accessible-styles)
7. [Web Fundamentals -> Hiding and Updating Content](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/hiding-and-updating-content) <<< read this, sounds important

`aria-live` has three allowable values: polite, assertive, and off.

`aria-live="polite"` tells assistive technology to alert the user to this change when it has finished whatever it is currently doing. It's great to use if something is important but not urgent, and accounts for the majority of aria-live use.
`aria-live="assertive"` tells assistive technology to interrupt whatever it's doing and alert the user to this change immediately. This is only for important and urgent updates, such as a status message like "There has been a server error and your changes are not saved; please refresh the page", or updates to an input field as a direct result of a user action, such as buttons on a stepper widget.
`aria-live="off"` tells assistive technology to temporarly suspend aria-live interruptions.

## Progressive Web Apps
Users expect native applications to be available offline and provide a feature- rich experience that is launchable from their home page. You'll be asked to show that you can use service workers, HTML, and JavaScript to build out Progressive Web App features similar to native applications by:

- Creating a web app that is available offline, and that caches elements by routing requests through a service worker
- Storing the default display orientation, theme color, display icon (add to home screen), and splash screen in the web application manifest (or using meta tags)
- Separating critical application functionality and UI into an application shell that can be loaded independently from the content

### Resources:
1. [Codelab -> Scripting the service worker](https://codelabs.developers.google.com/codelabs/pwa-scripting-the-service-worker/index.html?index=..%2F..dev-pwa-training#0)

#### Register service worker
```js
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('service-worker.js')
    .then(registration => {
      console.log('Service Worker is registered', registration);
    })
    .catch(err => {
      console.error('Registration failed:', err);
    });
  });
}
```

#### Install and activate service worker
```js
self.addEventListener('install', event => {
  console.log('Service worker installing...');
  // Add a call to skipWaiting here
});

self.addEventListener('activate', event => {
  console.log('Service worker activating...');
});
```

In service-worker.js, add a call to skipWaiting in the install event listener:
`self.skipWaiting();`

#### Fetch event
```js
self.addEventListener('fetch', event => {
  console.log('Fetching:', event.request.url);
});
```

#### Service worker scope
```js
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('service-worker.js')
    .then(registration => {
      console.log('SW registered with scope:', registration.scope);
    })
    .catch(err => {
      console.error('Registration failed:', err);
    });
  });
}

navigator.serviceWorker.register('/service-worker.js', {
  scope: '/kitten/'
});
```

2. [Codelab -> Caching files with the service worker](https://codelabs.developers.google.com/codelabs/pwa-caching-service-worker/index.html?index=..%2F..dev-pwa-training#0)

#### Install event, cache file
```js
const filesToCache = [
  '/',
  'style/main.css',
  'images/still_life_medium.jpg',
  'index.html',
  'pages/offline.html',
  'pages/404.html'
];

const staticCacheName = 'pages-cache-v1';

self.addEventListener('install', event => {
  console.log('Attempting to install service worker and cache static assets');
  event.waitUntil(
    caches.open(staticCacheName)
    .then(cache => {
      return cache.addAll(filesToCache);
    })
  );
});
```

#### Serve file from the cache
```js
self.addEventListener('fetch', event => {
  console.log('Fetch event for ', event.request.url);
  event.respondWith(
    caches.match(event.request)
    .then(response => {
      if (response) {
        console.log('Found ', event.request.url, ' in cache');
        return response;
      }
      console.log('Network request for ', event.request.url);
      return fetch(event.request)

      // TODO 4 - Add fetched files to the cache

    }).catch(error => {

      // TODO 6 - Respond with custom offline page

    })
  );
});
```

#### Add network response to the cache
```js
.then(response => {
  // TODO 5 - Respond with custom 404 page
  return caches.open(staticCacheName).then(cache => {
    cache.put(event.request.url, response.clone());
    return response;
  });
});
```

#### Delete outdated cache
```js
self.addEventListener('activate', event => {
  console.log('Activating new service worker...');

  const cacheWhitelist = [staticCacheName];

  event.waitUntil(
    caches.keys().then(cacheNames => {
      return Promise.all(
        cacheNames.map(cacheName => {
          if (cacheWhitelist.indexOf(cacheName) === -1) {
            return caches.delete(cacheName);
          }
        })
      );
    })
  );
});
```
Change the name of the cache to "pages-cache-v2":
`var staticCacheName = 'pages-cache-v2';`

3. [Codelab -> Offline quickstart](https://codelabs.developers.google.com/codelabs/pwa-offline-quickstart/index.html?index=..%2F..dev-pwa-training#0)

#### Precache resources
```js
const cacheName = 'cache-v1';
const precacheResources = [
  '/',
  'index.html',
  'styles/main.css',
  'images/space1.jpg',
  'images/space2.jpg',
  'images/space3.jpg'
];

self.addEventListener('install', event => {
  console.log('Service worker install event!');
  event.waitUntil(
    caches.open(cacheName)
      .then(cache => {
        return cache.addAll(precacheResources);
      })
  );
});

self.addEventListener('activate', event => {
  console.log('Service worker activate event!');
});

self.addEventListener('fetch', event => {
  console.log('Fetch intercepted for:', event.request.url);
  event.respondWith(caches.match(event.request)
    .then(cachedResponse => {
        if (cachedResponse) {
          return cachedResponse;
        }
        return fetch(event.request);
      })
    );
});
```

Manifest.json
```json
{
  "name": "Space Missions",
  "short_name": "Space Missions",
  "lang": "en-US",
  "start_url": "/index.html",
  "display": "standalone",
  "theme_color": "#FF9800",
  "background_color": "#FF9800",
  "icons": [
    {
      "src": "images/touch/icon-128x128.png",
      "sizes": "128x128"
    },
    {
      "src": "images/touch/icon-192x192.png",
      "sizes": "192x192"
    },
    {
      "src": "images/touch/icon-256x256.png",
      "sizes": "256x256"
    },
    {
      "src": "images/touch/icon-384x384.png",
      "sizes": "384x384"
    },
    {
      "src": "images/touch/icon-512x512.png",
      "sizes": "512x512"
    }
  ]
}
```

Manifest in HTML
```html
<link rel="manifest" href="manifest.json">

<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="application-name" content="Space Missions">
<meta name="apple-mobile-web-app-title" content="Space Missions">
<meta name="theme-color" content="#FF9800">
<meta name="msapplication-navbutton-color" content="#FF9800">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="msapplication-starturl" content="/index.html">
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

<link rel="icon" sizes="128x128" href="/images/touch/icon-128x128.png">
<link rel="apple-touch-icon" sizes="128x128" href="/images/touch/icon-128x128.png">
<link rel="icon" sizes="192x192" href="icon-192x192.png">
<link rel="apple-touch-icon" sizes="192x192" href="/images/touch/icon-192x192.png">
<link rel="icon" sizes="256x256" href="/images/touch/icon-256x256.png">
<link rel="apple-touch-icon" sizes="256x256" href="/images/touch/icon-256x256.png">
<link rel="icon" sizes="384x384" href="/images/touch/icon-384x384.png">
<link rel="apple-touch-icon" sizes="384x384" href="/images/touch/icon-384x384.png">
<link rel="icon" sizes="512x512" href="/images/touch/icon-512x512.png">
<link rel="apple-touch-icon" sizes="512x512" href="/images/touch/icon-512x512.png">
```

#### Manual prompt installation
```html
<section id="installBanner" class="banner">
    <button id="installBtn">Install app</button>
</section>
```

```css
.banner {
  align-content: center;
  display: none;
  justify-content: center;
  width: 100%;
}
```

```js
<script>
    let deferredPrompt;
    window.addEventListener('beforeinstallprompt', event => {

      // Prevent Chrome 67 and earlier from automatically showing the prompt
      event.preventDefault();

      // Stash the event so it can be triggered later.
      deferredPrompt = event;

      // Attach the install prompt to a user gesture
      document.querySelector('#installBtn').addEventListener('click', event => {

        // Show the prompt
        deferredPrompt.prompt();

        // Wait for the user to respond to the prompt
        deferredPrompt.userChoice
          .then((choiceResult) => {
            if (choiceResult.outcome === 'accepted') {
              console.log('User accepted the A2HS prompt');
            } else {
              console.log('User dismissed the A2HS prompt');
            }
            deferredPrompt = null;
          });
      });

      // Update UI notify the user they can add to home screen
      document.querySelector('#installBanner').style.display = 'flex';
    });
  </script>
```

4. [Codelab -> Adding a Service Worker and Offline into your Web App](https://codelabs.developers.google.com/codelabs/offline/index.html?index=..%2F..%2Findex#0)
5. [Web Fundamentals -> The App Shell Model](https://developers.google.com/web/fundamentals/architecture/app-shell)

## Performance optimization and caching
Mobile users demand websites that load nearly instantly, despite poor or absent connectivity. Because many users also face expensive data caps, you must minimize their application's data footprint to reduce page load time as much as possible. You'll be asked to show you can carry out performance audits on applications to reduce page load times and maintain responsive user experiences by:

- Preventing main thread blocking with a dedicated web worker
- Providing an optimized critical rendering path using:
- Compressed or minified JavaScript, HTML and CSS files to reduce render blocking
- Inline CSS for essential styles on a specific page, with asynchronous loading for additional styles as necessary
- Inline JavaScript files for initial rendering only where necessary (or otherwise eliminated, deferred, or marked as `async`)
- Ordered loading of remaining critical resources and early download of all critical assets to shorten the critical path -length
- Reduced DOM depth to minimize browser layout/reflow
- Your browser's developer tools to diagnose performance issues on mobile devices
-Prefetching files that load when resources are available, reducing the time to meaningful interaction
- Providing client storage that is appropriate to a web application’s data persistence needs, including:
- Session state management
- Asset caching based on their impact on load time and offline functionality
- Using IndexedDB to store dynamic content in offline mode

### Resources:
1. [Codelab -> IndexedDB API(https://codelabs.developers.google.com/codelabs/pwa-indexed-db/index.html?index=..%2F..dev-pwa-training#0)

#### Check for IndexedDB support
```js
if (!('indexedDB' in window)) {
  console.log('This browser doesn\'t support IndexedDB');
  return;
}
```

#### Create IndexedDB database
`var dbPromise = idb.open('couches-n-things', 1);`

#### Create object store (table) in database
```js
var dbPromise = idb.open('couches-n-things', 2, function(upgradeDb) {
  switch (upgradeDb.oldVersion) {
    case 0:
      // a placeholder case so that the switch block will 
      // execute when the database is first created
      // (oldVersion is 0)
    case 1:
      console.log('Creating the products object store');
      upgradeDb.createObjectStore('products', {keyPath: 'id'});

    // TODO 4.1 - create 'name' index

    // TODO 4.2 - create 'price' and 'description' indexes

    // TODO 5.1 - create an 'orders' object store

  }
});
```

#### Add items into object store
```js
dbPromise.then(function(db) {
  var tx = db.transaction('products', 'readwrite');
  var store = tx.objectStore('products');
  var items = [
    {
      name: 'Couch',
      id: 'cch-blk-ma',
      price: 499.99,
      color: 'black',
      material: 'mahogany',
      description: 'A very comfy couch',
      quantity: 3
    },
    {
      name: 'Armchair',
      id: 'ac-gr-pin',
      price: 299.99,
      color: 'grey',
      material: 'pine',
      description: 'A plush recliner armchair',
      quantity: 7
    }
  ];
  return Promise.all(items.map(function(item) {
      console.log('Adding item: ', item);
      return store.add(item);
    })
  ).catch(function(e) {
    tx.abort();
    console.log(e);
  }).then(function() {
    console.log('All items added successfully!');
  });
});
```

#### Create an index
```js
case 2:
  console.log('Creating a name index');
  var store = upgradeDb.transaction.objectStore('products');
  store.createIndex('name', 'name', {unique: true});
```

#### Get method with index
```js
return dbPromise.then(function(db) {
  var tx = db.transaction('products', 'readonly');
  var store = tx.objectStore('products');
  var index = store.index('name');
  return index.get(key);
});
```

#### Cursor - range between
```js
var lower = document.getElementById('priceLower').value;
var upper = document.getElementById('priceUpper').value;
var lowerNum = Number(document.getElementById('priceLower').value);
var upperNum = Number(document.getElementById('priceUpper').value);

if (lower === '' && upper === '') {return;}
var range;
if (lower !== '' && upper !== '') {
  range = IDBKeyRange.bound(lowerNum, upperNum);
} else if (lower === '') {
  range = IDBKeyRange.upperBound(upperNum);
} else {
  range = IDBKeyRange.lowerBound(lowerNum);
}
var s = '';
dbPromise.then(function(db) {
  var tx = db.transaction('products', 'readonly');
  var store = tx.objectStore('products');
  var index = store.index('price');
  return index.openCursor(range);
}).then(function showRange(cursor) {
  if (!cursor) {return;}
  console.log('Cursored at:', cursor.value.name);
  s += '<h2>Price - ' + cursor.value.price + '</h2><p>';
  for (var field in cursor.value) {
    s += field + '=' + cursor.value[field] + '<br/>';
  }
  s += '</p>';
  return cursor.continue().then(showRange);
}).then(function() {
  if (s === '') {s = '<p>No results.</p>';}
  document.getElementById('results').innerHTML = s;
});
```

#### Process function
```js
return dbPromise.then(function(db) {
  var tx = db.transaction('products');
  var store = tx.objectStore('products');
  return Promise.all(
    orders.map(function(order) {
      return store.get(order.id).then(function(product) {
        return decrementQuantity(product, order);
      });
    })
  );
});
```

#### Process function - more
```js
return new Promise(function(resolve, reject) {
  var item = product;
  var qtyRemaining = item.quantity - order.quantity;
  if (qtyRemaining < 0) {
    console.log('Not enough ' + product.id + ' left in stock!');
    document.getElementById('receipt').innerHTML =
    '<h3>Not enough ' + product.id + ' left in stock!</h3>';
    throw 'Out of stock!';
  }
  item.quantity = qtyRemaining;
  resolve(item);
});
```


2. [Supercharged Youtube series -> Web Workers(https://www.youtube.com/watch?v=X57mh8tKkgE)

Main.js
```js
window.addEventListener('load', () => {

  const webWorker = new Worker('web-worker.js')

  webWorker.addEventListener('message', (message) => {
    console.log({messageFromMain: message.data})
  })

  document.getElementById('myButton').addEventListener('click', () => {
    webWorker.postMessage('myMessage')
  })
})
```

web-worker.js
```js
self.addEventListener('message', message => {
  console.log({
    messageInWebWorker: message.data
  })

  postMessage(message.data)
})
```


3. [Web Fundamentals -> Why Performance Matters(https://developers.google.com/web/fundamentals/performance/why-performance-matters/)

#### Remark - study about preload, prefetch, preconnect, etc...

4. [Web Fundamentals -> Resource Prioritization(https://developers.google.com/web/fundamentals/performance/resource-prioritization)
5. [Web Tools -> Get Started with Analyzing Network Performance in Chrome DevTools(https://developers.google.com/web/tools/chrome-devtools/network-performance/)
6. [Web Tools -> Critical Request Chains(https://developers.google.com/web/tools/lighthouse/audits/critical-request-chains)

## Testing and debugging
Developers typically work in highly iterative deployment environments, relying on extensive testing and debugging to maintain functionality and code integrity. You'll be asked to show that you can verify expected behaviors and diagnose common web application bugs by:

- Writing unit tests that first verify a function’s intended behavior, and then iteratively modifying its code until it passes those tests
- Setting breakpoints within a complicated function to determine exactly where it deviates from expected behavior
- Using console logs to output relevant debugging information
- Reproducing and fixing bugs based on user reported issues

### Resources:
1. [Web Fundamentals -> Debugging Service Workers](https://developers.google.com/web/fundamentals/codelabs/debugging-service-workers/)

#### Push notification? 
- https://codelabs.developers.google.com/codelabs/debugging-service-workers/#6

2. [Web Tools -> Chrome Dev Tools](https://developers.google.com/web/tools/chrome-devtools/)
3. [Web Tools -> Get Started with Debugging JavaScript in Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/javascript/)
4. [Web Tools -> Diagnose and Log to Console](https://developers.google.com/web/tools/chrome-devtools/console/console-write)

## ES2015 concepts and syntax
Web developers must stay current with the latest JavaScript features that promote simpler and more readable code. With polyfills enabling code written in ES2015 JavaScript to be used in unsupported browsers, there is a strong incentive for developers to begin using the new features and syntax. You'll be asked to show that you understand and can write ES2015 JavaScript code using:

- JavaScript promises with ES2015 syntax that create asynchronous functions and incorporate graceful error handling
- Variables that can be used with block scope, function scope, and made immutable depending on context using `let`, `var`, and `const`
- String literals that include string interpolation and multi-line strings
- Arrow functions that create anonymous functions and use an unbounded `this`
- Default function parameters that initialize default values for a function when no argument or `undefined` is provided
`for...of` loops that can iterate over any iterable object while running a custom function on each
- Maps that allow for arbitrary key and value pairs that are iterable and include non-string keys
- Sets that contain only unique, iterable elements where an array would degrade performance

### Resources:
1. [Codelabs -> Promises](https://codelabs.developers.google.com/codelabs/pwa-promises/index.html?index=..%2F..dev-pwa-training#0)

#### Promises
```js
function getImageName(country) {
  country = country.toLowerCase();
  const promiseOfImageName = new Promise((resolve, reject) => {
    setTimeout(() => {
      if (country === 'spain' || country === 'chile' || country === 'peru') {
        resolve(country + '.png');
      } else {
        reject(Error('Didn\'t receive a valid country name!'));
      }
    }, 1000);
  });
  console.log(promiseOfImageName);
  return promiseOfImageName;    
}
```

#### Promises from scratch
```js
const promise = new Promise((resolve, reject) => {
  // do a thing, possibly async, then...

  if (/* everything turned out fine */) {
    resolve("Stuff worked!");
  }
  else {
    reject(Error("It broke"));
  }
});
```

#### Promises race 
```js
var promises = [
  getImageName('Spain'),
  getImageName('Chile'),
  getImageName('Peru')
];

allFlags(promises).then(function(result) {
  console.log(result);
});

const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, 'one');
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'two');
});

Promise.race([promise1, promise2])
.then(logSuccess)
.catch(logError);
```

2. [Codelabs -> Build your first ES2015/ES6 application](https://codelabs.developers.google.com/codelabs/chrome-es2015/)
3. [Web Fundamentals -> JavaScript Promises: an Introduction](https://developers.google.com/web/fundamentals/getting-started/primers/promises)

## Mobile web forms
Filling out online forms, especially on mobile devices, can be difficult. To improve the user experience you'll be asked to show that you can use basic HTML5, JavaScript, and the HTML5 Constraint Validation API, to design efficient and secure HTML web forms with:

- Appropriate `label` tags associated with inputs
- Inputs with appropriate `type`, `name` and `autocomplete` attributes
- Inputs with large touch targets for mobile forms
- Suggestions for user input using the `datalist` element
- Front-end validation of inputs (e.g., `pattern`, `maxlength`, `required`) and DOM elements, including:
- Checking validation errors in real-time with pseudo-classes on inputs
- Form validation prior to submission (Constraint Validation API)

### Resources:
1. [Web Fundamentals -> Create Amazing Forms](https://developers.google.com/web/fundamentals/design-and-ui/input/forms/)
