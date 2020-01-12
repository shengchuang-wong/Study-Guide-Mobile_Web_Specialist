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

<meta name="viewport" content="width=device-width, initial-scale=1">


2. [Codelabs -> Responsive images](https://codelabs.developers.google.com/codelabs/pwa-responsive-images/index.html?index=..%2F..dev-pwa-training#0)
3. [Web Fundamentals -> Video](https://developers.google.com/web/fundamentals/media/video)
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
2. [Web Fundamentals -> Introduction to Semantics](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/)
3. [Web Fundamentals -> The Accessibility Tree](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/the-accessibility-tree)
4. [Web Fundamentals -> Text Alternatives for Images](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/text-alternatives-for-images)
5. [Web Fundamentals -> Aria Labels and Relationships](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/aria-labels-and-relationships)
6. [Web Fundamentals -> Accessible Styles](https://developers.google.com/web/fundamentals/accessibility/accessible-styles)
7. [Web Fundamentals -> Hiding and Updating Content](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/hiding-and-updating-content)

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
