# Vessel-Trip-Extraction
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/LICENSE)

The processing of sattelite data for vessel trajectory preprocessing and trip extraction.


<p align="center">
  <img  src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/trip_extraction.png" width="420" height="250" hspace="20"/>
  
  <img  src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/demo-output.gif" width="360" height="250" />
</p>


  

In this [notebook](https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/Vessel_Trajectory_Processing_and_Trip_Extraction.ipynb) a series of methods were developed to process vessel trajectories. ***Noise Filtering*** filter the raw trajectories into cleaned and denoised trajectories. ***Stay point detection*** is conducted to cluster the stay points. Finally, ***Port labeling*** is conducted to classify if a stay point is ported, awaited for porting (near the lands), or stay at sea. Finally, ***Segmenation*** segments the vesssel sub-trajectories as vessel trip segements.
