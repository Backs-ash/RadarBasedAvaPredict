# Snow Avalanche Detection with LIDAR and SONAR

## Introduction

Our project focuses on using LIDAR and SONAR technologies for early prediction and mitigation of snow avalanches in vulnerable mountain terrain. This ``README`` provides an overview of how these technologies work and their application in snow avalanche detection.

## Research and Pipeline

### Lidar Technology

- Lidar is an active ranging instrument that measures target distance using the time-of-flight principle.
- The sensor's position is determined through differential GPS (DGPS) triangulation.
- After georegistration, collected data is represented as (x,y,z) points, where z can represent single returns, multiple returns, or a full waveform, each with corresponding attributes like return intensity or transmit pulse information.
- Advanced systems can geolocate the entire waveform or all returns, resulting in a spatial vector.

### Snow Depth Calculation

- Calculating snow depth involves subtracting snow-free from snow-covered surface datasets.
- Specialized software packages like [Cloud Compare](http://www.danielgm.net/cc/) can directly subtract two point-cloud datasets, producing a difference cloud for point-wise or gridded analysis.
- For users without specialized software, an efficient method is to interpolate both snow-free and snow-covered point clouds to common grids and subtract the grid values.

### Optical Properties of Ice

- Ice's optical properties are described by the complex refractive index ``(m = n + ik)``, where n describes refraction, and k describes absorption (absorption coefficient).
- Table 1 provides values of k for ice at common lidar system wavelengths.             // Where is the table?
- Understanding the sensitivity of light transmission and absorption to snow grain size and liquid water content is crucial for assessing laser interaction with the snow surface.

### Noise Removal in Snowy Conditions

- Falling rain and snow can corrupt sensor measurements, especially for lidar sensors.
- However there exists a [method](https://ieeexplore.ieee.org/document/8575761) for removing snow noise using a 3D outlier detection algorithm, the dynamic radius outlier removal filter.
- This method accounts for variations in point cloud density with increasing distance from the sensor.
- It effectively removes snow noise while retaining environmental feature detail necessary for autonomous localization and navigation.

## Usage and Miscellaneous

### Key Datasets

- This study relies on three key datasets: snowpack simulations, snow depth observations, and avalanche hazard assessments.
- Snow cover models like Crocus or Snowpack are used to simulate detailed snow properties, aiding avalanche forecasting.
- Logistic regression models predict storm slab avalanche problems based on snowpack data.

### References

1. [LIDAR Measurement of Snow Depth: A Review](https://www.cambridge.org/core/journals/journal-of-glaciology/article/lidar-measurement-of-snow-depth-a-review/4419DF5C778946103080CB6187D434C0#R75)
2. [Using snow depth observations to provide insight into the quality of snowpack simulations for regional-scale avalanche forecasting](https://www.sciencedirect.com/science/article/pii/S0165232X20304109#:~:text=The%20model%20SURFEX%2FISBA%2DCrocus,up%20to%2050%20snow%20layers.)
3. [Dynamic Radius Outlier Removal Filter for Snow Noise Removal](https://ieeexplore.ieee.org/document/8575761)

These references provide further information and context for the technologies and methods used in this project. Users and contributors can explore these sources for relevant resources.
