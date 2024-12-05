# The Turing Trust Data Analysis Project

* [Final Analysis Report](https://www.canva.com/design/DAGXr81qhjQ/1NHgjnik3NnQPdNrXbX4ow/edit?utm_content=DAGXr81qhjQ&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

* Company Overview: The Turing Trust aims to refurbish donated IT equipment by securely erasing data, installing educational software, and providing resources to those who need them to schools in Malawi.

* Purpose: This project aims to analyze various aspects of the drive-wiping process specified on Blancco hardware erasure reports by developing MongoDB queries. By identifying inefficiencies across various drive types and providing meaningful metrics on the erasure performance, I aim to develop actionable recommendations for The Turing Trust to improve resource management and streamline its device-wiping process, which constitutes a significant portion of its operations.

* Impact on The Turing Trust: By minimizing unnecessary wipe cycles and improving wipe speeds, The Turing Trust can reduce operational time and resource costs, enabling faster device refurbishment.

* Tech Used:
  - MongoDB (NoSQL): To store, query, and aggregate drive wipe data.
  - Python:
    - pandas: For data processing and calculations (like adjusted total drives)
    - Matplotlib: To create the bar chart visualizing wipe trends.
    - Seaborn: To create statistical plots (box and whisker).
  - Jupyter Notebook: To document and run the entire workflow interactively.
  - JSON: the data format used to store and transfer Blancco data, integrating seamlessly with MongoDB

* Folder Structure: 
1. Data: Instructions for accessing the data cluster as a database user (via connection IP address)
   - Contains Blancco data erasure reports saved in JSON format
3. MongoDB Queries: Jupyter Notebook files for data analysis
4. Visualizations: Files of data visualizations created on Jupyter Notebook

* Reflection: 
This data science project has been an invaluable experience, both in terms of technical growth and the development of actionable insights for The Turing Trust. The central aim of analyzing the drive-wiping process and optimizing resource management has allowed me to dive deep into MongoDB queries and work with a large dataset to uncover inefficiencies in the current operations. Through this process, I not only honed my skills in data collection, analysis, and visualization but also contributed to enhancing the overall efficiency for the trust. The initial hypothesis centered on identifying inefficiencies in the drive-wiping process, including redundant wipes, variability in wipe speeds, and failure messages that could lead to wasted resources. I was able to confirm or deny some of these hypotheses and present actionable recommendations that can significantly impact operational time and cost. The collaboration with Blancco software experts was instrumental in shaping the analysis, ensuring that I was addressing the right questions and that my methodology was aligned with best practices in data erasure. I am extremely grateful for the help and advice provided by Steve Cook, the IT Development Manager, with whom I worked closely throughout the project. We met twice a week to discuss potential queries, and his feedback on my work was invaluable. His expertise and guidance were instrumental in refining my queries and ensuring that I was on the right track, which significantly improved the quality and efficiency of the analysis. As a data scientist, this project reinforced the importance of asking the right questions and aligning technical work with business objectives. The ability to distill complex data into actionable insights, backed by solid analysis, is a skill that I will continue to refine as I move forward in my career.  

Reflection on tools used:
I also gained an appreciation for how well-structured databases, like MongoDB, can facilitate complex data analysis tasks, especially when dealing with large-scale data sets and varied formats. I believe MongoDB is a solid tool for an analysis project at The Turing Trust to store and query the data. In the initial stages of the project, I primarily worked with MongoDB Charts for data visualization. However, as I progressed, I started to notice its limitations. For example, MongoDB Charts is not compatible with certain query commands, such as $lookup, which hindered some of the more complex data manipulations I wanted to perform. Additionally, I found that it lacks a redo/undo feature, which can be quite frustrating when making errors or needing to correct mistakes during the visualization process. These limitations led me to seek alternative approaches to enhance my analysis and ensure greater flexibility in my work. Therefore, I moved the visualization platform to Jupyter Notebooks where I worked with Python. As a result, I dedicated a lot of time to getting more familiar with Python’s libraries for data manipulation and visualization, which will undoubtedly be useful in future data analysis projects and jobs. I particularly enjoyed the flexibility of using Jupyter Notebooks and GitHub together, as they complemented each other very well. I wrote all my code in Jupyter Notebooks, which allowed me to seamlessly develop and test my analysis. Once the code was complete, I could easily upload the notebooks to GitHub, where I added detailed descriptions and included files for every visualization. This workflow helped me keep everything organized, provided a clear record of my progress, and made it simple to share and collaborate on my work. Using MongoDB's Aggregation Framework alongside visualization tools provided not just raw numbers but also visual patterns that revealed the underlying issues more clearly. It was incredibly rewarding to translate raw data into a visual format that could quickly communicate trends. However, the project was not without challenges. Dealing with typos and capitalization differences in the data and rare instances, such as reports with no asset ID, required a great deal of attention. There were times when fine-tuning the queries or reformatting the data seemed daunting, but these challenges provided significant learning opportunities, and I believe double-checking my queries has become second nature. 


