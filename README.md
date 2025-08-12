## What is it? Who is it for? 
GPU Cloud Providers that are looking to launch their service will require end user facing documentation. This Git repository contains a starting point for end user facing documentation that GPU Clouds can whitelabel and launch in hours. 

--- 
## Local Development Environment 

## Step 1: Fork/Clone Git Repo
Once you get access to it, Fork & Clone the Git repository

## Step 2: Download/Install Python 
If not already installed, Download and Install Python 3.x. We will be using “pip3” (Python’s package manager) to install the required packages. 

--- 

## Step 3: Create Virtual Environment
We recommend using a virtual environment, which is an isolated Python runtime. Any Python packages that you install or upgrade will be local and isolated to the environment. 

``` bash
python3 -m venv venv
```

### Check Dependencies 
A newly created virtual environment will not have any packages installed yet. You can verify by using the following command which should not produce any results. 

``` bash
pip3 freeze
```
---

### Step 4: Install Mkdocs Material
We use [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/). This is a powerful documentation framework on top of MkDocs, a static site generator for project documentation. Since the raw content is markdown and PNG files, users can 

```
pip3 install mkdocs-material
```

--- 
### Step5: Install Dependencies

``` bash 
pip3 install weasyprint pillow cairosvg mkdocs-lightbox 
```

--- 

## Activate Environment 

You can activate the environment by typing the following commands. In Terminal, ensure you are in the correct folder before executing the following: 

```
. venv/bin/activate
```
