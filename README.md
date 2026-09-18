Mental Health Data Preprocessing and EDA

Group ID: MLB-WEB3G1-05

1. Project Overview and Dataset Details

This project covers data cleaning, preprocessing, and Exploratory Data Analysis (EDA) for Progress Review I. Six members develop individual preprocessing notebooks and integrate their contributions into a combined pipeline.

Dataset: depression_data.csv

Original records: 413,768

Original columns: 16

Dataset location: data/raw/depression_data.csv

Original dataset source: To be added by the group.

Target variable: To be confirmed by the group. Current example code uses History of Mental Illness.

Columns: Name, Age, Marital Status, Education Level, Number of Children, Smoking Status, Physical Activity Level, Employment Status, Income, Alcohol Consumption, Dietary Habits, Sleep Patterns, History of Mental Illness, History of Substance Abuse, Family History of Depression, and Chronic Medical Conditions.

The dataset has no column named Depression. History of Mental Illness describes mental-illness history and must not be interpreted as a depression diagnosis.

2. Group Members and Responsibilities

Member

IT Number

Name

Responsibility

Assigned EDA Visualization

1

IT25104081

Rukshan R A P

Handling missing data

Age histogram

2

IT25104091

Premathilaka I D T P

Duplicate detection and removal

Income histogram

3

IT25104082

Muneer M M

Encoding categorical variables

Smoking-status count plot

4

IT25104115

Muhadh M R

Outlier detection and justified treatment

Income boxplots

5

IT25104094

Dissanayake K M N D

Normalization / scaling

Correlation heatmap

6

IT25104084

Rameen M R M

Feature selection: remove Name and separate features from target

Target-variable distribution

Each member must explain their technique, justify its use, show code and output, and interpret at least one EDA visualization.

3. Repository Structure

The following paths follow the group's chosen layout. Use these notebook names when organizing the final files.

Path relative to MLB-WEB3G1-05/

Contents

README.md

Project overview and run instructions

data/raw/depression_data.csv

Original dataset

data/external/

External datasets, if used

notebooks/IT25104081_Member1_Missing_Data.ipynb

Rukshan's notebook

notebooks/IT25104091_Member2_Duplicate_Removal.ipynb

Premathilaka's notebook

notebooks/IT25104082_Member3_Categorical_Encoding.ipynb

Muneer's notebook

notebooks/IT25104115_Member4_Outlier_Handling.ipynb

Muhadh's notebook

notebooks/IT25104094_Member5_Feature_Scaling.ipynb

Dissanayake's notebook

notebooks/IT25104084_Member6_Feature_Selection.ipynb

Rameen's notebook

notebooks/group_pipeline.ipynb

Combined preprocessing pipeline

results/eda_visualizations/

PNG/JPEG visualizations, including age_histogram.png and age_boxplot.png if generated

results/logs/

Optional execution logs

results/outputs/depression_data_processed.csv

Intended final combined output

.gitignore

Git exclusion rules

Submission note: The supplied review PDF lists group_pipeline.ipynb at the group-folder root. This README follows the group's requested notebooks/ location. For the final ZIP, place the pipeline at the root as specified by the PDF and adjust its paths accordingly.

4. Required Libraries

Use Python 3 with pandas, numpy, matplotlib, seaborn, scikit-learn, and Jupyter. pathlib is included with Python.

python -m pip install pandas numpy matplotlib seaborn scikit-learn jupyter

5. How to Run the Notebooks

Download or clone the repository and open the MLB-WEB3G1-05 folder.

Install the required libraries using the command above.

Place the unchanged CSV in data/raw/depression_data.csv.

Start Jupyter from the group folder:

jupyter notebook

Open notebooks/group_pipeline.ipynb for the combined workflow, or an individual notebook for a member's contribution.

Restart the kernel and run all cells from top to bottom. Resolve any error before continuing.

Check results/eda_visualizations/ for charts and results/outputs/ for exported data.

Use the following setup in notebooks instead of personal Windows drive paths. It supports execution from the project root or its notebooks folder:

from pathlib import Path
import pandas as pd

project_folder = Path.cwd()
if project_folder.name == "notebooks":
    project_folder = project_folder.parent

data_path = project_folder / "data" / "raw" / "depression_data.csv"
plot_folder = project_folder / "results" / "eda_visualizations"
output_folder = project_folder / "results" / "outputs"

plot_folder.mkdir(parents=True, exist_ok=True)
output_folder.mkdir(parents=True, exist_ok=True)

df = pd.read_csv(data_path)

6. Combined Pipeline Order

Step

Stage

Responsibility

1

Import libraries and load the original CSV once

Shared

2

Inspect columns, data types, and shape; confirm target

Shared

3

Detect and remove verified duplicate records

Member 2

4

Handle missing input values

Member 1

5

Investigate income outliers and apply justified treatment

Member 4

6

Remove Name; separate input features X and target y

Member 6

7

Encode categorical input features

Member 3

8

Scale appropriate numerical input features

Member 5

9

Save processed data and charts

Shared

Each stage must use the previous stage's output. Do not reload raw data between processing stages. Remove Name before encoding and exclude the target from input-feature scaling. Preserve alignment between feature rows and target values.

Create categorical charts before encoding where needed, and income boxplots before and after treatment. IQR identifies unusual values; removal requires justification.

This review focuses on preprocessing and EDA. For later model evaluation, split the data before fitting data-dependent preprocessing and learn its settings from training data only.

7. Output-File Locations

Location

Output

results/eda_visualizations/

Each member's saved PNG/JPEG charts

results/outputs/depression_data_processed.csv

Final integrated dataset; configure the pipeline to save this filename

results/outputs/feature_selected_data.csv

Feature-selection stage output

results/outputs/selected_features.csv

Selected input-feature names

results/outputs/target_distribution.csv

Target category counts and percentages

results/eda_visualizations/target_distribution.png

Target-distribution chart

results/logs/

Execution logs, if generated

The feature-selection output is an intermediate output and is not necessarily fully encoded or scaled. Output files are generated by the notebooks; verify that saved filenames match this README.
