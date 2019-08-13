# vue-template
A Vue standard template including Vuetify 2.0, Vou Router and Pug.

:exclamation: It is important to have previous knowledge on Node.js and Vue.js!

## First steps
First, create Vue app using vue-cli:

```vue create vue-template```

Then add Vuetify to your project. I'll explain what it is soon.

```vue add vuetify```

### Vuetify
Reference [here](https://vuetifyjs.com/pt-BR/getting-started/quick-start).
According to [madewithvuejs](https://madewithvuejs.com/vuetifyjs), **Vuetify.js is a component framework for Vue.js. It aims to provide clean, semantic and reusable components that make building your application a breeze.**


### Vue Router
Reference [here](https://router.vuejs.org/).
**Vou Router is the official router for Vue.js**. You can learn more [here](https://router.vuejs.org/).
First, I installed vue-router using yarn (you can also use npm if you're trying this by yourself).

```yarn add vue-router```

After that, I've created a folder called ```/router``` inside ```/src``` (that's how I learned it and how I like to organize it).

Inside ```/router```, I've created two files: ```index.js``` and ```routes.js```.

```routes.js``` is where we're going to declare all the routes in our project. Everytime you need a new page to your app, you will create the .vue file inside ```/src/pages``` (I created this folder containing all the pages - it's all about organization), then you go on ou routes file, import this new .vue file and declare the new route, for exemple:

```
// inside routes.js
import NewPage from '../pages/NewPage.vue'

export default [
  {
     meta: {
      public: true // you're saying if this page is public or not (in this case it is :))
     },
     path: '/newpage', // the path of this new page
     component: NewPage, // the one you imported
     name: 'newpage'
  }
]
```

```index.js``` is where I've imported Vue Router and basically said "Vue, we're using Vue Router now". Also, inside this file, I told Vue Router where our routes are.

```
import Vue from 'vue'
import VueRouter from 'vue-router'
import routes from './routes' // imported the file with all the routes

Vue.use(VueRouter) // vue now knows we're using VueRouter

var router = new VueRouter({ // the instance of VueRouter
    mode: 'history', // its mode
    routes // the routes
})

export default router // export it so we can use it on other files
```

Then in my (our) ```src/main.js``` file, I declared the Router:

```
import Vue from 'vue'
import App from './App.vue'
import vuetify from './plugins/vuetify'
import router from './router' // import router instance

Vue.config.productionTip = false

new Vue({
  router, // tells vue we're using it now
  vuetify,
  render: h => h(App)
}).$mount('#app')
```

This main.js file is (literally) the main JavaScript file that drives our app.

### Pug
**It is optional!** But I love the simplicity so I'd like to share it :)

Finally, Pug! I could explain, but I found [here](https://imasters.com.br/desenvolvimento/codigos-html-mais-organizados-e-limpos-com-pug) the perfect explanation. Translating it to english:
> It is a high-performance, feature-rich template engine implemented with JavaScript for the Node.js ecosystem. It acts as an intermediary between Node and HTML, meaning at run time Pug substitutes project variables with current values and then sends the resulting HTML string to the client.

Also, Pug is based on indentation and whitespace (plain text, and you can learn [here](https://pugjs.org/language/plain-text.html) about it and its syntax). This means there are no open and close tags, which makes the code much cleaner, more organized and easier to understand.

To install it, here's what I've done:

```yarn add vue-loader vue-template-compiler```

```yarn add pug-plain-loader```

```yarn add pug```

To use Pug, you just need to add ```lang="pug"``` on your external template tag:
```
<template lang="pug">

</template>
```

## Creating your first page!
This will be just an exemple.

0. On ```App.vue```, change this part of the code:
```
<v-content>
    <HelloWorld/>
</v-content>
```
To:
```
<v-content>
    <router-view/>
</v-content>
```
This way, you're setting to show any page you create.

1. At ```/pages```, create a new file, add some content, e.g.:
```
<template lang="pug">
    v-container
        h1 Hello, World!
</template>
```
:exclamation: Remember you can use it without pug!

2. As I mentioned earlier, now go to ```/src/router/routes.js``` to declare your new route (you can scroll up to see the code!);

3. Access the page you created on the browser (using the path you declared, e.g.: ```localhost:8080/mynewpath```).

And, yay, you did it! :sparkles:
