# How to Deploy Docsify Locally

To deploy Docsify locally, follow these steps:

## 1. Ensure Node.js and NPM are Installed

Docsify requires Node.js and npm (Node Package Manager). You can check if they are installed by running the following commands:

```bash
node -v
npm -v
```

# 2. Install Docsify Globally

```bash
npm install -g docsify-cli
```

# 3. Serve Your Docsify Site Locally
Assuming your documentation files are located in the docs directory inside ~/Downloads/Modern-Fullstack-Hero, you can serve it locally by navigating into that directory and running the Docsify serve command:

```bash
cd ~/Downloads/Modern-Fullstack-Hero
docsify serve docs

```

# 4. Access Your Local Docsify Site

After running the <code>docsify serve docs command</code>, Docsify will start a local server. You can access it by navigating to the following URL in your browser.

```bash
http://localhost:3000
```
