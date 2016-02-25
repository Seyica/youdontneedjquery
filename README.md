"You Don't Need jQuery" is based on [You Might Not Need jQuery](https://github.com/HubSpot/YouMightNotNeedjQuery), but is updated to reflect new APIs, new methodologies, and better, more simplified examples.

---

[...] Please take a moment to consider if you actually need jQuery as a dependency; maybe you can include a few lines of utility code, and forgo the requirement. If you're only targeting more modern browsers, you might not need anything more than what the browser ships with.

[...] Some developers believe that jQuery is protecting us from a great demon of browser incompatibility when, in truth, [modern] browsers are pretty easy to deal with on their own.

**- youmightnotneedjquery.com**

---

# Modern Browsers
Browsers today are nothing like their legacy counter-parts. The "big three"--being Chrome, Firefox, and Edge--are what we call, "evergreen", meaning that they self-regulate updates, giving you the most updated engines available. "**You Don't Need jQuery**" only focuses on these modern, evergreen browsers. If you need to support more legacy browsers, like IE, try reading [You Might Not Need jQuery](https://github.com/HubSpot/YouMightNotNeedjQuery) instead.

---
# You Don't Need jQuery

Most of the APIs that I'll be showing can be [polyfilled](https://en.wikipedia.org/wiki/Polyfill), meaning that you can recreate these features once, and then use all over your code. However, there are some syntax features (like async/await) that I use that will have to be "transpiled", using something like [Babel](https://babeljs.io/)

---

## AJAX GET

**jQuery**
```javascript
$.ajax({
    url: 'path/to/json',
    success: data => {
        // ...
    },
    error: error => {
        // ...
    }
});
```

**Modern** | Using the [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) and [async/await](http://tc39.github.io/ecmascript-asyncawait/)
```javascript
(async () => {
    try {
        const request = await fetch('path/to/json');
        const data = await request.json();
        // ...
    }
    catch (e) {
        // ...
    }
});
```

---

## AJAX POST

**jQuery**
```javascript
$.ajax({
    url: 'path/to/whatever',
    type: 'POST',
    contentType: 'application/json',
    data: JSON.stringify(myObjectHere),
    success: data => {
        // ...
    },
    error: error => {
        // ...
    }
});
```

**Modern** | Using the [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) and [async/await](http://tc39.github.io/ecmascript-asyncawait/)
```javascript
(async () => {
    try {
        const request = await fetch('path/to/whatever', {
            method: 'POST',
            headers: new Headers({ 'Content-Type': 'application/json' }),
            body: JSON.stringify(myObjectHere)
        });
        const data = await request.json();
        // ...
    }
    catch (e) {
        // ...
    }
});
```

---

WORK IN PROGRESS