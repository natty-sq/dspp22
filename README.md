# Data Science Project
# Powerlifting: differences between genders looking at total weight lifted in competition relative to lifters body-weight.

Powerlifting is a popular strength based sport where the goal is lifting the highest possible weight in 3 lifts: squat, bench, and deadlift. This project focuses only on full competitions where all 3 lifts are performed. It also only looks at non-equipped groups. 

**Project aims**

This project explores the relationship between gender and relative strength in competitive powerlifting. For this analysis, the lifters body-weight and total weight lifted were used to calculate relative strength.

note: all the weights used are in kilograms (Kg).

**Data source**

The dataset for this analysis was taken from the OpenPowerlifting Data Service. Please note that this dataset gets updated periodically, therefore the results of the analysis could slightly differ if they were run using the most up to date dataset. The set for this analysis was sourced after update on 10/04/26. 

Data sourced from: <url>https://openpowerlifting.gitlab.io/opl-csv/bulk-csv.html</url>

## EDA and data cleaning

For EDA, a ydata-profiling report has been generated. However, before creating the report, the powerlifters names have been anonymised by assigning a unique index to each lifter. This was done to follow data protection as well as remove bias on the analysis.

### Data Profiling Report

The interactive dataset report created using the `ydata-profiling` tool allows for dataset exploration. This is a great tool for EDA, as the report highlights the important aspects of the dataset like schema, number of empty cells, and duplicates. Moreover, the report allows for exploration of each column individually. In this case, it was used to detect outliers in the columns for weight and age classes, as well as body-weight and total weight lifted. 

<iframe src="data_profile/unfiltered_report.html" width="100%" height="1200px"></iframe>

### Data cleaning 

Data cleaning steps for this dataset included: 
- Removing whitespaces in cells to standardise formats.
- Duplicates were removed.
- Removing name column and instead assigning a unique index for each lifter. 
- Filtering out the dataset to only include full competition (SBD) and only non-equipped by setting `Event` column to only use `SBD` and the `Equipment` column to only use `Raw`.
- Following that, the `Sex` column has been inspected and the `Mx`records were excluded as the volume (130 records) wasn't sufficient to provide any significant insights.
- The `AgeClass` column was filtered out to only include lifters over 18 years old and then ordered in ascending order. 
- The `WeightClass` column was filtered to only keep IPF official classes for both men and women and then ordered in ascending order. 
- Only the records from 2011 onwards were kept to reduce dataset dimensionality as well as ensure the underrepresented category had a more robust representation (the records for women in earlier years shows less than 15% representation each year).
- Outliers were removed for total weight lifted by using IQR method. 

**Total weight lifted by weight class before and after removing outliers** 

![Screenshot 2026-04-30 142354.png](images/Screenshot%202026-04-30%20142354.png)

![Screenshot 2026-04-30 142408.png](images/Screenshot%202026-04-30%20142408.png)

**Total weight lifted by age class before and after removing outliers** 

![Screenshot 2026-04-30 141657.png](images/Screenshot%202026-04-30%20141657.png)

![Screenshot 2026-04-30 141803.png](images/Screenshot%202026-04-30%20141803.png)

## Data analysis and results 

The analysis showed a significant correlation between body-weight and total weight lifted.

| Group   | Correlation |
|---------|-------------|
| Overall | 67%         |
| Male    | 54%         |
| Female  | 46%         |

Following the correlation check, for both groups minimum, maximum, and average weight lifted were calculated. 

|   | Minimum | Maximum | Average |
|---------|---------|---------|---------|
| Male    | 117.93  | 1010.0 | 562.4 |
| Female  | 95.9    | 743.0 | 315.6 |

Grouping the dataset by weight class and sex, the average body-weight and total weight lifted were calculated in each group. 

The analysis showed that the lifters gender has significant impact on the relative strength. The average ratio for all weight classes was 16.51% for men and 22.35% for women, where the higher the percentage, the lower the relative strength. The analysis also highlights a trend where the higher the lifters body-weight, the lower the relative strength. This trend showed consistent for both men and women. 

To better visualise it, here are scatter and bar plots showing the relationship between the average total weight lifted and average body-weight per weight class split by lifters sex. 

![Screenshot 2026-04-30 140736.png](images/Screenshot%202026-04-30%20140736.png)

![Screenshot 2026-04-30 140749.png](images/Screenshot%202026-04-30%20140749.png)

## Conclusion and recommendations

This project set out to answer if the competitive powerlifters gender impacts their relative strength. The analysis proved the lifters gender has a significant impact on their ability to lift more weight in competition.

A recommendation for further exploration into the topic could focus on looking how the relative strength trends for both sexes but focus on looking at different age classes, specifically looking at differences between pre-pubescent lifters and adults. Hypothetically, relative strength should be more equal and close together for both sexes in the pre-pubescent lifters group.

### References 

- OpenPowerlifting (n.d.) OpenPowerlifting Dataset. Available at: https://www.openpowerlifting.org
- McKinney, W. (2018) Python for Data Analysis. 2nd edn. Sebastopol: O’Reilly Media.
- docs.profiling.ydata.ai. (n.d.). Welcome - YData Profiling. [online] Available at: https://docs.profiling.ydata.ai/latest/.
- Aggarwal, C.C. (2017) Outlier Analysis. 2nd edn. Cham: Springer.
- Helms, E.R., Storey, A.G., Cross, M.R. et al. (2018) ‘RPE and velocity relationships for the back squat, bench press, and deadlift in powerlifters’, Journal of Strength and Conditioning Research, 32(2), pp. 292–297.
- International Powerlifting Federation (IPF) (2023) IPF Technical Rules Book. Available at: https://www.powerlifting.sport.
- Machine Learning Plus. (2023). How to detect outliers using IQR and Boxplots? [online] Available at: https://machinelearningplus.com/machine-learning/how-to-detect-outliers-using-iqr-and-boxplots/.