# `CustomCallbackBackend` for i18next

This is a very simple i18next backend to be used in the browser or in the
server. It allows you to tap in to i18next's callback to load resources without
having to write the boilerplate yourself.

# Getting started

Package can be downloaded via [npm](https://www.npmjs.com/package/i18next-callback-backend).

```bash
npm install i18next-callback-backend
```

Wiring up:

```js
import i18next from "i18next";
import CustomCallbackBackend from "i18next-callback-backend";

i18next
.use(CustomCallbackBackend)
.init(i18nextOptions);
```

- As with all modules you can either pass the constructor function (class) to the i18next.use or a concrete instance.
- If you don't use a module loader it will be added to `window.i18nextCustomCallbackBackend`

## Backend Options

```js
{
  // Callback used when loading a single resource.
  customLoad: (language, namespace, callback) => {
    // Your custom loading logic.

    callback(null, /* your loaded resource */);
  },

  // Callback used when loading multiple resources. (Optional)
  customLoadMulti: (languages, namespaces, callback) => {
    // Your custom loading logic.

    callback(null, /* your loaded resources */);
  },


  // Callback used when saving resources. (Optional)
  customCreate: (languages, namespace, key, fallbackValue) => {
    // Your custom saving logic.
  },
}
```

Options can be passed in:

**preferred** - by setting `options.customLoad`,  in i18next.init:

```js
import i18next from "i18next";
import CustomCallbackBackend from "i18next-callback-backend";

i18next
.use(CustomCallbackBackend)
.init({
  customLoad: /* your custom callback */,
  customLoadMulti: /* your custom callback */,
  customCreate: /* your custom callback */,
});
```

on construction:

```js
import CustomCallbackBackend from "i18next-callback-backend";
const customCallbackBackend = new CustomCallbackBackend(
  null,
  {
    customLoad: /* your custom callback */,
    customLoadMulti: /* your custom callback */,
    customCreate: /* your custom callback */,
  }
);
```

via calling init:

```js
import CustomCallbackBackend from "i18next-callback-backend";
const customCallbackBackend = new CustomCallbackBackend();
customCallbackBackend.init({
  customLoad: /* your custom callback */,
  customLoadMulti: /* your custom callback */,
  customCreate: /* your custom callback */,
});
```
