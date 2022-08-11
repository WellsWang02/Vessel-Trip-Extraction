# Vessel-Trip-Extraction
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/LICENSE)

The processing of sattelite data for vessel trajectory preprocessing and trip extraction.


<p align="center">
  <img  src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/trip_extraction.png" width="420" height="250" hspace="20"/>
  
  <img  src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/demo-output.gif" width="360" height="250" />
</p>


  

In this [notebook](https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/Vessel_Trajectory_Processing_and_Trip_Extraction.ipynb) a series of methods were developed to process vessel trajectories. ***Noise Filtering*** filter the raw trajectories into cleaned and denoised trajectories. ***Stay point detection*** is conducted to cluster the stay points. Finally, ***Port labeling*** is conducted to classify if a stay point is ported, awaited for porting (near the lands), or stay at sea. Finally, ***Segmenation*** segments the vesssel sub-trajectories as vessel trip segements.


## Noise Filtering

The function of *noise detection* is provided. 
* Done with **DBSCAN:** eps=400, min_samples=4
* The function would generate a new column called *Noise*, where **Noise=-1** means the point is a noise.
* Detected noise will be removed
<p align="center">
  <img alt="Trajectory with Noise" src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/noises.png" width="420" height="250" hspace="20"/>
  
  <img alt="Trajectory Noise Filtered" src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/noise_filtered.png" width="360" height="250" />
</p>


## Stay Point Detection

The function of *stay point detection* is provided. 
* Done with new parameters **DBSCAN:** eps=400, min_samples=4
* Successfully recognize the missed stay points, and reduced the number of clusters by combining the nearby sub-clusters.
* The cluster would generate a new column called *Cluster*, where **Cluster=0,1,2....** means *stay points* are clustered as different numbers, while **Cluster=-1** means the points is detected as *on the way* (non-stay points).



## Port Detection

The port detection detect the previously clustered stay points and determines whether they are within a port positions. As known in the process of this notebook, in a lot of cases vessels won't directly went into the port but stay near it for a while. Hence, there is a need to recognize the stay points as ported or not.

<p align="center">
  <img src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/port_detection.png" width="460" height="250" />
</p>

## Segmentation

### Label the trajectories by trip and ports
Add a column **Segments** to identify the trip of the trajectories. For example, a trajectory with 3 trips can be labeled as:  
 * *Moving*(1) --> **Port**(2) --> *Moving*(3) --> **Port**(4) --> *Moving*(5) --> **Port**(6)

### Segment by created labels
The function in this part turn the trajectory into sub-trajectories(trips) using the previously defined *Segment* column. We store the segmented sub-trajectories in a dictionary called **trips**. To call on of the trip, we can simply use **trips[i]**, where *i* denotes the index of the trips the vessel is at through out the 3 months time span (the duration of our raw AIS data).
