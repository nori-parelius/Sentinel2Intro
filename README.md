# Presentation on Sentinel 2

This repo contains the presentation I will be holding about Sentinel 2 for the course TEK4710 at UiO.

The presentation includes a demo of how to download Sentinel 2 data using the Sentinel Hub APIs, visualise the data and calculate the NDVI index. 

If you are a participant in that course, as a pre-homework, I would like you to read this README.md before the class, and to create an account at Copernicus. You can also check out the Broswer I describe here, because I won't be spending time on that in class. 

If you want to follow along during class, I also suggest preparing a conda environment with the necessary Python libraries. 


## Note about Copernicus Open Access Hub vs Copernicus Data Space Ecosystem

The [Copernicus Open Access Hub](https://scihub.copernicus.eu/), which was previously distributing esa’s data, has closed at the end of October 2023. The new service is called [Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/) and it provides a simple [Browser](https://dataspace.copernicus.eu/browser/?zoom=3&lat=26&lng=0&themeId=DEFAULT-THEME&visualizationUrl=https%3A%2F%2Fsh.dataspace.copernicus.eu%2Fogc%2Fwms%2Fa91f72b5-f393-4320-bc0f-990129bd9e63&datasetId=S2_L2A_CDAS&demSource3D=%22MAPZEN%22&cloudCoverage=30) that you can use to download data. 

Apart from the Browser, the new Copernicus Data Space provides a number of APIs to download data. There are several options depending on what one is interested in [APIs | Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/analyse/apis). In the notebook I am using the [Sentinel Hun APIs](https://dataspace.copernicus.eu/analyse/apis/sentinel-hub).

If you search around for APIs to download Sentinel data, you will surely run into many of them. Particularly the Python library called sentinelsat was very popular. However, this was based on the old Open Access Hub, which isn’t up anymore, so the sentinelsat package doesn’t work and there are probably other third-party libraries that also got broken because of this (just so you know if you try something and it doesn’t work).

## How to create a Copernicus Data Space account

In order to download data from Copernicus, you have to create a user account. To do this, you click on the Register button here: [Sign in to Copernicus Data Space Ecosystem](https://identity.dataspace.copernicus.eu/auth/realms/CDSE/protocol/openid-connect/auth?client_id=cdse-public&response_type=code&scope=openid&redirect_uri=https%3A//dataspace.copernicus.eu/account/confirmed/1), fill out the form and hit Register. (If anyone has used the old Open Access Hub and had an account there, this is not the same platform, so you will need to register here.) I also suggest that once you have an account, you also create an OAuth client. To do this you go to [User Settings](https://shapps.dataspace.copernicus.eu/dashboard/#/account/settings) and Create new. You get a client id and a client secret. You won’t be able to see the secret again, so copy it somewhere where you won’t lose it!

## Downloading images using the Browser
In the [Browser](https://dataspace.copernicus.eu/browser/?zoom=3&lat=26&lng=0&themeId=DEFAULT-THEME&visualizationUrl=https%3A%2F%2Fsh.dataspace.copernicus.eu%2Fogc%2Fwms%2Fa91f72b5-f393-4320-bc0f-990129bd9e63&datasetId=S2_L2A_CDAS&demSource3D=%22MAPZEN%22&cloudCoverage=30)’s panel on the left you can either visualize or search for products. The Visualize tab allows you to look at the images right in the Browser. You can choose the date, or a date range, maximum cloud coverage and processing level (1C or 2A) for the images, as well as what you want to look at, i.e. true color (RGB), various indexes (NDVI, NDWI,..) and other kinds of postprocessing.

In the Search tab you pick the satellite you want and the date range. Then you either zoom in on the area you are interested in, or you draw it onto the map with the tools that are on the right. The search will return all of the tiles that overlap with your area of interest, which you then can download.

When you download the data, it comes as a zip file with a long name containing a .SAFE file with the same name. You find the images inside in a .jp2 format under GRANULE/long_folder_name/IMG_DATA. 

## What you need to install in order to run this notebook
### That is if you decide to run it on your own computer

1. First of all you need [Anaconda](https://www.anaconda.com/download)  
Anaconda is the easiest way to get coding with Python, so go ahead and install if you don't have it yet.
Installing Anaconda should provide all you need, including the jupyter notebooks. 
2. Create a new environment  
Most projects will require you to install a bunch of Python packages. It can get messy fast, because many 
packages depend on each other. It's good practice to make a new virtual environment, called conda environment
in this case for any new projects. 
To do this, you go to Anaconda Powershell Prompt and type: 
```conda create --name <your_env_name>``` where <your_env_name> can be something like sentinel2 or whatever you want.
Then type ```conda activate <your_env_name>``` and you can start using it.  
Note: In Jupyter notebook you will need to pick the right environment. 
3. Install the necessary packages
These are the packages used:  
* ipykernel (to run the notebook) 
* ipywidgets 
* sentinelhub (to interact with the API and get the images)  
* rasterio (to work with geotiffs in Python)
* geopandas (working with geovectors)
* folium (get to use maps)
* jupyter (just for the presentation, you don't need that)

You install them with ```conda install -c conda-forge <package_name>```
