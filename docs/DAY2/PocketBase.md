
# Introduction
Pocketbase is an open source backend, with SQLite as its database, built-in authentication, and a RESTful API. It is designed to be easy to use and deploy, making it a great choice for small to medium-sized projects.

Having a backend means that you don't have to worry about setting up a server, database, or authentication system from scratch. Pocketbase provides all of these features out of the box, so you can focus on building your application.

# Installation

Pocketbase is very simple to set up. Head over to [PocketBase.io](https://pocketbase.io) and follow the instructions to create a new project. Once you have created a project, you will be given a URL that you can use to access your backend.

# Collection

Pocketbase uses collections to organize your data. A collection is similar to a table in a traditional database, and it stores a set of related data. You can create as many collections as you need for your project, and each collection can have its own set of fields.

In contrast to building a backend with database functionality from scratch, Pocketbase provides a simple and intuitive way to create collections and manage your data.

A single entry to a collection is called a record. This is the same as a row in a traditional database table. Each record has a unique identifier, which is used to access and update the record.

This is how it looks like in the Pocketbase dashboard:
<img src="https://pocketbase.io/images/screenshots/collection-panel.png" alt="Collection" width="500"/>



# Step-by-Step Guide to Create a Vue.js Application with PocketBase

## Introduction

We are going to integrate existing Vue.js code with PocketBase.

Navigate to your downloaded PocketBase executable files. You can download it from [PocketBase](https://pocketbase.io/).

Start the PocketBase server with this command:

```bash
./pocketbase.exe serve
```

Register your account on the admin link, and create a new content called Post. Then, create two new fields: Title and Description.


## Installing PocketBase in Your Project

Navigate to your project folder and install PocketBase in npm with the following command:

```bash
cd my-project
npm install pocketbase
```


## Importing PocketBase into the Code
To integrate PocketBase into your Vue.js app, import it as follows:
```js
import PocketBase from 'pocketbase';
```

Next, add onMounted to manage lifecycle hooks:
```js
import { ref, onMounted } from 'vue';
```

## Creating a New PocketBase Instance

create new instance of the PocketBase class
```js
const pb = new PocketBase('http://127.0.0.1:8090');, 
```
The pb variables holds the instance of the PocketBase

## Adding the Vue.js Elements
```js
  <input v-model="titleVal" @change="logging" ><br>
  <input v-model="descVal" @change="logging" ><br>
  <button @click="add"> Add</button>

  <ul>
    <li v-for="post in posts">
      <h3>{{ post.title }}</h3>
      <p>{{ post.description }}</p>
    </li>
  </ul>
```

## Creating an Async Function

### What is an Async Function?

An async function is a function that operates asynchronously via the event loop. It allows you to use the await keyword within it, which pauses the execution of the function until a promise is fulfilled.

You declare an async function using the async keyword before the function definition:


```js
async function add() {
  // Function body
}
```

### Creating the Data Object
Within the add() function, define the data object that contains the input values:

```js
const data = {
  title: titleVal.value,
  description: descVal.value
};
```

### Creating a New Record
Use the following code to create a new record in the items collection in PocketBase:
```js
const record = await pb.collection('posts').create(data);
```

Push the new record into the posts array:
```js 
posts.value.push(record);
```

## Fetching Data with OnMounted Lifecycle Hook

Define the onMounted lifecycle hook to run code when the component is mounted. This is where you will fetch the existing data from PocketBase:

```js
onMounted(async () => {
  // Code to fetch posts will go here
});
```

### Fetch Data from PocketBase 

Inside the onMounted function, use the await keyword to call the getFullList() method on the posts collection. This retrieves all records from the collection:

```js
const _posts = await pb.collection('posts').getFullList();
```

Then, use the spread operator ... to push all items from _posts into the posts array:

```js
posts.value.push(..._posts);
```

Here are the complete code


```js
<script setup>
import { ref, onMounted } from 'vue'
import PocketBase from 'pocketbase';

const pb = new PocketBase('http://127.0.0.1:8090');

const titleVal = ref('')
const descVal = ref('')

const posts = ref([])

async function add() {
  const data = {
    title : titleVal.value,
    description : descVal.value
  }
  const record = await pb.collection('posts').create(data);
  console.log("record", record);
}

onMounted(async () => {
  const _posts = await pb.collection('posts').getFullList();
  console.log("posts:", _posts);

  posts.value.push(..._posts);
})

</script>

<template>

  <input v-model="titleVal" @change="logging" ><br>
  <input v-model="descVal" @change="logging" ><br>
  <button @click="add"> Add</button>

  <ul>
    <li v-for="post in posts">
      <h3>{{ post.title }}</h3>
      <p>{{ post.description }}</p>
    </li>
  </ul>
</template>

<style scoped>
</style>
```




Now, you can run your Vue application. In your terminal, execute:

```bash
npm run serve
```

