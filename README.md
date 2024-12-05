# README
# Wildfire-Research-Final

## Please see the final written report in file **Part 4 Written Report** and the academic poster summarizing this project in **Kilpatrick_poster_241202.pdf**.

## Project Motivation and Description 
Fresno is a mid-sized city in the California Central Valley, an economic hub predominantly contributing to the agricultural industry. As of 2020, the city boasts over half a million inhabitants; it is geographically centered between population centers in Northern California, Southern California, and Nevada. There is evidence to suggest that wildfires are increasing in not only size but also intensity. Airborne pollutants from wildfires in forests hundreds of miles away from Fresno still pose the risk of exacerbating chronic heart and lung conditions (Environmental Protection Agency). 

The links between increased wildfire-related pollution and increased mortality in California are well-documented (Chen et al., Gwon et. al). This analysis creates a predictive estimate for the impact of smoke caused by wildfires within 650 miles of Fresno. Then, data on deaths caused by chronic lower respiratory diseases inform the predictive estimate to quantify future impacts of smoke from a public health perspective. This project presents a refinement of the preliminary smoke estimate discusses the use of non-periodic time series forecasting techniques. This project generates correlations between the refined smoke estimate Fresno’s deaths caused by respiratory conditions. In turn, calling for a study detecting causal connections between the two phenomena.

## Data Citations
California Department of Public Health. Death Statistical Master File (Static), 1989-2013. Compiled by Center for Health Statistics and Informatics.

Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3.

## Licenses of Source Data
"USGS-authored or produced data and information are considered to be in the U.S. Public Domain." More information can be found [here](https://www.usgs.gov/information-policies-and-instructions/copyrights-and-credits)

Open for public use contingent on following [terms of service](https://data.chhs.ca.gov/pages/terms).

### Data Source Brief Summaries:
"This dataset contains counts of deaths for California residents by ZIP Code based on information entered on death certificates. Final counts are derived from static data and include out-of-state deaths of California residents. The data tables include deaths of residents of California by ZIP Code of residence (by residence). The data are reported as totals, as well as stratified by age and gender. Deaths due to all causes (ALL) and selected underlying cause of death categories are provided. See temporal coverage for more information on which combinations are available for which years" (CalHHS).

"These dataset uses these existing layers and utilizes a series of both manual processes and ArcGIS Python (arcpy) scripts to merge these existing datasets into a single dataset that encompasses the known wildfires and prescribed fires within the United States and certain territories. Forty different fire layers were utilized in this dataset... Overall, we believe this dataset is designed be to a comprehensive collection of fire boundaries within the United States and provides a more thorough and complete picture of fires across the United States when compared to the datasets that went into it" (Welty et al).

## Licenses of Source Code
This code example was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.3 - August 16, 2024

Tensorflow code for Convolutional Neural Networks adapted for Time Series Data licensed under the Apache License, Version 2.0 (the "License") you may not use this file except in compliance with the License. You may obtain a copy of the License at https://www.apache.org/licenses/LICENSE-2.0, Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

## Intermediary and Final Data Files/Schema
The following contextual files are generated upon creation of the repository or loaded in/duplicated:

1.  **README.md**
2.  **LICENSE.txt**
3.  **epa_air_quality_history_example.ipynb** Example source code provided via course materials
4.  **wildfire_geo_proximity_example.ipynb** Example source code provided via course materials. Note: this file is too large for github, and will not be available in the repository.
5. **USGS_Wildland_Fire_Combined_Dataset.json** Source data
6. **Wildfire Folder** Folder containing source code for reading in the source data's attributes (Reader.py, __pychache__, __init__.py)
7. **Course Project - City Assignments.xlsx** Spreadsheet containing student-city assignments
8. **Part 1 - Common Analysis Description.docx** Written description and instructions for course project part 1
9. **Part 2 Extension Plan Notebook.ipynb** Homework code for all analysis and visualizations for part 1 and part 2
10. **Part 1 Writeup** PDF containing visualization descriptions, reflection, and attributions
11. **Part 4 Written Report** PDF containing final report.
12. **Kilpatrick_poster_241202.pdf** Academic poster containing overview of research.
13. **Filtered geographic data for map creation** Folder containing geographic rasters and polygons for geographic analysis of Fresno.
14. **time_series.ipynb** Source sample code provided by Tensorflow for predictive model.

The following intermediary data files are generated by the scripts in this repository:

1.  **processed_fire_data.json** A JSON file of all original 130,000+ fire attributes with two new features: 'Closest_Distance_Miles' and 'Closest_Point'. Note: this file is too large for github, and will not be available in the repository; to generate, please run the 'Calculate All Shortest Distances' code block in **Part 1 Final homework Notebook.ipynb**.
2.  **filtered_fire_data.json** A JSON file with a fraction of the original fire attributes which satisfy two of the three filtering conditions:
- Fires in the last 60 years of wildland fire data (1961-2021).
- Fires within 650 miles of Fresno, CA.
3. **seasonal_filtered_fire_data.json** A JSON file with approximately 45,000 of the original fire attributes which satisfy all three filtering conditions:
- Fires in the last 60 years of wildland fire data (1961-2021).
- Fires within 650 miles of Fresno, CA.
- Defines the annual fire season as running from May 1st through October 31st.
4. **daily_summary_output.json** A JSON file containing two lists of attributes, for gaseous pollutants and particulate pollutants, resulting from calling the EPA's API.
5. **structured_aqi_output.json** A JSON file containing only the year, date, and air quality values from **daily_summary_output.json**.
6. **structured_aqi_output_with_average.json** A JSON file containing only the year, date, and a single average air quality index averaged from that day's AQI's.
7. **yearly_average_aqi.json** A JSON file containing a dictionary of each year and the aggregate (average) air quality index for that year.
8. **relevant_fires_with_scores** A JSON file containing all data from **seasonal_filtered_fire_data.json** with new features, including 'Cardinal_Direction_of_Fresno' and 'Smoke_Impact_Score'.
9. **smoke_by_year** A JSON file containing a dictionary of all years and the aggregate (sum) of all smoke impact scores for those years.
10. **annual_refined_stats.json**
11. **annual_smoke_impact_with_scores**
12. **correlation_inputs_with_mortality.csv** updated intermediary code file containing input variables for running the correlation algorithm.
13. **correlation_inputs.csv** intermediary file containing input variables for running the correlation algorithm.
14. **data-dictionary-deaths-by-zip-code.csv** CalHHS mortality data dictionary
15. **datapackage.json** CalHHS metadata
16. **Filtered geographic data for map creation** Filtered for just fresno, cartographic Boundary Files (2019) from the U.S. Census.
17. **Raw geographic data for map creation** Raw cartographic Boundary Files (2019) from the U.S. Census.
    - **cb_2019_us_zcta510_500k.cpg**
    - **cb_2019_us_zcta510_500k.dbf**
    - **cb_2019_us_zcta510_500k.prj**
    - **cb_2019_us_zcta510_500k.shp**
    - **cb_2019_us_zcta510_500k.shp.ea.iso.xml**
    - **cb_2019_us_zcta510_500k.shp.iso.xml**
    - **cb_2019_us_zcta510_500k.shx**
18. **Filtered_data_zipcause.csv** CalHHS data filtered by zip code and cause of mortality.
19. **final_estimates.json** save-able file for plotting.
20. **final_smoke_estimates_with_preliminary_and_refined.json** intermediary copy of all rounds of estimates.
21. **raw_all_calhhs_data.csv** original CalHHS data
22. **zip_filtered_raw_data.csv** intermediary file before filtering the CalHHS data into the **Filtered_data_zipcause.csv** file.
  
The following visualizations are displayed in the **Part 2 Extension Plan Notebook.ipynb**:

1. **Distribution of Smoke Impact Scores (Log Scale)**
2. **Annual Aggregated Smoke Impact Scores**
3. **Wildfires by Distance from Fresno (50-mile increments)**
4. **Total Acres Burned Per Year (1961-2020) for Fires Within 1800 Miles of Fresno**
- note: the "specified distance from your city" in the instructions has been interpreted to be the most recently mentioned distance, 1800 miles. This can be changed by toggling 'max_distance' in this graph's code under 'Total Acres Burned Per Year'
5. **Smoke Estimates (Divided by 50) vs. Gaseous and Particulate Pollutants (1961-2020)**
6. **Historical and Forecasted Smoke Estimates, CNN**
7. **Comparison of Smoke Impact Scores**
8. **CLRD Mortality-Informed Smoke Estimates**
9. **Total Deaths By Year (Chronic Lower Respiratory Diseases)**
10. **Fresno, CA (1989-2019) Deviation From Average Deaths due to CLRD, Controlling for Percentage of Population**
11. **Correlation Between Smoke Estimate and Annual Deaths Due to CLRD in 0-5 Years Following Wildfire Years** 

## Known Issues and Considerations
-   Wildfire data for 2021 not recorded in the source USGS dataset
-   The independently-generated smoke estimate is an oversimplification compared to standard air-quality impact indices standardly used in atmospheric science.
-   The choice of predictive model has both strengths and limitations.
-   Data quality may vary depending due to the datasets used by the USGS to create their combined dataset.

## Reproducibility and Citation
This homework follows reproducible research practices. Portions of the code has been text-generated by ChatGPT, OpenAI, 30 Oct. 2024. These portions are noted in the markdown of the code preceding them, including the prompt, and are wrapped in a function to contain them. Note that all portions of text-generated code have been edited from their original versions for logic, clarity, and usability.

If you use this data or code, please provide proper credit to the United States Geological Survey as the source of the data and the example notebook as a source of the software.
