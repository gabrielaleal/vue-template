# vue-template
A Vue standard template including Vuetify, Vou Router and Pug.

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

After that, I've created a folder called ```/router``` inside ```/src``` (that's how I learned it and how I like to organize it). Inside ```/router```, I've created two files: ```index.js``` and ```routes.js```.
```routes.js``` is where we're going to declare all the routes in our project. And ```index.js``` is where I've imported Vue Router and basically said "Vue, we're using Vue Router now". Also, inside ```index.js``` I told Vue Router where our routes are.

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
