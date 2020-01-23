# 1. How to work with satellite data in R

This tutorial will show the steps to grab data in ERDDAP from R, how to work with NetCDF files in R and how to make some maps and time-series of chlorophyll-a concentration around the main Hawaiian islands.

 If you do not have the `ncdf4` and `httr` packages installed in R, you will need to install them:

`install.packages('ncdf4')   
install.packages('httr')`

## Downloading data in R

Because ERDDAP includes RESTful services, you can download data listed on any ERDDAP platform from R using the URL structure. 

For example, the following page allows you to subset monthly Chlorophyll a data from the blended ESA OC-CCI product:  
[https://oceanwatch.pifsc.noaa.gov/erddap/griddap/esa-cci-chla-monthly-v4-1.html](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/esa-cci-chla-monthly-v4-1.html)

Select your region and date range of interest, then select the '.nc' \(NetCDF\) file type and click on "Just Generate the URL".

![](../../.gitbook/assets/image%20%28160%29.png)

In this specific example, the URL we generated is :

[https://oceanwatch.pifsc.noaa.gov/erddap/griddap/esa-cci-chla-monthly-v4-1.nc?chlor\_a\[\(2018-01-01T00:00:00Z\):1:\(2018-12-01T00:00:00Z\)\]\[\(30\):1:\(17\)\]\[\(195\):1:\(210\)\]](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/esa-cci-chla-monthly-v4-1.nc?chlor_a[%282018-01-01T00:00:00Z%29:1:%282018-12-01T00:00:00Z%29][%2830%29:1:%2817%29][%28195%29:1:%28210%29])

You can also edit this URL manually.   
  
In R, run the following to download the data using the generated URL \(you need to copy it from your browser\):

`library(ncdf4)  
library(httr)`

`junk <- GET('`[`https://oceanwatch.pifsc.noaa.gov/erddap/griddap/esa-cci-chla-monthly-v4-1.nc?chlor_a[(2018-01-01T00:00:00Z):1:(2018-12-01T00:00:00Z)][(30):1:(17)][(195):1:(210)]`](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/esa-cci-chla-monthly-v4-1.nc?chlor_a[%282018-01-01T00:00:00Z%29:1:%282018-12-01T00:00:00Z%29][%2830%29:1:%2817%29][%28195%29:1:%28210%29])`', write_disk("chl.nc", overwrite=TRUE))`

## Importing the downloaded data in R

Now that we've downloaded the data locally, we can import it and extract our variables of interest:

* open the file

`nc=nc_open('chl.nc')`

* examine which variables are included in the dataset:

`names(nc$var)`

`[1] "chlor_a"`

* Extract chlor\_a:

`v1=nc$var[[1]]  
chl=ncvar_get(nc,v1)`

* examine the structure of chl:

`dim(chl)`

`[1] 361 313 12`

Our dataset is a 3-D array with 316 rows corresponding to longitudes, 313 columns corresponding to latitudes for each of the 12 time steps.

* get the dates for each time step:

`dates=as.POSIXlt(v1$dim[[3]]$vals,origin='1970-01-01',tz='GMT')   
dates`

`[1] "2018-01-01 GMT" "2018-02-01 GMT" "2018-03-01 GMT" "2018-04-01 GMT" "2018-05-01 GMT" "2018-06-01 GMT" "2018-07-01 GMT"   
[8] "2018-08-01 GMT" "2018-09-01 GMT" "2018-10-01 GMT" "2018-11-01 GMT" "2018-12-01 GMT"`

* get the longitude and latitude values

`lon=v1$dim[[1]]$vals   
lat=v1$dim[[2]]$vals`

* Close the netcdf file and remove the data and files that are not needed anymore.

`nc_close(nc)   
rm(junk,v1)   
file.remove('chl.nc')`

## Working with the extracted data - Creating a map for one time step

Let's create a map of Chl a for January 2018 \(our first time step\).   
You will need to download the [scale.R](https://oceanwatch.pifsc.noaa.gov/files/scale.R) file and copy it to your working directory to plot the color scale properly.

* set some color breaks

`h=hist(chl[,,1], 100, plot=FALSE)   
breaks=h$breaks   
n=length(breaks)-1`

* define a color palette

`jet.colors <-colorRampPalette(c("blue", "#007FFF", "cyan","#7FFF7F", "yellow", "#FF7F00", "red", "#7F0000"))`

* set color scale using the jet.colors palette

`c=jet.colors(n)`

* open a new graphics window

`x11(width=6, height=4.85)`

* prepare graphic window : left side for map, right side for color scale

`layout(matrix(c(1,2,3,0,4,0), nrow=1, ncol=2), widths=c(5,1), heights=4)   
layout.show(2)   
par(mar=c(3,3,3,1))`

* plot the Chl map

`image(lon,rev(lat),chl[,length(lat):1,1],col=c,breaks=breaks,xlab='',ylab='',axes=TRUE,xaxs='i',yaxs='i',asp=1, main=paste("Monthly Chlorophyll a concentration", dates[1]))`

* example of how to add points to the map

`points(202:205,rep(26,4), pch=20, cex=2)`

* example of how to add a contour \(this is considered a new plot, not a feature, so you need to use par\(new=TRUE\)\)

`par(new=TRUE)   
contour(lon,rev(lat),chl[,length(lat):1,1],levels=0.09,xaxs='i',yaxs='i',labcex=0.8,vfont = c("sans serif", "bold"),axes=FALSE,asp=1)` 

* plot color scale using 'image.scale' function from 'scale.R' script\)

`par(mar=c(3,1,3,3))  
source('scale.R')   
image.scale(chl[,,1], col=c, breaks=breaks, horiz=FALSE, yaxt="n",xlab='',ylab='',main='Chl a')   
axis(4, las=1)   
box()`
