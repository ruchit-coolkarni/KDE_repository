# Description of Methodology
**Step 1: Selection of Station Datasets**

To determine which station datasets to include in our analysis, we apply a selection criterion based on data availability. Specifically, a station dataset is included if it contains at least 10% of rainfall records within its available record period. This threshold ensures that only stations with sufficient data coverage are considered for further analysis.

**Step 2: Applying Quality Control Checks on Rainfall Values**

We implement a quality control (QC) process to assess the reliability of rainfall values from all selected station datasets. The following figure illustrates how the data quality control check is applied to each rainfall value. See Figure below for details of the QC procedure.
![image](https://github.com/user-attachments/assets/c9c05bf6-4272-4b5d-ab4c-c9e9204600b1)

**Step 3: Calculating 99th Percentile threshold for each chosen station dataset**

We calculated the 99th percentile of rainfall across NSW at 5 km resolution using the Australian Gridded Climate Dataset (AGCD), as instrumental records vary in start and end dates. The 99th percentile, based on wet days (rainfall ≥ 1.00 mm) relative to the 1910–2023 average, was extracted at gauge locations

**Step 4: Getting the List of Extreme Rainfall Days**

A day is a called an Extreme Rainfall Day if at least one station present in the network crosses it's 99th percentile threshold value

**Step 5: Determining the Number of Stations Recording Rainfall ≥ 1.00 mm on Extreme Rainfall Days**

We identify the number of stations that recorded rainfall of at least 1.00 mm on days classified as extreme rainfall events.

**Step 6: Calculating the Active Station Count for Each Year with Extreme Rainfall Days**

We calculate the number of active stations for every year in which an extreme rainfall day was recorded.

**Step 7: Assigning Wet to Active Station Ratio to each Extreme Rainfall Day**

For Every Extreme Rainfall Day we got , we assigned an Wet to Active Station Ratio. Given by Ratio = Number of stations recording rainfall ≥1.00 mm on the Extreme Rainfall Day / Active station count for that year. Definition of Active Station count has been defined in the paper (See section 2.3)

**Step 8: Classification of Widespread vs Isolated Events**

See Figure below for details of the classification
<img width="714" alt="Widespread vs Isolated" src="https://github.com/user-attachments/assets/8ac817de-aef2-4615-8c74-b8daca23afe5" />

**Step 9: Visualizing Rainfall Dot Maps for Each Identified Widespread Event**

We generate dot maps to visualize rainfall distribution for each widespread extreme rainfall event identified in the study.

**Step 10: Applying Adaptive Kernel Density Estimation**

Adaptive Kernel Density Estimation (KDE) is employed to reveal the underlying structure of rainfall data. Unlike standard KDE, adaptive KDE adjusts to spatial variations, reducing bias in areas with clustered stations.We created rainfall heat maps for each day in a particular widespread extreme rainfall event. The heat maps gave the spatial distribution of rainfall throughout the NSW region. We used a Gaussian kernel and bandwidth factor of 1.5 to detect the underlying density estimate, i.e. the region where rainfall density was highest. A bandwidth factor of 1.5 was applied using Silverman’s rule of thumb 

**Step 11: Identifying and removing Coastal Widespread Extreme Rainfall Event**

In the New South Wales GeoJSON file, unique polygon council boundaries east of the Great Dividing Range were identified. If the highest KDE peak for each day of a widespread extreme rainfall event falls within these polygons, the event is classified as a Coastal Widespread Extreme Rainfall Event and excluded from this analysis.

**Step 12: Widespread Event Extreme Rainfall Pattern**

Identifying the daily centres of the highest KDE density and connecting them over days allowed us to visualise the progression of the event. This resulted in a pattern that represents the movement of extreme rainfall in a particular widespread event.

**Step 13: Removing Random 50 stations from the network**

We randomly removed 50 stations from the network to manually observe the consistency of the extreme rainfall patterns identified for each widespread extreme rainfall event.

**Final Step 14: Applying the Dynamic Time Warping Statistical Test**

We calculated KDE density peaks for each day in a stepwise manner after removing 50 stations from the network, corresponding to days identified in each widespread extreme rainfall event. The Dynamic Time Warping (DTW) statistical test was then applied to determine the minimum and critical station density thresholds required to study historical extreme rainfall patterns.
