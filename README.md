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

<p align="center">
  <img src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/port_detection.png" width="460" height="250" />
</p>
