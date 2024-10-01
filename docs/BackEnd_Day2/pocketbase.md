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


# Client-side SDK

Pocketbase is intended to be used with a client-side SDK, which provides an easy way to interact with your backend from your frontend code. The SDK handles authentication, making requests to the API, and parsing the responses.

The SDK is available for both Dart and Javascript. For our workshop, we will be using the Javascript SDK. You can get it by  

`npm install pocketbase --save`
```js
import PocketBase from 'pocketbase';

const pb = new PocketBase('http://127.0.0.1:8090');

...

// list and filter "example" collection records
const result = await pb.collection('example').getList(1, 20, {
    filter: 'status = true && created > "2022-08-01 10:00:00"'
});

// authenticate as auth collection record
const userData = await pb.collection('users').authWithPassword('test@example.com', '123456');

// or as super-admin
const adminData = await pb.admins.authWithPassword('test@example.com', '123456');

// and much more...
```

# File Uploads

### Understanding file uploads

Uploading files is a common task in web development. Whether you're building a social media platform, a file-sharing service, or an e-commerce site, you'll likely need to handle file uploads at some point.

In this section, we'll cover the basics of file uploads, including how to handle file uploads in a web application, how to upload files to a server, and how to store files in a database.

### Handling file uploads in a web application

When a user uploads a file in a web application, the file is sent to the server as part of an HTTP request. The server then processes the file and stores it in a location where it can be accessed later.

There are several ways to handle file uploads in a web application. One common approach is to use a form with an input element of type file. When the user selects a file to upload, the file is sent to the server as part of a form submission.

The file-type is multipart/form-data, which allows the form to include binary data, such as files. The server can then process the file and store it in a location where it can be accessed later.

On your client, you can use the Pocketbase SDK to upload files to your backend. Here's an example of how you can upload a file using the SDK:

```js
// Example HTML:
// <input type="file" id="fileInput" />

import PocketBase from 'pocketbase';

const pb = new PocketBase('http://127.0.0.1:8090');

...

const formData = new FormData();

const fileInput = document.getElementById('fileInput');

// listen to file input changes and add the selected files to the form data
fileInput.addEventListener('change', function () {
    for (let file of fileInput.files) {
        formData.append('documents', file);
    }
});

// set some other regular text field value
formData.append('title', 'Hello world!');

...

// upload and create new record
const createdRecord = await pb.collection('example').create(formData);
```
Let's break down the code:

1. We create a new FormData object, which is used to construct a set of key/value pairs representing form fields and their values.

2. We get a reference to the file input element in the HTML document.

3. We add an event listener to the file input element that listens for changes. When a file is selected, we loop through the selected files and append them to the FormData object.

4. We append a regular text field value to the FormData object.

5. We use the Pocketbase SDK to upload the FormData object to the backend and create a new record in the 'example' collection.
