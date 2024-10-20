# Step-by-Step Guide to Create a Vue.js Application with PocketBase

## Introduction
In this guide, we will create a simple Vue.js application that allows users to add items with a title and description. The application will store these items in a PocketBase database.

## Prerequisites
- Basic knowledge of Vue.js and JavaScript.
- A running PocketBase server. You can download it from [PocketBase](https://pocketbase.io/).

## Step 1: Create a New Vue Project
If you haven't created a Vue project yet, you can do so by using Vue CLI. Open your terminal and run:

```bash
vue create my-project
```

Replace `my-project` with your preferred project name. Follow the prompts to set up your project.

## Step 2: Install PocketBase SDK
Navigate to your project directory and install the PocketBase SDK:

```bash
cd my-project
npm install pocketbase
```

## Step 3: Set Up the Main Vue Component
Create a new Vue component (e.g., `ItemList.vue`) in the `src/components` directory and open it for editing.

```bash
touch src/components/ItemList.vue
```

## Step 4: Write the Code
Paste the following code into your `ItemList.vue` file:

```vue
<script setup>
import { ref, onMounted } from 'vue';
import PocketBase from 'pocketbase';

const Title = ref('');
const Description = ref('');
const items = ref([]); // Changed from _posts to items

const pb = new PocketBase('http://127.0.0.1:8090');

async function add() {
  const data = {
    Title: Title.value,
    Description: Description.value,
  };
  const record = await pb.collection('items').create(data); // Change 'Niggas' to 'items'
  console.log("record", record);
  // Optionally, you can push the new record to items to see it immediately
  items.value.push(record);
}

// View data in the database
onMounted(async () => {
  try {
    const fetchedItems = await pb.collection("items").getList(); // Change 'Niggas' to 'items'
    console.log("Fetched items: ", fetchedItems); // Log the fetched data
    items.value.push(...fetchedItems.items); // Correctly push items to items
  } catch (error) {
    console.error("Error fetching items: ", error); // Log any errors
  }
});
</script>

<template>
  <input v-model="Title" placeholder="Enter Title" />
  <input v-model="Description" placeholder="Enter Description" />
  <button @click="add">Add Me</button> <!-- Changed button text -->

  <ul>
    <li v-for="item in items" :key="item.id"> <!-- Changed from nigga to item -->
      <h3>{{ item.Title }}</h3> <!-- Changed from Name to Title -->
      <h3>{{ item.Description }}</h3> <!-- Changed from rich_or_not to Description -->
    </li>
  </ul>
</template>

<style scoped>
</style>
```

## Step 5: Register the Component
Open your `App.vue` file and register the `ItemList` component.

```vue
<template>
  <div id="app">
    <ItemList />
  </div>
</template>

<script setup>
import ItemList from './components/ItemList.vue';
</script>
```

## Step 6: Run Your Application
Now, you can run your Vue application. In your terminal, execute:

```bash
npm run serve
```

Visit `http://localhost:8080` in your browser to see your application in action.

## Conclusion
You have now created a simple Vue.js application that can add items with titles and descriptions to a PocketBase database. You can expand this application further by adding more features, such as editing and deleting items.
