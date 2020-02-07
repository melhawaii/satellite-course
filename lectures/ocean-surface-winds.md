# Ocean Surface Winds

![QuikSCAT, 01/03/2004](../.gitbook/assets/image%20%28157%29.png)

Ocean wind is defined as the motion of the atmosphere relative to the surface of the ocean.

Typically, ocean winds are measured very close to the ocean surface by buoys, platforms, and ships. The most common reference height for near-surface ocean wind measurements is **10 meters above sea level**.  
  
Satellite ocean wind measurements are done **using both passive and active instruments.**

Today, the combination of all available satellite wind measurements can provide **global coverage** over the ice-free oceans at **multiple times per day.**

Sensors operate at microwave frequencies -&gt; can make measurements day and night and under nearly all-weather conditions.

Both active \(radar scatterometers\) and passive \(radiometers\) microwave instruments are capable of retrieving the ocean surface wind speed.

Active microwave instruments are also capable of retrieving the wind direction.

Microwave measurements are inaccurate in regions of heavy rain and close to coasts.

Typical spatial resolution is ~ 25km.

## Passive sensors – basic principle

The ocean surface responds quickly to the motion of the air above, which provides a distinct **roughness** pattern depending on the relative speed and direction of the wind with respect to the ocean surface.

The roughness of the ocean surface provides a specific “**brightness**” which can only be observed using passive microwave radiometers;

With the right combination of specific microwave wavelengths and processing algorithms, the brightness of the ocean surface can be accurately translated to a near-surface wind speed.

## Active sensors – basic principle

Scatterometry uses surface roughness and pulse angle to get wind direction and speed.

The backscatter of scatterometer pulses is sensitive to sea surface roughness, which can be translated to **wind speed** \(see above\).

![](../.gitbook/assets/image%20%2845%29.png)

The backscatter is also sensitive to the pulse direction relative to the **wind direction.**

For any wind speed, the backscatter returned to the sensor is  
- maximal with the pulse pointed upwind  
- minimal with the pulse pointed ****crosswind

Problem: A suite of speeds and directions could explain a single measurement.

![](../.gitbook/assets/image%20%2828%29.png)

Solution:   
 - Measure backscatter at several pulse directions.   
 - Then solve for the wind speed and direction that best fits all of the measurements.

![](../.gitbook/assets/image%20%286%29.png)

## Ocean Surface Winds - sensors

![From: http://www.remss.com/measurements/ccmp/](../.gitbook/assets/image%20%2859%29.png)

## CCMP

The Cross-Calibrated Multi-Platform \(CCMP\) gridded surface vector winds are produced using satellite, moored buoy, and model wind data, and as such, are considered to be a Level-4 ocean vector wind analysis product.

The V2.0 CCMP processing now combines Version-7 RSS radiometer wind speeds, QuikSCAT and ASCAT scatterometer wind vectors, moored buoy wind data, and ERA-Interim model wind fields using a Variational Analysis Method \(VAM\) to produce four maps daily of 0.25 degree gridded vector winds.

Data is provided every 6 hours, and as monthly composites.

Spatial resolution is 0.25º

From 1987 – present.

## Wind stress & Wind stress curl

**Wind stress** is the shear stress exerted by the wind on the surface of the ocean.  
It is the force component parallel to the surface, per unit area, as applied by the wind on the water surface.

**Wind stress curl** is a measure of the rotation of wind: curl = dv/dx - du/dy  
In the northern hemisphere, positive curl is associated with upwelling of water, negative curl with downwelling.

Wind stress and wind stress curl are available for QuikSCAT and ASCAT data

## References

[https://sos.noaa.gov/datasets/ocean-surface-winds/](https://sos.noaa.gov/datasets/ocean-surface-winds/)  
  
[https://podaac.jpl.nasa.gov/OceanWind](https://podaac.jpl.nasa.gov/OceanWind)  
  
[http://www.remss.com/measurements/ccmp/](http://www.remss.com/measurements/ccmp/)  
  
  
  


