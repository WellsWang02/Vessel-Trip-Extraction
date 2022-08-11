# Vessel-Trip-Extraction
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/LICENSE)


<p align="right">
  <img width="460" height="300" src="https://github.com/WellsWang02/Vessel-Trip-Extraction/blob/main/demo-output.gif">
</p>

The processing of sattelite data for vessel trajectory preprocessing and trip extraction.

In this notebook a series of methods were developed to process vessel trajectories. ***Noise Filtering*** filter the raw trajectories into cleaned and denoised trajectories. ***Stay point detection*** is conducted to cluster the stay points. Finally, ***Port labeling*** is conducted to classify if a stay point is ported, awaited for porting (near the lands), or stay at sea. Finally, ***Segmenation*** segments the vesssel sub-trajectories as vessel trip segements.
