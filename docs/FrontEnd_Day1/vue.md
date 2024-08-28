# Basic Usage of Vue.js

## Introduction

Vue.js is a progressive JavaScript framework used for building user interfaces. It is designed to be incrementally adoptable, making it easy to integrate with other projects and libraries.

## Getting Started

To use Vue.js, you can either include it via CDN or install it using npm/yarn. Here’s a basic setup for both methods.

### 1. Including Vue.js via CDN

Add the following script tag to your HTML file to include Vue.js from a CDN:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vue.js Example</title>
  <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
</head>
<body>
  <div id="app">
    {{ message }}
  </div>
  <script>
    new Vue({
      el: '#app',
      data: {
        message: 'Hello, Vue.js!'
      }
    });
  </script>
</body>
</html>

