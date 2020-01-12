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
5. [Web Fundamentals -> Aria Labels and Relationships](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/aria-labels-and-relationships)
6. [Web Fundamentals -> Accessible Styles](https://developers.google.com/web/fundamentals/accessibility/accessible-styles)
7. [Web Fundamentals -> Hiding and Updating Content](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/hiding-and-updating-content) <<< read this, sounds important

aria-live has three allowable values: polite, assertive, and off.

aria-live="polite" tells assistive technology to alert the user to this change when it has finished whatever it is currently doing. It's great to use if something is important but not urgent, and accounts for the majority of aria-live use.
aria-live="assertive" tells assistive technology to interrupt whatever it's doing and alert the user to this change immediately. This is only for important and urgent updates, such as a status message like "There has been a server error and your changes are not saved; please refresh the page", or updates to an input field as a direct result of a user action, such as buttons on a stepper widget.
aria-live="off" tells assistive technology to temporarly suspend aria-live interruptions.

## Progressive Web Apps
Users expect native applications to be available offline and provide a feature- rich experience that is launchable from their home page. You'll be asked to show that you can use service workers, HTML, and JavaScript to build out Progressive Web App features similar to native applications by:

- Creating a web app that is available offline, and that caches elements by routing requests through a service worker
- Storing the default display orientation, theme color, display icon (add to home screen), and splash screen in the web application manifest (or using meta tags)
- Separating critical application functionality and UI into an application shell that can be loaded independently from the content

### Resources:
1. [Codelab -> Scripting the service worker](https://codelabs.developers.google.com/codelabs/pwa-scripting-the-service-worker/index.html?index=..%2F..dev-pwa-training#0)
2. [Codelab -> Caching files with the service worker](https://codelabs.developers.google.com/codelabs/pwa-caching-service-worker/index.html?index=..%2F..dev-pwa-training#0)
3. [Codelab -> Offline quickstart](https://codelabs.developers.google.com/codelabs/pwa-offline-quickstart/index.html?index=..%2F..dev-pwa-training#0)
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
2. [Supercharged Youtube series -> Web Workers(https://www.youtube.com/watch?v=X57mh8tKkgE)
3. [Web Fundamentals -> Why Performance Matters(https://developers.google.com/web/fundamentals/performance/why-performance-matters/)
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
