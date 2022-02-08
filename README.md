<img src="https://vuejs.org/images/logo.png" width="150" height="150">

![](https://vuejs.org/images/logo.png =150)

[[https://vuejs.org/images/logo.png |width=100px]]

# Using Vue 2, Build A Simple Single Page Application

#### Introduction

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

#### Installing and configuring the Vue router


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

Now open your src/App.vue file and replace it with the following content:

```
<template>
  <div id="app">
  <!-- the router outlet, where all matched components would ber viewed -->
  <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
}
</script>
<!-- styling for the component -->
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5c7e22;
  margin-top: 62px;
}
</style>
```

#### Setting up our routes

```
//import the hello component
import Hello from './components/Hello'
//define your routes
const routes = [
//define the root url of the application.
{ path: '/', component: Hello }
]
```

So create a file inside the src/components folder called About.vue and let’s place the following into it.

```
<template>
  <div id="about">
  When you have a great story about how your product or service was built to change lives, share it. The "About Us" page is a great place for it to live, too. Good stories humanize your brand, providing context and meaning for your product. What’s more, good stories are sticky -- which means people are more likely to connect with them and pass them on.
  </div>
</template>

<script>
export default {
  name: 'about'
}
</script>
<!-- styling for the component -->
<style>
#about {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5c7e22;
  margin-top: 62px;
}
</style>
```

To do that, open your main.js and replace the routes constant block with the following:

```
//import the hello component
import Hello from './components/Hello'
//import the about component
import About from './components/About'
//define your routes
const routes = [
//route for the home route of the web page
{ path: '/', component: Hello },
//route for the about route of the web page
{ path: '/about', component: About }
]
```

If we now navigate to http://localhost:8080/about, we would see that our about text is being rendered.

#### Using the router links

Let us open our App.vue file, and then add a router link to it.

So before the declaration of our <router-view></router-view> in the component, let’s add two router links:

```
<router-link v-bind:to="'/'">Home</router-link>
<router-link v-bind:to="'/about'">About</router-link>
```

:+1:
