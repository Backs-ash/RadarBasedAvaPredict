# Snow Avalanche Detection with LIDAR and INFRARED

Our project focuses on using LIDAR and SONAR technologies for early prediction and mitigation of snow avalanches in vulnerable mountain terrain. This ``README`` provides an overview of how these technologies work and their application in snow avalanche detection.

## Research and Pipeline

## Lidar Technology

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
- Understanding the sensitivity of light transmission and absorption to snow grain size and liquid water content is crucial for assessing laser interaction with the snow surface.

### Noise Removal in Snowy Conditions

- Falling rain and snow can corrupt sensor measurements, especially for lidar sensors.
- However there exists a [method](https://ieeexplore.ieee.org/document/8575761) for removing snow noise using a 3D outlier detection algorithm, the dynamic radius outlier removal filter.
- This method accounts for variations in point cloud density with increasing distance from the sensor.
- It effectively removes snow noise while retaining environmental feature detail necessary for autonomous localization and navigation.

## Infrared Technology 

- An infrared based nondestructive testing will also be used to evaluate the structural integrity of a snowpack.
- Through the infrared techology thermal features like thermal inertia wil be extracted from the snowpack.
- The extracted features are used to map the [snowpack density](https://www.sciencedirect.com/science/article/abs/pii/S0034425722004291) and create thermal heatpacks which identify the '*weakness*' or '*strength*' of a snowpack.


## Hardware Requirements 
- A basic I/O device with the minimum technology to support Lidar and Infrared processing and detection.

## Usage and Miscellaneous

### Key Datasets

- This study relies on fout key datasets: snowpack simulations, snow depth observations,avalanche hazard assessments and the DN values of an area.
- Snow cover models like Crocus or Snowpack are used to simulate detailed snow properties, aiding avalanche forecasting.
- Glacier Winter Surface Mass Balance ( GWSMB ) is a dataset based on six glaciers across the French Alpines which contains data about ice and glaciers density and surface mass balance. Additionally, the spatio temporal reconstruction winter glacier mass balance is important for [assessing](https://tc.copernicus.org/articles/17/977/2023/) long term impacts of climate change on snowpacks.


### References

1. [LIDAR Measurement of Snow Depth: A Review](https://www.cambridge.org/core/journals/journal-of-glaciology/article/lidar-measurement-of-snow-depth-a-review/4419DF5C778946103080CB6187D434C0#R75)
2. [Using snow depth observations to provide insight into the quality of snowpack simulations for regional-scale avalanche forecasting](https://www.sciencedirect.com/science/article/pii/S0165232X20304109#:~:text=The%20model%20SURFEX%2FISBA%2DCrocus,up%20to%2050%20snow%20layers.)
3. [Dynamic Radius Outlier Removal Filter for Snow Noise Removal](https://ieeexplore.ieee.org/document/8575761)
4. [Crocus](https://gmd.copernicus.org/articles/5/773/2012/gmd-5-773-2012.pdf)
5. [Spatial and temporal vairability in snow density](https://www.sciencedirect.com/science/article/abs/pii/S0341816223005362)

These references provide further information and context for the technologies and methods used in this project. Users and contributors can explore these sources for relevant resources.
