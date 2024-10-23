
# Beginning VueJS

## Some short notes

VueJS is a JavaScript framework for building Single Page Application for the web. It uses HTML, CSS, JSS and uses both component-based and declarative programming model to build user interfaces. It is a progressive framework, which means that it is both flexible and *incrementally* adoptable. These are the uses for VueJS:

- Enhancing static HTML without a build step
- Embedding as Web Components on any page
- Single-Page Application (SPA)
- Fullstack / Server-Side Rendering (SSR)
- Jamstack / Static Site Generation (SSG)
- Targeting desktop, mobile, WebGL, and even the terminal

A framework is just a structured way of writing JavaScript code. Different frameworks does the same things (which is building interactive web application) differently, with different goals in mind.

## Before we begin

1) Install NodeJS, as this will be the only way we will install JS library, frameworks, and packages via *NPM* throughout this workshop 

## Setting up a VueJS project

For this workshop, we will be using Vite.

### What is Vite?

I copied this from Wikipedia :
**Vite** (French: [[vit]](https://en.wikipedia.org/wiki/Help:IPA/French "Help:IPA/French"), like "veet") is a local development server written by Evan You, the creator of [Vue.js](https://en.wikipedia.org/wiki/Vue.js "Vue.js"), and used by default by [Vue](https://en.wikipedia.org/wiki/Vue.js "Vue.js") and for [React](https://en.wikipedia.org/wiki/React_(software) "React (software)") project templates. It has support for [TypeScript](https://en.wikipedia.org/wiki/TypeScript "TypeScript") and [JSX](https://en.wikipedia.org/wiki/JSX_(JavaScript) "JSX (JavaScript)"). It uses Rollup and [esbuild](https://en.wikipedia.org/wiki/Esbuild "Esbuild") internally for bundling.

It monitors files as they're being edited and upon file save the web browser reloads the code being edited through a process called Hot Module Replacement (HMR) which works by just reloading the specific file being changed using ES6 modules (ESM) instead of recompiling the entire application.

Vite provides built-in support for server-side rendering (SSR). By default, it listens on TCP port 5173. It is possible to configure Vite to serve content over [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS") and proxy requests (including [WebSocket](https://en.wikipedia.org/wiki/WebSocket "WebSocket")) to a back-end web server (such as [Apache HTTP Server](https://en.wikipedia.org/wiki/Apache_HTTP_Server "Apache HTTP Server") or [lighttpd](https://en.wikipedia.org/wiki/Lighttpd "Lighttpd")).

### Vite for VueJS

Open *PowerShell* and run the command ```npm create vite@latest``` and press ENTER. This should prompt you to setup a name for your project, and select VueJS when the prompt is shown. Afterwards, you may choose TypeScript, or JavaScript (depending on how much you like to suffer). Vite will then create a new folder containg your VueJS project scaffold. Before you start, make sure to run *cd* into the project folder Vite just made and run the command *`npm i`* to install any missing dependencies for your project.

After setting up your VueJS project, you should find folder named *src* and a file named *`App.vue`*. This is where we will be writing our VueJS code. 
Open *`App.vue`* and you should see this code

```javascript
<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
```
VueJS uses a component-based programming model, which means that we will be writing our code in components. Components are reusable pieces of code that can be used to build a user interface. In this case, we have a component named *HelloWorld* which is imported from the file *HelloWorld.vue*. We will be writing our code in this file.

Our HelloWorld component looks like this

```javascript
<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
```
The file has three sections, the *script* section, the *template* section, and the *style* section. The *script* section is where we will be writing our JavaScript code. The *template* section is where we will be writing our HTML code. The *style* section is where we will be writing our CSS code.

## Understanding Reactivity in a Web App
In the *script* section, we have this code
```javascript
const count = ref(0)
```
This is a variable named *count* that is initialized to 0. This variable is reactive, which means that if the value of *count* changes, the UI will automatically update to reflect the new value. This is the concept of reactivity in VueJS.
In order to use this variable in our HTML code, we need to use the *mustache* syntax. The *mustache* syntax is a way to display the value of a variable in HTML. It looks like this
```html
<p>{{ count }}</p>
```
So if you were to put it in our *template* section, it would look like this
```html
<template>
<p>{{ count }}</p>
</template>
```
In contrast to regular 'ol JavaScript, we don't need to use the *document.getElementById()* function to get the element we want to change. We can just use the *mustache* syntax to display the value of our variable in HTML. This is the concept of data-binding in VueJS.
To appreciate the power of reactivity, we need to see it in regular JavaScript. Open *index.html* and add this code
```html
<p id="count"></p>
```
This is a paragraph element with an id of *count*. Now, open *main.js* and add this code
```javascript
let count = 0
const countElement = document.getElementById("count")
countElement.innerHTML = count
```
This is a variable named *count* that is initialized to 0. This variable is not reactive, which means that if the value of *count* changes, the UI will not automatically update to reflect the new value.

To change the value using say a button in regular Javascript, we need to use the *document.getElementById()* function to get the element we want to change. We can then use the *innerHTML* property to change the value of the element. This is the concept of data-binding in regular JavaScript.

See the sample code
```javascript
let count = 0
const countElement = document.getElementById("count")
countElement.innerHTML = count
function increment() {
    count++
    countElement.innerHTML = count
}
```

Based on this code, we can see that using regular javascript to build a web application is tedious and time-consuming. This is why we use frameworks like VueJS to build web applications.

If we write this in VueJS, it would look like this
```javascript
<script setup>
import { ref } from 'vue'
let count = ref(0)
</script>
<template>
<p>{{ count }}</p>
<button @click="count++">Increment</button>
</template>
```
The *@click* is a shorthand for *v-on:click*. This is a directive that listens to the click event on the button. When the button is clicked, the count variable is incremented by 1. The UI will automatically update to reflect the new value of count.
You can write your own functions in the script tag, and replace the *count++* with your own function. For example
```javascript
<script setup>
import { ref } from 'vue'
let count = ref(0)
function Increment() {
    count++
}
</script>
<template>
<p>{{ count }}</p>
<button @click="Increment">Increment</button>
</template>
```

## Ability to develop a frontend application using HTML, CSS, JavaScript

We start this part by first creating our own Vue component file. Create a new file named *Counter.vue* in the *src/components* folder. In this file, we will be writing our VueJS code. Open *Counter.vue* and you should see this code
```javascript
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <div>
    <button type="button" @click="count++">count is {{ count }}</button>
  </div>
</template>
```
This is a component named *Counter* that is imported from the file *Counter.vue*. We will be writing our code in this file.
In order to use this component in our App.vue file, we need to import it. Open *App.vue* and add this code
```javascript
<script setup>
import Counter from './components/Counter.vue'
</script>
```
In our template section, we can now use the *Counter* component. Add this code to the template section
```html
<template>
  <div>
    <Counter />
  </div>
</template>
```

### Styling with CSS

You can see that our component is looking quite boring. We can add styles to our component to make it look better. Open *Counter.vue* and add this code to the style section
```css
<style scoped>
button {
    background-color: #4CAF50; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
}
</style>
```
This is a style for our button. The *scoped* attribute means that the style will only be applied to the component it is defined in. This is the concept of scoped CSS in VueJS.

### Enhancing functionality with JavaScript within Vue components

Let's take at a Todo List and see how we can implement it using VueJS. Create a new file named *TodoList.vue* in the *src/components* folder. In this file, we will be writing our VueJS code. Open *TodoList.vue* and you should see this code
```javascript
<script setup>
import { ref } from 'vue'
const todos = ref([])
const todo = ref("")
function addTodo() {
    todos.value.push(todo.value)
    todo.value = ""
}
</script>
<template>
    <div>
        <input type="text" v-model="todo" />
        <button @click="addTodo">Add Todo</button>
        <ul>
            <li v-for="todo in todos">{{ todo }}</li>
        </ul>
    </div>
</template>
```
Here in our *script* section, we have a list of todos, and a todo variable that is used to store the value of the input field. We also have a function named *addTodo* that is used to add the todo to the list of todos. In our *template* section, we have an input field that is bound to the todo variable. We also have a button that is bound to the *addTodo* function. We also have a list that is bound to the list of todos.

The `v-model` directive is used to bind the value of the input field to the todo variable. The `v-for` directive is used to loop through the list of todos and display them in the list. As usual, our `@click` directive is used to bind the button to the *`addTodo`* function.

### What are props?

In our *HelloWorld* component, we have this code
```javascript
<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>
```
This is a variable named *`msg`* that is initialized to an empty string. This variable is a prop, which means that it is passed from the parent component to the child component. In this case, the parent component is *`App.vue`* and the child component is *`HelloWorld.vue`*. We can pass the value of *`msg`* from *`App.vue`* to *`HelloWorld.vue`* like this
```html
<template>
  <div>
    <HelloWorld msg="Vite + Vue" />
  </div>
</template>
```
Multiple props can be passed from the parent component to the child component. For example
```javascript
<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
  count: Number
})

const count = ref(0)
</script>
```
This is particularly useful when you are breaking down components into smaller ones. For example, you can break down a Todo List into a Todo Item component. This is how you would do it
```javascript
<script setup>
import TodoItem from './components/TodoItem.vue'
import { ref } from 'vue'
     
let todo = ref("")
const todos = ref([])
function addTodo() {
    todos.value.push(todo.value)
    todo.value = ""
}
</script>

<template>
    <div>
        <input type="text" v-model="todo" />
        <button @click="addTodo">Add Todo</button>
        <TodoItem v-for="todo in todos" :todo="todo" />
    </div>
</template>
```
For the TodoItem component, we can build it like this
```javascript
<script setup>
import { ref } from 'vue'
defineProps({
todos: Array
})
</script>
<template>
    <ul>
        <li v-for="todo in todos">{{ todo }}</li>
    </ul>
</template>
```
You have now successfully built a Todo List using VueJS. You can now add more features to your Todo List, like a delete button, or a checkbox to mark a todo as completed.

Before we move to routing, and the Fetch API, let's look at a better way of styling our components using Tailwind CSS.

## Styling with Tailwind CSS

Tailwind CSS is a collection of utility classes that can be used to style your components. It is a utility-first CSS framework, which means that it is composed of many small utility classes that can be combined to build any design. It is also highly customizable, which means that you can configure it to suit your needs.

Let's take a look back at our Counter component. We can style it using Tailwind CSS like this
```html
<template>
  <div>
    <button type="button" @click="count++" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">count is {{ count }}</button>
  </div>
</template>
```
This is a button that is styled using Tailwind CSS. You can see that it is quite long and tedious to write. This is why we use Tailwind CSS IntelliSense. Tailwind CSS IntelliSense is an extension for VSCode that provides instant Tailwind CSS support in your editor. It provides features like autocomplete, syntax highlighting, and linting for Tailwind CSS. You can install it from the VSCode Marketplace.

For more information on Tailwind CSS, you can visit their website at https://tailwindcss.com/

Tailwind CSS is a great tool to have in your web development arsenal as it allows you to build beatiful and responsive websites in a short amount of time.

## Understanding how routing works, and how to use it
### What is routing?

Routing in the context of Single Page Applications is a way to navigate between pages. In a Single Page Application, the browser does not reload the entire page when the user navigates to a different page. Instead, it only loads the content that is needed for that page. This is the concept of routing in Single Page Applications.
Traditionally, routing is done on the server-side. The server handles the request and returns the appropriate page. In Single Page Applications, routing is done on the client-side. The client handles the request and returns the appropriate page.

The advantage of routing on the client-side is that it is faster and more responsive. Our web application no longer needs to wait for the server to respond before loading the page.
The disadvantage is that it is not SEO-friendly. This is because the server does not know what page the user is on, so it cannot index the page. This is why we need to use server-side rendering to make our Single Page Applications SEO-friendly.

We don't need to worry about SEO for this workshop, so we will be using client-side routing.

### What is Vue Router?

Vue Router helps link between the browser's URL/History and Vue's components allowing for certain paths to render whatever view is associated with it.

### Setting up Vue Router

To use Vue Router, we need to install it first. Open *PowerShell* and run the command *npm install vue-router@4*. This will install Vue Router in our project. Now, we need to import it in our *main.js* file. Open *main.js* and add this code
```javascript
import { createApp } from 'vue'
import App from './App.vue'
import {createRouter,createWebHashHistory} from "vue-router";
import Home from "./components/Home.vue";
const routes = [
     { path: '/', component: Home },
]

// 3. Create the router instance and pass the `routes` option
// You can pass in additional options here, but let's
// keep it simple for now.
const router = createRouter({
     // 4. Provide the history implementation to use. We are using the hash history for simplicity here.
     history: createWebHashHistory(),
     routes, // short for `routes: routes`
})
createApp(App).use(router).mount('#app')
```
In our App.vue, we need to add a router-view component. This is where our components will be rendered. Open *App.vue* and add this code
```html
<template>
  <div>
    <router-view />
  </div>
</template>
```

And now our routing works. To change the page, we need to add a router-link component. Open *Home.vue* and add this code
```html
<template>
  <div>
    <router-link to="/about">About</router-link>
  </div>
</template>
```
This is a link to the about page. When the user clicks on the link, the page will change to the about page. We also need to add a router-view component to the about page. Open *About.vue* and add this code
```html
<template>
  <div>
    <h1>About Page</h1>
  </div>
</template>
```
This is a simple about page. You can add more pages to your application by creating a new component and adding it to the routes array in *main.js*.

### What are navigation guards?

This is a work in progress. We'll add it soon

## Making API Requests with Fetch API

### What is the Fetch API?

The Fetch API provides an interface for fetching resources (including across the network). It is a more powerful and flexible replacement for XMLHttpRequest.
During ancient times, we used XMLHttpRequest to make API requests. It was a tedious and time-consuming process.

This was how we used it.
```javascript
var request = new XMLHttpRequest()
request.open('GET', 'https://api.github.com/users', true)
request.onload = function () {
  // Begin accessing JSON data here
  var data = JSON.parse(this.response)
  if (request.status >= 200 && request.status < 400) {
    data.forEach((user) => {
      console.log(user.login)
    })
  } else {
    console.log('error')
  }
}
request.send()
```
Although, this problem was somewhat remedied by the introduction of jQuery. jQuery made it easier to make API requests, but it was still tedious and time-consuming.
```javascript
$.ajax({
  url: 'https://api.github.com/users',
  dataType: 'json',
  success: function(data) {
    data.forEach((user) => {
      console.log(user.login)
    })
  }
});
```
The difference between the two is that jQuery is a library, while the Fetch API is a browser API. This means that the Fetch API is built into the browser, while jQuery is not. This is why we need to install jQuery before we can use it.
This is how we use the Fetch API.
```javascript
fetch('https://api.github.com/users')
  .then(response => response.json())
  .then(data => {
    data.forEach((user) => {
      console.log(user.login)
    })
  })
  .catch(err => console.log(err))
```

See the difference? The Fetch API is much easier to use than XMLHttpRequest. This is why we will be using the Fetch API for this workshop.

### Use the Fetch API to make API requests

Let's take a look at how we can use the Fetch API to make API requests. Open *Home.vue* and add this code
```javascript
<script setup>
import { ref } from 'vue'
let users = ref([])
fetch('https://api.github.com/users')
  .then(response => response.json())
  .then(data => {
    users.value = data
  })
  .catch(err => console.log(err))
</script>
<template>
  <div>
    <ul>
      <li v-for="user in users">{{ user.login }}</li>
    </ul>
  </div>
</template>
```
This is a list of users that is fetched from the GitHub API.
Fetch API will be used to make API requests in this workshop. Especially after we built our Go RESTFul API.

### POST Requests with Fetch API

We can also use the Fetch API to make POST requests. Let's take a look at how we can do that. Open *Home.vue* and add this code
```javascript
<script setup>
import { ref } from 'vue'
let users = ref([])
let username = ref("")
function addUser() {
  fetch('https://api.github.com/users', {
    method: 'POST',
    body: JSON.stringify({
      username: username.value
    }),
    headers: {
      'Content-type': 'application/json; charset=UTF-8',
    },
  })
    .then((response) => response.json())
    .then((json) => {
      users.value.push(json)
    })
}

</script>
<template>
  <div>
    <input type="text" v-model="username" />
    <button @click="addUser">Add User</button>
    <ul>
      <li v-for="user in users">{{ user.login }}</li>
    </ul>
  </div>
</template>

```

Although this probably wouldn't work, as the GitHub API requires authentication. But you get the idea :).




