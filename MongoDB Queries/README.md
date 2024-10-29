#  Overview: 

* Contains Jupyter notebooks used to analyze Blancco erasure reports

### 1. `drives_wiped_sucessfully_multiple_times.ipynb`
   - **Purpose**: To analyze the total number of drives that have been wiped successfully more than once over time, specifically grouped by month to test hypothesis
   - **Hypothesis**: The number of drives wiped unnecessarily (successfully wiped more than once) will decrease over time, particularly after the implementation of new guards.
   -  **Goal**: To assess the effectiveness of recent initiatives aimed at optimizing the drive wiping process. The intention is to minimize wasted time and effort by ensuring that workers do not spend unnecessary resources wiping devices that do not require it. By examining the trends over time, we can evaluate whether the implemented changes have had a positive impact on operational efficiency.
   -  **Model**: [MongoDB Charts](https://charts.mongodb.com/charts-project-0-beoqpwb/dashboards/66ed6f58-5025-4323-87af-e63522a514c5/charts/6cceedc3-be2c-4caa-9c8e-570071b9a8a5)
