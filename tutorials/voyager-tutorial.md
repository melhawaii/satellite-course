# Voyager tutorial

Voyager is an interactive map interface for visualizing and downloading oceanographic data that was developed by John Maurer from PacIOOS \([http://www.pacioos.hawaii.edu/voyager/](http://www.pacioos.hawaii.edu/voyager/)\). 

OceanWatch \(OW\) partnered with PacIOOS to develop a separate instance of Voyager specifically for OceanWatch data \(remote sensing data\), as well as to add some new features. 

The PacIOOS version of Voyager contains a lot more data types \(in situ, models, etc…\), go check it out as well! 

This tutorial will give a brief overview of Voyager. 

## Introduction to Voyager

Go to the OW Voyager viewer page: [http://www.pacioos.hawaii.edu/voyager/oceanwatch.html](http://www.pacioos.hawaii.edu/voyager/oceanwatch.html) 

On the Welcome screen, click on the “Help” tab and read through it to familiarize yourself with Voyager.

![](../.gitbook/assets/image%20%28167%29.png)

Close the Welcome screen

## Choosing a dataset

In the side bar, under “satellite data”:

* select the “MODIS \(chlorophyll\)” dataset.
* Select the variable “chlorophyll”
* Select a time span \(daily, weekly or monthly\).  Observe the difference in missing data due to clouds between all time spans. 
* Now select “monthly”. 
* Click on “oldest”.  This will automatically go to the earliest time step in the dataset. 

You should now have a map for June 2002.

![](../.gitbook/assets/image%20%28142%29.png)

## Map options

Click on the + sign next to “map options”, to expand the map options menu.

* There, you can change the color scale used to display the data and adjust the minimum and maximum for the color bar.
* At the very bottom of the side bar, click on “lat/lon” to add a graticule to the map.
* Click on “range”, then click on a location on the map to display lines of equal distance from that location. 
* Click on “range” again to remove the lines from the map.
* Click on “distance”, then on 2 locations on the map to calculate the distance between them.  What is the distance between Japan and California? Click on “change units” to get the distance on km. \(metric system for the win!\) 
* Click on “distance” again to clear the map.
* Click on “area” to calculate the area of a polygon on the map. Then clear the map.

## Overlays

* Select a new dataset: GOES-POES SST. Display the monthly SST for September 2015 in ºC.
* Under the “Navigation” tab, click on the + sign next to “maritime boundaries”, then select "EEZ".
* Unselect EEZ, then at the very top of the side bar, click on “set region”. Select “Hawaii”. Then “set region”. Click on a location close to Kailua-Kona. 
* In the menu that pops up, click on “all” on the “show data plot” row. This generates a time-series of SST at that location.

![](../.gitbook/assets/image%20%2822%29.png)

* Close the pop up window. 

## Area statistics

* Select monthly AVHRR P4.1+GAC SST. 
* In the side bar, below “map options”, click on the + sign next to “area statistics”. Click on “draw box”. 
* Click on a location on the map for the first corner of the box, then a second one. 
* Click on the marker in the center of the box, then again select “show data plot all”.  This can take a while to compute. Don’t make your box too big.   This computes statistics within that box \(depending on what you selected, average temperature, standard deviation, minimum, maximum for that whole box\). You’ll notice this dataset has a coarser spatial resolution.

![](../.gitbook/assets/image%20%28165%29.png)

* Click on “back” in the bottom left corner of the pop-up window, then click on “download data all”.  This generates a csv file of the whole time-series.

## Sharing and saving maps

* Now, at the top right of the screen, click on “link”. Copy the link, and paste in a new browser tab.  You should get the exact same map, with the same options. This makes it very easy to share maps with others. 
* In your pop-up window, click on “remove area” to clear the map.
* Zoom out until you can see the whole North Pacific. Then at the top right of the screen, click on “save image” then “get image”. This can take a while. Eventually, you will be prompted to save the image. It should look something like this:

![](../.gitbook/assets/image%20%2891%29.png)

