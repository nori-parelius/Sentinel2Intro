# Sentinel 2 data

This repo contains the code for a lecture on using Sentinel 2 as part of TEK4710 at ITS, UiO.

The .ipynb file includes a demo of how to download Sentinel 2 data using the Copernicus Browser, visualise the data and calculate the NDVI index. 

You can open the notebook directly in Google Colab and work with it there:

![Open In Colab](https://colab.research.google.com/github/nori-parelius/Sentinel2Intro/blob/main/Sentinel2.ipynb)


If you are a participant in that course, as a pre-homework, I would like you to read this README.md before the class. 


## How to create a Copernicus Data Space account

[Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/) is the platform that distributes the data from European Space Agency's satellites. 

In order to download data from Copernicus, you have to create a user account. To do this, you click on the Register button here: [Sign in to Copernicus Data Space Ecosystem](https://identity.dataspace.copernicus.eu/auth/realms/CDSE/protocol/openid-connect/auth?client_id=cdse-public&response_type=code&scope=openid&redirect_uri=https%3A//dataspace.copernicus.eu/account/confirmed/1), fill out the form and hit Register. (If anyone has used the old Open Access Hub and had an account there, this is not the same platform, so you will need to register here.) 

## What you need to install in order to run this notebook

Please, try to get this conda environment ready before the class.

### 1. First of all you need [Anaconda](https://www.anaconda.com/download/success) 

Download the full Anaconda on the left (under Distribution Installers), or if you know what you are doing and are comfortable using a command line interface, go for Miniconda. 

Anaconda is the easiest way to get coding with Python, so go ahead and install if you don't have it yet.
Installing Anaconda should provide all you need, including the jupyter notebooks.

### 2. Create a new environment with the right packages

Most projects will require you to install a bunch of Python packages. It can get messy fast, because many 
packages depend on each other. It's good practice to make a new virtual environment, called conda environment
in this case, for any new projects. 
These are the packages used in this project:  
* jupyter (for jupyter notebook)
* ipykernel (jupyter) 
* ipywidgets (jupyter)
* rasterio (to work with geotiffs in Python)
* matplotlib (for plotting)
* shapely (working with geometries)
* pyproj (working with projections)  

Note: In Jupyter notebook you will need to pick the right environment. 

You have two options for creating the env and istalling packages: 

#### a) Install it yourself   

To do this, you go to Anaconda Powershell Prompt and type:   

```conda create --name <your_env_name>``` where <your_env_name> can be something like sentinel2 or whatever you want.

Then type ```conda activate <your_env_name>``` and you can start using it.  

You install packages with ```conda install -c conda-forge <package_name>```, so you can do `conda install -c conda-forge jupyter ipykernel ipywidgets rasterio matplotlib shapely pyproj` in one go. 

#### b) Install from the environment.yml file

Download the `environment.yml` file from this repo, then go to Anaconda Powershell Prompt, navigate to the folder where you store the file and run:  
`conda env create -f environment.yml`.  
This will create the environment, give it the name that I called mine, i.e. `Sent2Intro25` and install the necessary packages. You can then activate the environment by typing ```conda activate Sent2Intro25```.

