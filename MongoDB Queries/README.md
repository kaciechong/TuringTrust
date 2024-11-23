#  Overview: 
### 1. `drives_wiped_sucessfully_multiple_times.ipynb`
   - **Purpose**: To analyze the monthly trends in drives wiped successfully more than once and evaluate the effectiveness of new safeguards in preventing unnecessary re-wipes. Each wipe takes up time and uses a license, so it is important to ensure previously wiped drives are not erased again, thereby improving operational efficiency.
   - **Hypothesis**: The number of drives unnecessarily wiped (successfully wiped more than once) will decrease over time, particularly after implementing new safeguards in August 2022.
   - **Findings**: There is a **noticeable decrease over time in number of drives wiped unnecessarily**, with no month in 2024 with more than 10 drives wiped unnecessarily.
   - **Further Investigation**: Investigate if the reason there are still unnecessary wipes could likely be due to mistyping the asset ID – when an asset ID is mistyped, it must be re-erased.
      - To address the remaining instances in recent months after the implementation of the safeguards of       unnecessary wipes, I investigated whether mistyped asset IDs are a contributing factor. Mistyping         asset IDs often necessitates re-erasure, and addressing this issue could further reduce                   inefficiencies.
      - Asset ID Analysis: I manually reviewed the reports for each of the 54 disk serials, checking the        associated asset IDs to determine if mistyped asset IDs were the cause
         1. 9/54 devices (16.6%) were identified as having asset IDs that differed by 1-2 characters,    
            suggesting mistyping.
         2. 16/54 devices (29.6%) had completely different asset IDs, often linked to the same vendor,                disk serial, and interface type. These are cases when a single serial number is associated                with multiple asset IDs.
         3. 27/54 devices (50%), the same asset ID and erasure details were found. However, some reports              with the same erasure details showed overlapping wipe times, indicating a **Blancco software              glitch**.
         4. 2/54 devices (3.7%) had no asset ID recorded (e.g. IPAD).
   - **Reccomendations**:
      1. The potential recommendation to increase the size of asset IDs to prevent mis-typing is unnecessary, as only ~16% of the cases involved mistyped asset IDs.
      2. Collaborate with Blancco to address the glitch issue. Ensure that all known bugs, especially those involving overlapping wipe times or missing objects, are fixed.
      3. Implement automated checks within Blancco or a separate monitoring tool to detect potential duplicate wipes or data discrepancies in real time.
      4. Investigate the frequency of overlapping wipe times for the same erasure serial. This could reveal if the issue is widespread and provide insights into patterns or recurring events, such as specific times of day or hardware types, that contribute to the issue.

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
   - **Findings**: Real-world erasure rates for SATA/SSD drives are notably lower than the manufacturer’s advertised speeds:
Hardware specifications because most of the points on the scatter plot are clustered below 20 GB/min.
   - **Reccomendations**: 
      - Investigate Further: Conduct a deeper analysis of the factors contributing to the lower erasure rates.
      - Review Hardware Specifications: Examine the hardware specifications to identify any limitations that may affect performance.
      - Develop Test Rig: Create a dedicated testing setup to evaluate the erasure performance of different drives under controlled conditions. This rig should allow for consistent testing across various hardware and software configurations to identify optimal setups.
      - Contact Blancco’s support team to discuss the findings and seek their expertise on optimizing erasure processes. Provide them with data from the tests, and ask for recommendations on best practices or potential software updates that could enhance performance.
   - **Model**: [MongoDB Charts](https://charts.mongodb.com/charts-project-0-beoqpwb/dashboards/66ed6f58-5025-4323-87af-e63522a514c5/charts/32e79b80-4177-42f7-bf47-d25819bc1b2b)
     
