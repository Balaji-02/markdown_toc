# markdown_toc
Creating a workflow that runs on push to any branch and uses actions to automatically generates table of contents
# CI/CD Pipeline with GitHub Actions for Markdown Documentation

## Introduction

In this guide, we'll walk through the process of setting up a Continuous Integration and Continuous Deployment (CI/CD) pipeline using GitHub Actions to automatically generate a table of contents for your Markdown documentation file.

## Prerequisites

Before you begin, ensure that you have the following:

- A GitHub account
- A repository containing your Markdown documentation files

## Steps

### Step 1: Create a GitHub repository

If you haven't already, create a new repository on GitHub to store your Markdown documentation files.

### Step 2: Set up GitHub Actions workflow

1. Inside your repository, create a `.github/workflows` directory.
2. Within the `workflows` directory, create a YAML file (e.g., `markdown-toc.yml`) to define your GitHub Actions workflow.

```yaml
name: Generate Table of Contents

on:
  push:
    branches:
      - '*'

jobs:
  generate_toc:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout code
      uses: actions/checkout@v2
      
    - name: Install Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'
      
    - name: Install markdown-toc
      run: npm install -g markdown-toc
      
    - name: Generate Table of Contents
      run: markdown-toc -i README.md
