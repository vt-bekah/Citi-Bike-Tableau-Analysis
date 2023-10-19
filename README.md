# Citi-Bike-Tableau-Analysis
Jersey City Officials & Citi-Bike Leaders are looking for an analysis of Citi-Bike ride data to determine how to better serve the population and improve rider ship. The goals behind the scenes are to cut-down down on pollution and energy usage from vehicle traffic, improve citizen health, and make more money (of course).

# Features
* Download and clean the Citi Bike data selected for analysis
    * combine the monthly files into a single file
    * Adopt one headernaming convention (Citi Bike changed format between Jan 2021 and Feb 2021)
    * Update station latitude and longitude values such that each start station has a single identifer and each end station has a single identifier
* Create a summary map displaying station usage by ride count and trip time with an overlay of zip codes.
    * Allow filtering by year and month
    * Visually represent ride counts and trip time
* Explore usage by ride time, frequency, and location to determine if additional stations would be beneficial
* Explore subscriber vs. non-subscriber usage across ride time, frequency, and location to propose recommendations for increasing profit
* Create a report of findings and recommendations readable by non-data analysts (Citi-Bike_Usage_Analysis_2018-2022.md)
* Create a Tableau Story to support findings and recommendations usable by non-data analysts
* Publish the Tableau Story to Tableau's public site ([2018-2020_JC-CitiBike_Analysis/JCCiti-BikeUsageRevenue](https://public.tableau.com/app/profile/rebekah.aldrich/viz/2018-2020_JC-CitiBike_Analysis/JCCiti-BikeUsageRevenue?publish=yes)) 

# Results

Refer to [Citi-Bike_Usage_Analysis_2018-2022.md](Citi-Bike_Usage_Analysis_2018-2022.md)


# File Notes
* Data files are not uploaded to Github due to size of files
    * Download all 2018-2022 csv files, extract them, and place them in a folder named "raw-data"
    * Create a folder for clean-data to hold the exported data file(s)
* CleanData.ipynb cycles through the files in the raw-data folder and exports consolidate file(s) into the clean-data folder
    * The script requires all file names to follow the same pattern (note some files may have typos and need fixed prior to running the script)
    * Citi Bikes changed the data format between Jan 2021 and Feb 2021 so the script runs separately for Jan 2018 - Jan 2021 and Feb 2021 - Dec 2022. Then updates header names to align and merges the two chunks. Nulls are left in the columns that exist in one but not the other.
    * Citi Bikes data has multiple latitude / longitude locations tied to the same station name. As a result, this file consolidates latitude and longitude coordinates to a single latitude / longitude per station name by finding the average value use at each starting and each end location and overwriting the downloaded values
* Citi-Bike_Usage_Analysis_2018-2022.md contains the written analysis
* 2018-2020_JC-CitiBike_Analysis.twbx.twbx is the downloaded Tableau workbook found at [2018-2020_JC-CitiBike_Analysis/JCCiti-BikeUsageRevenue](https://public.tableau.com/app/profile/rebekah.aldrich/viz/2018-2020_JC-CitiBike_Analysis/JCCiti-BikeUsageRevenue?publish=yes) 

    

# References
* Downloaded csv files for Jersey City data 2018-2022: https://s3.amazonaws.com/tripdata/index.html
* Leveraged Tableau documentation to enhance multiple views: https://help.tableau.com/current/pro/desktop/en-us/design_and_analyze.htm


# Getting Started

## Prerequisites
* You must have a we browser to view the linked Tableau story.
* You must have an application capable of reading markdown (md) files to view the written analysis.
* To open and explore the Tableau workbook, you must have Tableau public installed locally.
* To execute the jupyter notebook file, you must have python, jupyter notebook, and pandas.

## Cloning Repo
$ git clone https://github.com/vt-bekah/Citi-Bike-Tableau-Analysis.git

# Built With
* Public Tableau 2023.2
* Python v3.10.11
* jupyter notebook v6.5.2
* jupyterlab v3.6.3
* conda v23.5.0


**Python Modules**
* pandas v1.5.3



