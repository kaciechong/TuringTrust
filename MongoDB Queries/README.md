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

### 4. `RAM_trends.ipynb`
   - **Purpose**: To analyze RAM types of wiped devices, specifically grouped by month to see the trend over time, to ensure we are effectively managing device donations that have newer RAM types. The goal is to ensure that devices with newer and more advanced RAM types are prioritized when receiving donations. By tracking RAM types, you can ensure that your device donation program remains aligned with the latest technology trends, helping to provide recipients with more capable and future-proof devices.
   - **Hypothesis**: Never memory types (DDR3 and DDR4) are increasing while older memory types (DDR and DDR2) are decreasing over time.  
   - **Findings**: DDR and DDR2 memory types have seen a significant decline, becoming essentially obsolete by August 2024.
DDR3 and DDR4 remain the most common memory types in use, with both showing upward trends. While DDR3 has historically been the most common, DDR4 is steadily increasing in prevalence and is expected to continue growing.
   - **Reccomendations**:
        - Future analyses should consider incorporating Salesforce data to more accurately track memory type trends based on the actual donation dates. This approach will help ensure that devices with newer RAM types are prioritized in the donation process, leading to better decision-making and optimization of device donations.

### 5. `erasure_rate_by_interface_success.ipynb`
   - **Purpose**: To calculate the average erasure rate (GB per minute) of successfully wiped drives for each interface type, identifying which interface types have the most efficient erasure times. This analysis will enable the Turing Trust to prioritize acquiring devices with faster erasure capabilities, improving overall operational efficiency. Additionally, providing accurate erasure speed estimates based on interface type will enhance customer service by offering realistic timelines for secure data erasure services, catering to customer demands for reliable and prompt processing.
   - **Findings**:
     - NVMe drives exhibit a significantly higher average erasure rate of 107.10 gb/min than all of the other interface types, making them the fastest option by a large margin
     - Although SAS drives, with a rate of 10.73 gb/min, have the second-highest erasure rate, their performance is still significantly slower than NVMe drives. Their erasure rates are closer to those of the other interface types, which fall within a similar range: SAS/SSD = 7.67 gb/min, SPI = 7.34 gb/min, SATA = 6.25 gb/min,  USB/SSD = 5.68 gb/min, SATA/SSD = 5.18 gb/min, SATA/SSHD = 4.17 gb/min, EMMC = 4.01 gb/min,  IDE = 1.92 gb/min, USB = 0.34 gb/min

### 6. **Further Investigation of Previous Query**: `Distribution_of_rates.ipynb`
   - **Purpose**: By creating a box-and-whisker plot for each interface type, we can observe the variability between interface types and the difference in central tendency.
   - **Box & Whisker Plot Development**:
     - Create a data frame for easier data manipulation and simplifies grouping and aggregation.
     - Handling Outliers: The Interquartile Range (IQR) method was applied to identify and remove outliers for each interface type for better visualization.
     - For each interface type, the 1st quartile (Q1) and the 3rd quartile (Q3) were calculated.
     - The IQR was computed as the difference between Q3 and Q1, and outliers were defined as values outside the range [Q1 - 1.5 * IQR, Q3 + 1.5 * IQR].
     - The seaborn library was used to create the boxplot to visualize the distribution of data, including medians, quartiles, and potential outliers.
   - **Findings**:
      - NVMe actually appears to have a similar erasure rate to other high-performing interface types when considering its median value. However, it is highly variable due to extreme outliers, skewing its average rate higher than it might realistically be for most cases.
      - SAS/SSD shows the highest erasure rates overall, with the largest maximum and median rates. It has higher variability, but this variability is generally within high-performance ranges.
      - USB/SSD has a unique distribution: the upper quartile is particularly high, with 25% of data exceeding ~10 GB/min, showing that USB/SSD can achieve high speeds in some instances. However, the median rate (~2.5 GB/min) is much lower, suggesting that typical performance is significantly slower.
      - IDE contains a few low-performing outliers, which reinforce its already slow and narrow erasure rate distribution.
      - SAS has a median erasure rate similar to NVMe but shows less variability. It achieves higher minimum rates compared to NVMe but a lower maximum, indicating a more consistent but slightly less extreme performance compared to SAS/SSD.
      - SATA/SSD displays a susceptibility to outliers, often skewing its erasure rates, and its overall performance tends to be on the lower side compared to NVMe or SAS/SSD, with a narrower distribution and lower maximum values.
      - USB shows low erasure rates with very little variability. Its overall performance remains consistently at the lower end of the spectrum.
      - SPI stands out for its remarkable consistency, with erasure rates tightly clustered around ~7 GB/min. The lack of variability suggests it delivers steady but moderate performance.

### 7. `rig_faster.ipynb`
   - **Purpose**: To determine whether wiping devices on the rig is generally faster than wiping them directly on the device. This will help us assess if it would be more efficient to wipe all devices on the rig instead.
   - **Hypothesis**: Wiping on the rig will, in most cases, be faster and will show a significant reduction in time compared to wiping on the device.
   - **Findings**:
     - Out of 61 devices wiped successfully on both the rig and the device:
     - The rig is faster 34 times, while the device is faster 27 times.
     - Positive values (device faster) occur relatively frequently, showing that the device often outpaces the rig in wiping speed.
     - The average wipe time difference is -103.19 seconds, meaning that, on average, wiping on the device takes approximately 103.19 seconds less than wiping on the rig. This result disproves the hypothesis that the rig is generally faster than the device in terms of wipe time.
    
### 8. `dataframe_with_rigwipemessage.ipynb` + `Analyzing_dataframe.ipynb`
   - **Purpose**: To identify the significance of specific erasure failure messages and assess their impact on the probability of achieving a successful wipe on the rig; we want to see how fatal erasure messages are after a device wipe to see if it is worth taking the time to wipe it on the rig.
   - **Findings**:
     - Look at the last data frame in 'Analyzing_dataframe' file to see the failure rates for each failure message:
     - Messages to Scrap (Above 50% Failure Rate): Messages with a failure rate above 50% (indicated by those above the red line) suggest that the rig wipe is highly likely to fail. These failure messages should be considered for scrapping as the chances of success are low.
     - However, it's crucial to understand the context of each failure message before deciding to scrap it. For example, while the message “Read errors count reaches or exceeds the configured threshold” has a failure rate of 54%, it also indicates that the drive is unhealthy.
     - Messages Not to Scrap (Below 50% Failure Rate): Messages with a failure rate below 50% (below the red line) are generally more promising, with a higher chance of a successful wipe on the rig. These messages indicate that the wipe could still succeed and are worth further investigation.
