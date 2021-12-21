# Using Vue 2, Build A Simple Single Page Application

## Introduction

Today, we will be learning how to build a single-page application using Vue.js.
Vue.js is a library for building interactive web interfaces. It provides data-reactive components with a simple and flexible API.

Getting started with the Vue CLI

```
npm install -g vue-cli

```

```
vue init webpack spa
```

Webpack in this command refers to the name of the template we would like to scaffold, as the vue-cli helps us to scaffold templates. There are different templates to use, for more information on that

we would need to change into the directory of our application:

```
cd spa
```

Install the modules:

```
npm install
```

Run the development server:

```
npm run dev
```

## Installing and configuring the Vue router


Install Vue Router by running the following command.

```
npm install vue-router --save
```

Now let’s head into our src/main.js to configure the application to use the router.

Copy and replace the contents of src/main.js to this:


```
// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
//import the vue instance
import Vue from 'vue'
//import the App component
import App from './App'
//import the vue router
import VueRouter from 'vue-router'
//tell vue to use the router
Vue.use(VueRouter)
//define your routes
const routes = []

// Create the router instance and pass the `routes` option
// You can pass in additional options here, but let's
// keep it simple for now.
const router = new VueRouter({
  routes, // short for routes: routes
  mode: 'history'
})
//instatinat the vue instance
new Vue({
//define the selector for the root component
  el: '#app',
  //pass the template to the root component
  template: '<App/>',
  //declare components that the root component can access
  components: { App },
  //pass in the router to the Vue instance
  router
}).$mount('#app')//mount the router on the app
```





