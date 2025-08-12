# Introduction 

GPU Cloud Providers that are looking to launch their service will require end user facing documentation. This Git repository contains a starting point for end user facing documentation that GPU Clouds can whitelabel and launch in hours. 

--- 
## Local Development Environment 
Follow the steps below to create a local dev environment. 

### Step 1: Fork/Clone Git Repo
Once you get access to it, Fork & Clone the Git repository

### Step 2: Download/Install Python 
If not already installed, Download and Install Python 3.x. We will be using “pip3” (Python’s package manager) to install the required packages. 

### Step 3: Create Virtual Environment
We recommend using a virtual environment, which is an isolated Python runtime. Any Python packages that you install or upgrade will be local and isolated to the environment. 

``` bash
python3 -m venv rafay-venv
```

### Check Dependencies 
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
pip3 install weasyprint pillow cairosvg mkdocs-lightbox 
```

--- 

## Use Local Dev Environment 

### Activate Env
Ensure you have activated the virtual environment before you can use it. In Terminal, ensure you are in the correct folder before executing the following. 

``` bash 
. venv/bin/activate
```

If this was activated correctly, you should see the the name (venv) preflixed in your terminal. 

``` bash 
(venv) mohan.a@mohanas-MacBook-Pro Documents %
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

---

## Delete/Cleanup Environment 

Since we are using Virtual Environments, it is straightforward to cleanly remove all dependencies. Follow the steps below. 

```
source venv/bin/activate
pip freeze > requirements.txt
pip uninstall -r requirements.txt -y
deactivate
rm -r venv/
```
