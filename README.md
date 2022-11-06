# Drug Data Analysis using Matplotlib
This repo contains a jupyter notebook utilizing pandas data transformation for data visualizations using Matplotlib. Some level of understanding of statistical analysis should be had to properly understand the observations section of the notebook, as time has not permitted me to write a more accessible reading. Ultimately, the goal of this analysis was to see the any particular drug regimens efficacy at reducing tumor volume in test subject mice.

In this repo you will find:

|Notebook| Description|
|--------|------------|
|[Drug Regimen Analysis Notebook](regimen_notebook.ipynb)| A notebook containing the observational report and associated visualizations and data transformation that allowed for the reports observations.|

|Data|Description|
|----|-----------|
|[Mouse Meta](data/Mouse_metadata.csv)|This csv file contains the mouse data information, such as subject ID, what regimen they were trialed on, their sex, age, and weight.
|[Mouse Results](data/Study_results.csv)| This csv file contains the data associated to each subject ID over the period of 45 days in 5 day increments for tumor volume and observed metastatic sites.|

# Notebook Explanations
You will find this notebook broken into sections. Here I will describe the aim/purpose of each section with a brief on how it works.

### *Section I*: Observations and Thoughts
This section contains the overall distilled thoughts for the entirety of the notebook, what conclusions I drew from the total visualizations, and what I thought were the meaning intepretations of the data. 

### *Section II*: Initial Setup & Dataset creation
This section contains the imported dependencies for the notebook to run. Notably these are
1. matplotlib.pyplot for visualization and analysis 
2. pandas for data transformation and analysis
3. scipy.stats for analysis
4. numpy for functions
Also found in this section is the dataset importation and initial transformations. As the data came as two csv files, these were combined into one pandas dataframe. Duplicate subjects were removed from the data pool as well. 

### *Section III*: Dataset Summary Statistics
In this section, two ways to get and show summary statistics(mean, median, variance, standard deviation, standard error of mean) were used. 
One, a more line by line method, adding summary statistic columns one by one to a dataframe.
The second, a single line method utilizing pandas groupby function with the .agg, or aggregate function. This allows for an aggregate of functions to passed through at once. 
Ultimately, the tables are the same, just with considerations for line space taken. I also sort the values by standard error of mean to visualize the heiarchy and see if any regemins are suitable for further analysis.

### *Section IV*: Timepoint observations
This section is for looking at total count of timepoint data from the start of the timepoints, day 0, and at the end of the timepoints, day 45. This was done to see if there was any observable difference one could reason for the lack of subject consistency for overall timepoints. The utlimate reasoning for this is in section I as an observation. This section served as the data visualization for that observation.

### *Section V*: Bar Charts
This section contains two horizontal bar charts, one from pandas, and one from matplotlib. These bar charts aimed to visualize the total amount of data for each drug regimen using the availible timepoints. The thinking being that each timepoint existing for each regimen is its running count of datapoints. Ultimately, this is the overall charted visualization of Section IV.

### *Section VI*: Pie Charts
This section contains two pie charts. One pandas, one matplotlib. Their purpose is to visualize the gender distrubution of test subjects in the study, as an assurance if there was a particular leaning/favoring of subject gender morphology. 

### *Section VII*: Quartiles, Outliers, and Boxplots
This section aimed to establish statistical parameters for 4 particular drug regimens. These 4 drug regimens estbalished themselves as the only regimens to fall below a .5 SEM value.  Ultimately, after calculating the quartile values and estbalishing the interquartile range, no outliers were determined, and therefore no datapoints needed additional consideration for further analysis. A box/whisker plot was created to ultimately visualize the range/spread of the 4 drug regimens of current interest. These drugs can be changed out by adjusting the drugs in the `desired_treatments` list at the top of the section. Adjusting this list will not bother any further code/analysis as they all reference the list by index position, eg `drug_one_df = ... desired_treatments[0]`. The only section that won't change is the markdown table at the top of the section detailing what drug one through four are. Future revision of this notebook could/should remedy that. 

### *Section VIII*: Line Plot
This line graph is adjustable, as it seeks the datapoint of  `mouse_id['Mouse ID'][0]`. Simply changing the [0] to the indexed position of the desired mouse ID will give you the line graph of that mouse. I chose to do this instead of static mouse ID as it offers more future customizability, where a prompt might ask for the desired mouse ID, and a function would take that input and find the index value of the given mouse, and use that output. 

### *Section IX*: Scatter Plot
This section aimed to visualize the averaged data point scatter of tumor volume to the weight of mice, showing what might be a linear relationship between the weight of a mouse and the size of its tumor. To me, it makes sense that as the mass of the creature increases, the mass of the tumor it contains also increases. Some studies use the ratio of tumor volume to patient/subject weight as an indicator of patient outcome. The analysis/observation of this data is made with that in mind. 

### *Section IX*: Correlation and Regression
This section aimed to visualize the correlation and regression of the averaged data point scatter of tumor volume to the weight of mice. Ultimately, what it shows is a strong linear relationship of the scatter plot data, and a strong coeffiecient of determination for the relationship between the weight of a mouse and its tumor volume. The analysis and observation views this through the lens of the established idea of the ratio of tumor volume to patient/subject weight as an indicator of patient outcome.
