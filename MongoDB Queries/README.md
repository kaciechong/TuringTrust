#  Overview: 
### 1. `drives_wiped_sucessfully_multiple_times.ipynb`
   - **Purpose**: To analyze the total number of drives that have been wiped successfully more than once over time, specifically grouped by month, and assess the effectiveness of recent initiatives aimed at optimizing the drive wiping process. The intention is to minimize wasted time and effort by ensuring that workers do not spend unnecessary resources wiping devices that do not require it. By examining the trends over time, we can evaluate whether the implemented changes have had a positive impact on operational efficiency.
   - **Hypothesis**: The number of drives wiped unnecessarily (successfully wiped more than once) will decrease over time, particularly after the implementation of new guards.
   - **Findings**: There is a **noticeable decrease over time in number of drives wiped unnecessarily**, with no month in 2024 with more than 10 drives wiped unnecessarily.
   - **Further Investigation**: Investigate if the reason there are still unnecessary wipes could likely be due to mistyping the asset ID – when an asset ID is mistyped, it must be re-erased.
   - **Model**: [MongoDB Charts](https://charts.mongodb.com/charts-project-0-beoqpwb/dashboards/66ed6f58-5025-4323-87af-e63522a514c5/charts/6cceedc3-be2c-4caa-9c8e-570071b9a8a5)

### 2. `average_speed_of_successful_wipes.ipynb`
   - **Purpose**: To analyze the trend in average erasure elapsed times of successfully wiped drivesover time, specifically grouped by month, to ensure we are effectively managing and optimizing our erasure processes while also taking improved device donations over time that take less time to wipe; this ultimately improves operational efficiency.
   - **Hypothesis**: The erasure times are decreasing over time due to newer device donations which take less time to wipe.
   - **Findings**: There is some fluctuation in the average times, with notable peaks and valleys; however, there is **no downward trend**.
      - Notes:
           - The average erasure time recorded in December 2021 was just 13 seconds. This unusually low time can be attributed to it being a testing period during which only one device was wiped, resulting in this specific measurement.
           - Noticeable peaks in September, Novemeber 2022 and July, October 2023 - possible problematic devices or more complex erasure processes involved in those months
           - Prediction: The introduction of more complex devices alongside simpler ones could lead to higher average times, as newer devices may require specific handling or longer processes.
   - **Reccomendations**:
        - Investigate Specific Months: Look into the data for specific months with unusually high average erasure times to understand what specific devices were processed with slow speeds and whether there were operational changes. 
        - Categorize Erasures by Device Type: Implement a classification system to categorize erasure data by device type, including specifications like RAM, storage capacity, and manufacturer. This will enable a more nuanced analysis of which device categories are associated with longer erasure times, allowing for targeted strategies to improve processes for specific types of devices.
   - **Model**: [MongoDB Charts](https://charts.mongodb.com/charts-project-0-beoqpwb/dashboards/66ed6f58-5025-4323-87af-e63522a514c5/charts/69368530-84e5-45fa-a3f0-c2fac351ba22)
     
### 3. `long-term_average_speed_of_successful_wipes.ipynb`
   - **Purpose**: To find the long-term average erasure elapsed times of successfully wiped drives to know how much of the operational time goes toward wiping devices (related to query #2)
   - **Findings**: Across all months, it takes an average of **1 hour and 16 minutes** to successfully wipe a drive.

### 4. `erasure_rate_by_interface_success.ipynb`
   - **Purpose**: To find the average erasure rate (gb/minute) for each interface type to find which interface types have the most efficient erasure times.
   - **Findings**:
     - NVMe drives exhibit a significantly higher average erasure rate (about 110 GB/min), making them the fastest option by a large margin.
     - SAS drives have the second-highest erasure rate, though it is much lower than NVMe.
     - SATA, USB, and SSD interfaces (e.g., SATA/SSD) show relatively low erasure rates. For example, SATA drives are barely above USB and IDE in speed. These interfaces are not ideal for high-speed operations and could be de-prioritized in tasks where faster completion is a priority.
   - **Recommendations**:
     - Prioritize NVMe and SAS Drives: Focus on these high-throughput drives during peak operational times for faster turnaround.
     - Infrastructure for High-Speed Interfaces: Invest in equipment specifically optimized for NVMe and SAS drives to fully utilize their higher erasure rates.
     - Consider whether it’s cost-effective to continue handling extremely slow interfaces like IDE and USB
   - **Further Investigation**: The average erasure rate for **SATA/SSD** is substantially lower than the manufacturer’s advertised write speed. Investigate further if the slow rates are due to outliers by creating a scatter plot that looks at each drive individually; We can observe the scatter plot to see if most SATA/SSD data points are actually clustered at lower rates
   - Real Average for SATA/SSD: 5.188 GB/min
   - Advertised:
     - Write-up: 19.92 GB/min
     - Read-up: 31.64 GB/min
   - **Model**: [MongoDB Charts](https://charts.mongodb.com/charts-project-0-beoqpwb/dashboards/66ed6f58-5025-4323-87af-e63522a514c5/charts/e3607c90-2655-4847-800e-0840140d5fcc)

### 5. `erasure_rate_for_SATA/SSD.ipynb`
   - **Purpose**: To find the erasure rate (gb/minute) of individual drives with interface type SATA/SSD; the goal is to see the disk's serial number and model of successfully wiped devices on a scatter plot to observe if the slow rates in SATA/SSD drives are due to outliers (in reference to query 4).
   - **Findings**: 
   - **Further Investigation**: 
   - **Model**: [MongoDB Charts]()
     
Comparative Results: Real-world erasure rates for SATA drives are notably lower than the manufacturer’s advertised speeds:
Hardware specifications.
Development of a test rig to replicate conditions.
Supporting ticket submissions to Blancco for additional insights.
Visualization and Documentation
Use MongoDB Charts to create scatter plots and box plots for visual representation of the erasure times versus capacity for different interface types.
Review the "Erasure Time vs Capacity" scatter plot in MongoDB Charts specifically for SATA/SSD drives to better understand performance trends and anomalies.
Insight: When we look at specific examples of SATA/SSD, write speed is substantially lower than the manufacturer’s advertised write speed → recommendation: investigate that further because we can speed up → delve into hardware specs, develop test rid, support ticket with Blancco

