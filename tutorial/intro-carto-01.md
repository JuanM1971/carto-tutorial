# Introduction to Mapping with CARTO 

####Workshop Objectives 
This exercise is intended to introduce users to mapping and displaying spatial information using the online platform, CARTO. 

[CARTO](https://carto.com) is an online platform that allows users to upload data and provides tools to visualize that data in interactive maps. Maps made on CARTO can be shared and embeded on websites and in different formats. On of the advantages of using CARTO as opposed to other interactive mapping platforms is that it allows you to directly upload your datasets and manipulate them online. This functionality includes selecting certain specific parts of your dataset using SQL-style queries. 

In this first introductory tutorial users will:

1. Create a CARTO account
1. Become familiar with CARTO's dataset and map views
1. Learn how to upload simple datasets in tabular and vector formats to their CARTO account
1. Learn basics of interface and visualization tools 


Subsequent tutorial pages demonstrate how to execute simple data manipulations in CARTO, as well as add interactive elements, customize basemaps, and embed and share maps.

The data used in this workshop can be found in the data folder of this repository [(here)](https://github.com/barnarderc/carto-tutorial/tree/master/data). 

- - - -
####Creating a CARTO Account

To begin using CARTO, users must first create an online account [here](https://carto.com/signup). CARTO's basic account is free, and allows users to upload a limited number of files. 

Once you've created your account, and verified your email, when you sign into CARTO you will be presented with the option to begin by creating a new map. 

![Intro page](https://github.com/barnarderc/carto-tutorial/blob/master/images/create-account.JPG?raw=true)

- - - 

#### Becoming Familiar with CARTO's Interface 

CARTO's platform divides users' accounts into a **Datasets** tab and a **Map** tab. In the Datasets tab, users can upload, edit, view or delete their own datasets. In the map view, users are able to build interactive mapping projects, combining one or more of their own datasets, to be published or shared. 

![](https://github.com/barnarderc/carto-tutorial/blob/master/images/map-datasets-view.JPG?raw=true)

We will begin using CARTOCARTO by uploading our dataset, **carto-tutorial-data.csv** from the **data** folder. Before we upload this data to CARTO, let's take a look at how it is formatted. 

- - - 

The data we will be using is in a tabular format, representing location points for three people as they travel from different starting locations, and end up in Paris, France. Here is a peek at the data structure: 


The data is formatted with 7 columns:
-	`person`: Person in the dataset's name, identifying who was at the given location point
-	`sequence`: Number of the sequence in which the given person stopped at the location point (if 1, then row represents the person's first stop, if 2, represents their second stop, etc.)
-	`lat`: Number representing the latitude; is one half of the location information necessary to plot the points in CARTO. 
-	`lon`: Number representing the longitude; second half of the location information necessary to plot the points in CARTO. 
-	`location`: Name of the city, if given, of the person's location
-	`country`: Name of the country, of location
-	`id`: Unique id for each person, to identify who was at given location


![](https://github.com/barnarderc/carto-tutorial/blob/master/images/data-descrip.JPG?raw=true)


Each of the three people has 7 location stops, as they make their way around the world to Paris. Each row represents one stop. In this tutorial, we are interested in mapping these individuals' movement, following their sequence of stops. We do not have any information about how much time they spend in each stop, but we do know the order they travel based on the `sequence` column. We also know which person stops where because we have an `id` column and a column with their name (`person`). 

Now that we have an idea of what our data looks like, and what we are interested in mapping, we can upload the dataset to CARTO and begin to explore and visualize it.

- - - 

On the CARTO web page, navigate to the "Your Datasets" tab, and click on the "New Dataset" option on the right-hand side of the page. A new window will appear, prompting users to choose the way in which to connect their dataset. 

![](https://github.com/barnarderc/carto-tutorial/blob/master/images/carto-upload-dataset.JPG?raw=true)

Users are able to connect datasets from a variety of sources, including data hosted on Google Drive and Dropbox. Users can also upload data in a variety of formats, tabular but also geographic.

In this case we have our **carto-tutorial-data.csv**, which you should download, and which we will upload by browsing to its downloaded location on your local computer.

Once chosen, connect the data by clicking "Connect Dataset".

- - -

When the data is finished uploading, CARTO will open the dataset and you should see the same rows and columns as shown previously. One main difference that should be noted, is that CARTO has added a column `the_geom`. This column tells CARTO how to map the points, and is based off of our `lat` and `lon` columns. CARTO has also added a column called `cartodb_id`; this is just a column with unique numbers for each row.

From here, we can go ahead and display this data on a map. At the top of the table, there is a sliding icon, which currently shows that we are in **Data View**. Toggle the slider to **Map View**. 

![](https://github.com/barnarderc/carto-tutorial/blob/master/images/map-view-1.JPG?raw=true)


In **Map View**, the data will be visualized as points, with one point representing each row of data in our dataset. When the points are first visualized, all of them are represented as the same color, and we do not see any differences based on which of our three subjects' locations a given point represents.

In order to begin altering the way your map looks, we must first create a map from this data. Click on the button in the top right of your page that says **Visualize**. After you click Visualize, you will be prompted to create a map, so click **Ok, Click Map**. 

You will now have a map open in the **Map Editor** mode, and you can now alter your map, and make it ready to be published and shared.

Important Elements in Map Editor mode:

In the Map Editor view, there are many icons and tools you can use to customize the look of your map, including its background, your data, and interactive elements. 


![](https://github.com/barnarderc/carto-tutorial/blob/master/images/basemap-elements-2.JPG?raw=true)

In order to change the map background, in the bottom left of the map there is the **Change Basemap** icon. Clicking this will bring up a menu of different background or basemap options. CARTO offers some options with or without labels, and allows you to connect to other basemaps. Here you can also connect customized basemaps from other sources, such as Mapbox. 


![](https://github.com/barnarderc/carto-tutorial/blob/master/images/basemap-elements.JPG?raw=true)

On the top of your Map Editor, there are icons that allow you to ad drawn items to your map, as well as labels, image annotations and text. If you click `Add Title`, a floating title will appear on your map. 


![](https://github.com/barnarderc/carto-tutorial/blob/master/images/map-title.JPG?raw=true)

Double-clicking this title will allow you to rename and edit the appearance.

- - -

####Editing Data Visualization

In your Map Edit view, on the right-side of the page, are tabs that allow you to edit the appearance of your data. 

![](https://github.com/barnarderc/carto-tutorial/blob/master/images/layer-properties-2.JPG?raw=true)

In this layer tab, you have multiple ways to customize the data visualization. Clicking on the second icon that looks like a paintbrush, you can navigate to the **Map Layer Wizard**, where you can choose what information will be used to color and code your data. Currently, your points are visualized using a simple color fill. 

Because we want to visualize these location points by our three people travelers, we want to change our points to distinct colors for each of the three people (we can think of the three of them like categories). 

In the Map Layer Wizard, switch your visualization mode from **Simple** to **Categories**. After choosing Categories as the visualization method, in the layer properties tab, you will be given the option to customize which column from your dataset you want to use as the categories. 

In the dropdown menu next to `column`, choose **person**. This is the column in your data with one of our three subjects' names based on who visited a location point. 

Once you choose the column, you are able to customize the colors representing each of the three people, as well as the size of the location points, and their opacity (fill).

Notice in the map that a legend should appear, labeling each othe three points so your map users know which person corresponds to which point color. (If a legend does not appear, click on the legend icon in the layer tab. There you can customize and add your legend).

Now your map should show points in three different colors based on our three people. We are also interested in showing these three peoples' movement over time. Because of this we will want to use CARTO's **Torque** visualization method. This uses a column in the data to create an order in which the points should appear. In our case, we have a column that reflects that movement; the column is called `sequence` and it has coded values from 1-7 for each point in each person's journey. We will use this to create a torque map. Furthermore, CARTO provides the option to create either a torque map using one variable, time, or to create a torque map using time, but differentiating by categories. We will use the latter option, since we want to differentiate by our individual people.

- - - 

In your layer properties tab, we can now symbolize our layer by different colors, and use the Torque categories visualization method. Symbolize the layer by choosing **Torque Cat**. 


Reminders: The **Time Column** in our column is the `sequence` column. The **Category Column** is our column to differentiate between people, using the `person` column. In the layers property you can also customize the length of time spent on each point, as well as the opacity, number of trailing points, etc. 

Our map now reflects each individual's sequence of movements. If we wanted to separate and isolate one of the people in our dataset, we can also do so using CARTO.

- - - 
###Filtering the Data

When working with categorical data, we might want to isolate or filter to a specific category, to visualize it alone on our map. This allows you to work with a single person's data, for example.

To do so, click on **Data View**. This will bring us back to the view of our dataset as rows and columns. 

From here, navigate to the layer properties tab and click on the **Filter** tab: 

![](https://github.com/barnarderc/carto-tutorial/blob/master/images/filter.JPG?raw=true)

In the filter tab, choose the column `person` to filter our rows by each person. You should now see a list of all three subjects' names. If you click on any of them, they will be deselected and filtered out of the data (this is not permanent and you can turn them on and off). 

Turn off both "Natasha Romanoff" and "James Howlett". Now, you should only have "Ami Han" selected. On top of your dataset, a notification should appear that asks if you want to "create dataset from query or clear view". 

We want to create a dataset from this query with just "Ami Han"'s rows. Click "create dataset from query". 

CARTO will navigate you now to your newly created dataset, which will be named "carto_tutorial_data_copy". Rename this file "Ami_Han". 

Now, let's do the same thing for our other two subjects. Click the back arrow at the top left of the page next to the dataset title to navigate back to your datasets. 

Click on "carto_tutorial_data", and return to the **Filter** tab. Select "Natasha Romanoff" and deselect "Ami Han" and "James Howlett" (in the filter tab with the column `person` selected).

Choose "create dataset from this query", which will bring you to your newly subsetted dataset, which you should rename "Natasha_Romanoff". 

Repeat the process for "James Howlett", renaming the new dataset "James_Howlett". 

Once this process of subsetting your data has been completed, navigate once more to **Your Datasets** page; you should now have four datasets: carto_tutorial_data, Natasha_Romanoff, Ami_Han, James_Howlett. 

Let's go back to our map now. Return to your main CARTO page by clicking the back arrow from your **Data View** (found at the top left of the page). When open to your CARTO dashboard, you should navigate to **Your Maps** dashboard by choosing your maps from the dropdown menu at the top of the page. In your maps page, choose the map you were previously working on, and click **Edit in CARTO**.

- - -
###Adding Interactivity

In your **Map View** editor, we can now add in the new dataset we just created, by clicking the plus sign in the layer properties tab. If you have additional datasets you are interested in overlaying, you can add up to 8 to a single map. In this case, we aren't interested specifically in adding more layers to our map, but it is useful in general. Click the plus sign **Add layer** and choose the data layer "Ami_Han" which we created previously.

For this layer, we can add additional information, in the form of interactive pop ups. In the layer properties tab, click the **info window**. 

![](https://github.com/barnarderc/carto-tutorial/blob/master/images/info-window.JPG?raw=true)

In the info window tab, you can customize your layer pop-up to appear when a point is clicked, or when a user hovers over it. Additionally, you can customize which columns appear in the pop up. **It is important to note, though, that the info windows and pop ups are disabled for Torque layers**. While you can add pop ups for points that are symbolized by category, for example, you cannot for torque layers. 

- - -

###Publishing your Map

Once you have customized all the features on your map, symbolized your data, and added interactive pop ups, you can export your map and embed it into websites or share its own link. At the top right of your **Map View**, click **Publish**. This will give you the option to embed your map (giving you the html to do so). Alternatively you can copy the link, and share it that way.

![](https://github.com/barnarderc/carto-tutorial/blob/master/images/publish2.JPG?raw=true)

- - -

###Additional Resources

While this tutorial has gone over an introduction to using CARTO, the website itself has created many tutorials to go over more intermediate mapping projects. Some tutorials that may be useful to combine with this tutorial include:

- [Adding lines from point data](https://carto.com/docs/tutorials/gps_track/)
- [Creating a Torque Heatmap](https://carto.com/docs/tutorials/heatmap/)
- [Custom Map Interactivity](https://carto.com/docs/tutorials/custom_interactivity/)
- [Sharing Your Map](https://carto.com/docs/tutorials/sharing_maps/)
- [Merging Two Datasets](https://carto.com/docs/tutorials/merging_data/)





