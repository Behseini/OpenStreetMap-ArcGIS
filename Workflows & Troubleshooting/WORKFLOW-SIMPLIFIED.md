##Workflow - Simplified

This workflow is a simplified step by step guide to to display OSM data using the layers and stylesheet provided in this repository and optimise the speed at which the data is processed and displayed in ArcGIS in stages. It uses the purpose built models based on the OpenStreetMap Editor for ArcGIS toolbox that remove the need to a user to put in a number of paramters, such as tag names.

For a more detailed workflow showing exactly what happens at each step, see [WORKFLOW-EXTENDED.md](https://github.com/GASCUK/OpenStreetMap-ArcGIS/blob/master/WORKFLOW-EXTENDED.md).

1. [Downloading and processing the data](https://github.com/GASCUK/OpenStreetMap-ArcGIS/blob/master/WORKFLOW.md#downloading-and-processing).
2. [Completing the data set](https://github.com/GASCUK/OpenStreetMap-ArcGIS/blob/master/WORKFLOW-SIMPLIFIED.md#completing-the-data-set).
3. [Creating an MXD and displaying the processed data in ArcMap](https://github.com/GASCUK/OpenStreetMap-ArcGIS/blob/master/WORKFLOW-SIMPLIFIED.md#creating-an-mxd-and-displaying-the-processed-data-in-arcmap).

###Downloading and processing the data

1. Download the raw OSM data for the area of interest from [Geofabrik](http://download.geofabrik.de/). 
 1. Download the .bz2 compressed OSM file and unzip it. _(**Note:** If this file is corrupt then download the .pbf and use the openly available [OSMConvert](http://wiki.openstreetmap.org/wiki/Osmconvert) tool to convert the .pbf to a .osm file)_.
 3. Whole continents can be downloaded if necessary but it is not recommended due to the time they take to process. If only a specific country is required then it is much more preferable to download just this data instead. _(**Note:** For example, the whole of Africa took us over 7 days to download and process whereas Cyprus took less than a couple of hours)_.
2. In ArcCatalog, open the [OpenStreetMap Models](https://github.com/GASCUK/OpenStreetMap-ArcGIS/tree/master/Models) toolbox and run the **Load OSM** model.
 1. ![Load OSM mode](https://raw.githubusercontent.com/GASCUK/OpenStreetMap-ArcGIS/master/Images/LoadOSMFileModel.png)
 2. Select the unzipped .osm file as the Load OSM parameter.
 3. Create a file geodatabase in your workspace and name the Target feature dataset "planet" in this gdb.
 4. Running this tool results in a feature dataset in the file gdb called planet containing three feature classes: planet_osm_ln, planet_osm_ply and planet_osm_pt.
3. In ArcCatalog, run the **OSM Attribute Selector** model in the [OpenStreetMap Models](https://github.com/GASCUK/OpenStreetMap-ArcGIS/tree/master/Models) to extract OSM keys from the tag collection and store them as standalone attributes.
 1. ![Load OSM mode](https://raw.githubusercontent.com/GASCUK/OpenStreetMap-ArcGIS/master/Images/OSMAttributeSelectorModel.png)
4. Create attribute indexes for all of the three feature classes within the planet feature dataset by running the **Add Index Attributes** model in the [OpenStreetMap Models](https://github.com/GASCUK/OpenStreetMap-ArcGIS/tree/master/Models).
 1. ![Load OSM mode](https://raw.githubusercontent.com/GASCUK/OpenStreetMap-ArcGIS/master/Images/AddOSMAttributeIndexesModel.png)

###Completing the data set
1. Add the [Natural Earth bathymetry data](https://github.com/GASCUK/OpenStreetMap-ArcGIS/blob/master/Data/README.md) and the [OSM dissolved land polygon](https://github.com/GASCUK/OpenStreetMap-ArcGIS/blob/master/Data/README.md) to the file geodatabase alongside the processed OSM data.

###Creating an MXD and displaying the processed data in ArcMap
1. Open ArcMap and add the Humanitarian OSM [stylesheet](https://github.com/GASCUK/OpenStreetMap-ArcGIS/tree/master/Styles): *Customize > Style Manager > Styles... > Add Style to List...*
2. Create a new blank MXD and load the [layers](https://github.com/GASCUK/OpenStreetMap-ArcGIS/tree/master/Layers).
3. Arrange the layers in numerical order.
4. Close ArcMap. Within ArcCatalog, set the MXD data source to the file geodatabase where the processed OSM data has been loaded into.
5. Reopen the MXD in ArcMap to view the symbolised OSM data.