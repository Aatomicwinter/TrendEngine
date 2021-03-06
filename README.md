# TrendEngine

TrendEngine serves detection of change and trend in vegetation using remote sensing time series data.
The process consists of three steps: acquisition, analysis and visualization of results.

TrendEngine employs Google Earth Engine Python API on the backend and allows to choose from two datasets: 
- GIMMS NDVI with resolution of 8000 m 
- MODIS NDVI with resolution of 250 m 

An area of interest (AOI) can be described by selecting an individual geographic point or a bounding box of a polygon 
on the provided map.
Results for an individual geographic point provide details and are plotted on graphs. Textual output is also provided.
Results for polygons provide an overview. They are displayed on interactive maps with descriptive statistics.

The analysis can be performed using two algorithms:
- PolyTrend for trend detection in time series. It returns:
    - the type of trend: cubic, cuadratic, linear or concealed (no net change), 
    - direction of change
    - slope of the linear fit
    Results for points contain details: a plot with the time series data and the fitted regression line.
    Results for polygon provide an overview: each pixel of displayed map represents one of the values calculated by PolyTrend:
    type of trend, slope, significance or direction.

    The data used is an annual NDVI composite created using the maximum value. 

    See: Jamali, S., Seaquist, J., Eklundh, L., Ardö, J., 2014. 
    Automated mapping of vegetation trends with polynomials using NDVI imagery over the Sahel. 
    Remote Sens. Environ. 141, 79–89. https://doi.org/10.1016/j.rse.2013.10.019

- Detecting Breakpoints and Estimating Segments in Trend describes characteristics of changes. It employs two algorithms: generalization 
    and change detection.
    1/ Generalization returns a generalized trend and f-local-change depicted on a plot. 
    2/ Change detection uses Seasonal Trend Decomposition (STL) based on loess to derive trend components: trend, seasonal, remainder. 
    TrendEngine visualizes them on plots. Additonally,  textual output includes characteristics of major changes: 
    the start and end dates, magnitude and statistical significance. An overview of these values can be displayed on change maps if 
    a polygon is selected.
    
    The data is composited from bimonthly NDVI to monthly.
    
    See: Jamali, S., Jönsson, P., Eklundh, L., Ardö, J., Seaquist, J., 2015. 
    Detecting changes in vegetation trends using time series segmentation. 
    Remote Sens. Environ. 156, 182–195. https://doi.org/10.1016/j.rse.2014.09.010

TODO:
- improve map display - better legends
- fix option of using own dataset
