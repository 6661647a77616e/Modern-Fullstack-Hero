# GitHub Actions for CI/CD Pipelines

## Introduction

GitHub Actions allows you to automate tasks within your software development lifecycle directly from your GitHub repository. It supports Continuous Integration (CI) and Continuous Deployment (CD) by running workflows in response to various events, such as code pushes or pull requests.

## 1. Setting Up GitHub Actions

### 1.1 Create a Workflow

Workflows are defined in YAML files and are stored in the `.github/workflows` directory of your repository. Each workflow can have multiple jobs that run in parallel or sequentially.

**Example Directory Structure:**

### 1.2 Define a Basic Workflow

Create a file named `ci-cd.yml` in the `.github/workflows` directory. Here’s a basic example:

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Set Up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '14'

      - name: Install Dependencies
        run: npm install

      - name: Run Tests
        run: npm test

      - name: Build
        run: npm run build

      - name: Deploy
        if: github.ref == 'refs/heads/main'
        run: |
          echo "Deploying to production..."
          # Add your deployment script here
Certainly! GitHub Actions is a powerful tool for automating workflows, including Continuous Integration (CI) and Continuous Deployment (CD). Below is a basic guide to getting started with GitHub Actions for CI/CD pipelines.

markdown

# GitHub Actions for CI/CD Pipelines

## Introduction

GitHub Actions allows you to automate tasks within your software development lifecycle directly from your GitHub repository. It supports Continuous Integration (CI) and Continuous Deployment (CD) by running workflows in response to various events, such as code pushes or pull requests.

## 1. Setting Up GitHub Actions

### 1.1 Create a Workflow

Workflows are defined in YAML files and are stored in the `.github/workflows` directory of your repository. Each workflow can have multiple jobs that run in parallel or sequentially.

**Example Directory Structure:**

your-repo/ └── .github/ └── workflows/ └── ci-cd.yml

yaml


### 1.2 Define a Basic Workflow

Create a file named `ci-cd.yml` in the `.github/workflows` directory. Here’s a basic example:

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Set Up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '14'

      - name: Install Dependencies
        run: npm install

      - name: Run Tests
        run: npm test

      - name: Build
        run: npm run build

      - name: Deploy
        if: github.ref == 'refs/heads/main'
        run: |
          echo "Deploying to production..."
          # Add your deployment script here

Explanation:

    name: The name of the workflow.
    on: Specifies the events that trigger the workflow. In this case, it runs on pushes and pull requests to the main branch.
    jobs: Defines the jobs to be run. Each job can run on different operating systems (e.g., ubuntu-latest).
    steps: Defines the individual steps within a job. Each step can use actions or run commands.
