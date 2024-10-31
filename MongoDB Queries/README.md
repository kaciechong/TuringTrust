#  Overview: 
### 1. `drives_wiped_sucessfully_multiple_times.ipynb`
   - **Purpose**: To analyze the total number of drives that have been wiped successfully more than once over time, specifically grouped by month to test hypothesis
   - **Hypothesis**: The number of drives wiped unnecessarily (successfully wiped more than once) will decrease over time, particularly after the implementation of new guards.
   - **Goal**: To assess the effectiveness of recent initiatives aimed at optimizing the drive wiping process. The intention is to minimize wasted time and effort by ensuring that workers do not spend unnecessary resources wiping devices that do not require it. By examining the trends over time, we can evaluate whether the implemented changes have had a positive impact on operational efficiency.
   - **Findings**: There is a **noticeable decrease over time in number of drives wiped unnecessarily**, with no month in 2024 with more than 10 drives wiped unnecessarily.
   - **Further Investigation**: Ivenstigate if the reason there are still unnecessary wipes could likely be due to mistyping the asset ID – when an asset ID is mistyped, it must be re-erased.
   - **Model**: [MongoDB Charts](https://charts.mongodb.com/charts-project-0-beoqpwb/dashboards/66ed6f58-5025-4323-87af-e63522a514c5/charts/6cceedc3-be2c-4caa-9c8e-570071b9a8a5)

### 2. `average_speed_of_successful_wipes.ipynb`
   - **Purpose**: To analyze the trend in average erasure elapsed times of successfully wiped drivesover time, specifically grouped by month to test hypothesis
   - **Hypothesis**: The erasure times are decreasing over time due to newer device donations which take less time to wipe.
   - **Goal**: To ensure we are effectively managing and optimizing our erasure processes while also taking improved device donations over time that take less time to wipe, ultimately improving operational efficiency and customer satisfaction.
   - **Findings**: There is some fluctuation in the average times, with notable peaks and valleys; however, there is **no downward trend**.
      - Notes:
           - The average erasure time recorded in December 2021 was just 13 seconds. This unusually low time can be attributed to it being a testing period during which only one device was wiped, resulting in this specific measurement.
           - Noticeable peaks in September, Novemeber 2022 and July, October 2023 - possible problematic devices or more complex erasure processes involved in those months
           - Prediction: The introduction of more complex devices alongside simpler ones could lead to higher average times, as newer devices may require specific handling or longer processes.
   - **Reccomendations**:
        - Investigate Specific Months: Look into the data for specific months with unusually high average erasure times to understand what specific devices were processed with slow speeds and whether there were operational changes. 
        - Categorize Erasures by Device Type: Implement a classification system to categorize erasure data by device type, including specifications like RAM, storage capacity, and manufacturer. This will enable a more nuanced analysis of which device categories are associated with longer erasure times, allowing for targeted strategies to improve processes for specific types of devices.
   - **Model**: [MongoDB Charts](https://charts.mongodb.com/charts-project-0-beoqpwb/dashboards/66ed6f58-5025-4323-87af-e63522a514c5/charts/69368530-84e5-45fa-a3f0-c2fac351ba22) 
