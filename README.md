# Meteor Vue i18n example

A simple meteor project featuring [vue](https://vuejs.org/) as ui layer ([more info](https://github.com/Akryum/meteor-vue-component)), with [internationalization](https://github.com/Akryum/meteor-vue-component/tree/master/packages/vue-i18n).

## Steps to reproduce

In the console, create the project and add the relevant packages:

    meteor create meteor-vue-example-i18n
    cd ./meteor-vue-example-i18n
    meteor remove blaze-html-templates
    meteor add static-html akryum:vue akryum:vue-component akryum:vue-i18n akryum:vue-i18n-ui akryum:vue-less


All the required npm dependencies will be automatically added to your project's `package.json` and installed with `meteor npm install`.

Replace the `client/main.html` file with:

```html
<head>
  <title>meteor-vue-example</title>
</head>

<body>
  <app></app>
</body>
```

Replace the `client/main.js` file with:

```javascript
// Libs
import {Meteor} from 'meteor/meteor';
import {Vue} from 'meteor/akryum:vue';

// Main app
import App from '/imports/ui/App.vue';

Meteor.startup(() => {
  new Vue({
    el: 'body',
    replace: false,
    components: {
      App
    }
  });
});
```

In your app, create *locale files* ending with `.<code>.i18n.json` where the `code` is the language code. For example, you can create the following files:
 - app.en.i18n.json
 - app.fr.i18n.json
 - app.ja.i18n.json

Each locale file is a json file with translated strings:

```json
{
  "title": "Be creative"
}
```

In your component template, use the `$t` method:

```html
<template>
  <div class="app">
    <h1>{{$t('title')}}</h1>
  </div>
</template>
```

You can use object-like nested strings:

```json
{
  "pages": {
    "home": "Home",
    "pricing": "Pricing",
    "about": "About"
  }
}
```

And use the dot notation in your templates:

```html
<template>
  <div class="app">
    <a>{{$t('pages.home')}}</a>
    <a>{{$t('pages.pricing')}}</a>
    <a>{{$t('pages.about')}}</a>
  </div>
</template>
```

For more information, see [usage](https://github.com/Akryum/meteor-vue-component/tree/master/packages/vue-i18n).
