# Introduction 

GPU Cloud Providers that are looking to launch their service will require end user facing documentation. This Git repository contains a starting point for end user facing documentation that GPU Clouds can whitelabel and launch in hours. 

--- 
## Local Development Environment 
Follow the steps below to create a local dev environment. 

### Step 1: Fork/Clone Git Repo
Once you get access to it, Fork & Clone the Git repository

```
git clone https://github.com/RafaySystems/gpucloud-docs.git
```

### Step 2: Download/Install Python 
If not already installed, [Download](https://www.python.org/downloads/) and Install Python 3.1.x. We will be using “pip3” (Python’s package manager) to install the required packages. You can optionally check if this was installed correctly by typing the following command 

```
python3 --version
```

You should see something like as the result 

```
Python 3.13.5
```

### Step 3: Create Virtual Environment
We recommend using a virtual environment, which is an isolated Python runtime. Any Python packages that you install or upgrade will be local and isolated to the environment. 

``` bash
python3 -m venv rafay-venv
```

**Check Dependencies**

A newly created virtual environment will not have any packages installed yet. You can verify by using the following command which should not produce any results. 

``` bash
pip3 freeze
```

### Step 4: Install Mkdocs Material
We use [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/). This is a powerful documentation framework on top of MkDocs, a static site generator for project documentation. Since the raw content is markdown and PNG files, users can 

```
pip3 install mkdocs-material
```
 
### Step5: Install Dependencies

``` bash 
pip3 install weasyprint pillow cairosvg mkdocs-glightbox 
```

## Use Local Dev Environment 

### Activate Env
Ensure you have activated the virtual environment before you can use it. In Terminal, ensure you are in the correct folder before executing the following. 

``` bash 
. rafay-venv/bin/activate
```

If this was activated correctly, you should see the the name (venv) preflixed in your terminal. 

``` bash 
(rafay-venv) mohan.a@mohanas-MacBook-Pro Documents %
```

### Run MkDocs Server 

In Terminal, navigate to the folder where you have the docs

``` bash 
mkdocs serve
```

The local build should complete in a few seconds. You should see something like the following. 

``` bash
INFO     -  Building documentation...
INFO     -  Cleaning site directory
INFO     -  Documentation built in 0.15 seconds
INFO     -  [07:59:27] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO     -  [07:59:27] Serving on http://127.0.0.1:8000/
``` 

### View Docs 

Open a web browser and navigate to "http://127.0.0.1:8000/". 

## White Labeling 

### Basic Information 

Open the file "mkdocs.yml" in your favorite IDE and update the values with your preferred name. Replace the boiler plate text "White Labeled GPU Cloud Provider" with your brand's name. 

``` yaml 
site_name: White Labeled GPU Cloud Provider
site_author: Name of Admin
site_description: >-
  Product Documentation for White Labeled GPU Cloud Provider

# Copyright
copyright: Copyright &copy; 2025 GPU Cloud Provider

nav:
  - White Labeled GPU Cloud: index.md
```

### Favico and Logo

The logo can be changed to a user-provided image (any type, incl. `*.png` and `*.svg`). Update the following lines in your `mkdocs.yml` file. 

``` yaml 
favicon: assets/favicon.png
  icon:
    logo: assets/logo.png 
``` 

### Core Content 

The core documentation content is in markdown files organized under **nav**. Feel free to update this content as required. 

``` yaml 
nav:
  - White Labeled GPU Cloud: index.md
  - Workspaces: workspace.md 
  - Compute: 
    - 'Overview': 'compute_overview.md'
    - 'Pods': 'pods.md'
    - 'Managed Kubernetes': 'k8s.md'
  - Developer Tools: 
    - 'Notebooks': 'notebook.md'
  - Users:  access_control.md
```

## Deploy Docs

Whitelabeled documentation can be deployed to a variety of [locations](https://squidfunk.github.io/mkdocs-material/publishing-your-site/). Popular ones are

1. Cloudflare
2. Netlify

### Deploy to Cloudflare Pages
Cloudflare Pages provide automated deployments (and preview builds on pull request) for static sites such as Mkdocs Material. It works with GitHub and GitLab.

1. In your Cloudflare dashboard, select Workers & Pages.
2. Select Create > Pages > Connect to Git. 

> [!NOTE]
> If this is your first time using Pages, go through the process to link you GitHub account. Make sure you allow access to the repo you want to deploy. If GitHub is connected, Cloudflare shows the Deploy a site from your account page.

3. Choose the repository you want to deploy. Select **Begin setup**.
4. In "Set up build and deployments", enter the build settings:
   - Check the Project name and Production branch are correct.
   - Select MkDocs in Framework preset.
   
5. Select Save and Deploy. Cloudflare will build your site which may take a few minutes.
6. Once the build and deployment is complete, you can view your site at the autogenerated preview link
7. From the site dashboard, select Visit site. 

## Delete/Cleanup Environment 

Since we are using Virtual Environments, it is straightforward to cleanly remove all dependencies. Follow the steps below. 

``` bash 
source venv/bin/activate
pip freeze > requirements.txt
pip uninstall -r requirements.txt -y
deactivate
rm -r venv/
```
