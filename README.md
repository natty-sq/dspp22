# Data Science Project
## Powerlifting: differences between genders looking at total weight lifted in competition relative to lifters body-weight.

Powerlifting is a popular strength based sport where the goal is lifting the highest possible weight in 3 lifts: squat, bench, and deadlift. This project focuses only on full competitions where all 3 lifts are performed. It also only looks at non-equipped groups. 

**Project aims**

This project explores the relationship between gender and relative strength in competitive powerlifting. For this analysis, the lifters body-weight and total weight lifted were used to calculate relative strength.

note: all the weights used are in kilograms (Kg).

**Data source**

The dataset for this analysis was taken from the OpenPowerlifting Data Service. Please note that this dataset gets updated periodically, therefore the results of the analysis could slightly differ if they were run using the most up to date dataset. The set for this analysis was sourced after update on 10/04/26. 

Data sourced from: https://openpowerlifting.gitlab.io/opl-csv/bulk-csv.html

### EDA and data cleaning

For EDA, a ydata-profiling report has been generated. However, before creating the report, the powerlifters names have been anonymised by assigning a unique index to each lifter. This was done to follow data protection as well as remove bias on the analysis.

# Data Profiling Report

<div style="height:1200px">
    <iframe src="unfiltered_report.html](images/unfiltered_report.html"
            style="width:100%; height:100%; border:none;">
    </iframe>
</div>

