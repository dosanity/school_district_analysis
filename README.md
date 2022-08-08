# School District Data Mining Analysis

## Project Overview
We are tasked to analyze data on student funding and student standardized test scores. We will be aggregating the data to showcase trends and school performance. In this analysis, we will assist the school board and superintendent in making decisions regarding the school budgets and priorities. Additionally, we are aware of the Family Educational Rights and Privacy Act of 1974 (FERPA) which protects the privacy of student education records. This law applies to all schools that receive funds under an applicable program of the U.S. Department of Education. Therefore, we will be data mining using general education data to predict trends and performances.

We will also address an issue that was brought to light by the school board wherein there is evidence of academic dishonesty. We will also clean the data and disregard grades before conducting the final analysis.

## Resources

+ Data Source 1: [schools_complete.csv](https://github.com/dosanity/school_district_analysis/files/9284310/schools_complete.csv)

+ Data Source 2: [students_complete.csv](https://github.com/dosanity/school_district_analysis/files/9284312/students_complete.csv)

+ Software: Python 3.10, Jupyter Lab 3.4.4

## Results

### Academic Dishonesty

As stated before, we will clean the data and disregard grades due to academic dishonesty. We replaced the ninth graders' math and reading scores from Thomas High School and this can be seen the the updated analysis.

```
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), ["reading_score"]] = np.nan
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), ["math_score"]] = np.nan
```

### School District Summary

In the school district summary, we analyzed general information about all schools in the district:
+ `Total Schools` : Total number of schools.
+ `Total Students` : Total number of students.
+ `Total Budget` : Combined budget of all schools.
+ `Average Math Score` : Overall average math score in the district.
+ `Average Reading Score` : Overall average reading score in the district.
+ `% Passing Math` : Percentage of students that scored 70% or better in math.
+ `% Passing Reading` : Percentage of students that scored 70% or better in reading.
+ `% Overall Passing` : Percentage of students that scored 70% or better in math and reading.

#### Original Summary

| Total Schools | Total Students | Total Budget   | Average Math Score | Average Reading Score | % Passing Math | % Passing Reading | % Overall Passing |
| :-----------: | :------------: | :------------: | :----------------: | :-------------------: | :------------: | :---------------: | :---------------: |
| 15            | 39,170         | $24,649,428.00 | 79.0               | 81.9                  | 75.0           | 85.8              | 65.2              |

#### Updated Summary

| Total Schools | Total Students | Total Budget   | Average Math Score | Average Reading Score | % Passing Math | % Passing Reading | % Overall Passing |
| :-----------: | :------------: | :------------: | :----------------: | :-------------------: | :------------: | :---------------: | :---------------: |
| 15            | 39,170         | $24,649,428.00 | 78.9               | 81.9                  | 74.8           | 85.7              | 64.9              |

As we can see, removing the data for academic dishonesty did not impact the school district summary. This is due to the analysis not focusing on one particular student and is accounting for the overall school district. There were slight changes in the `Average Math Score`, `% Passing Math`, `% Passing Reading`, and `% Overall Passing`. 

### School Summary

Using the same variables as before, we will now look at individual schools. As stated, We calculated the total number of schools, students, and budget. We also looked into the average math and reading scores overall. To calculate the percent of students passing math and reading, we looked at the percentages greater than or equal to 70%.

In the school summary, we analyzed the general information of individual schools. The variables are:

+ `School Type` : Type of school. (District or Charter)
+ `Total Students` : Total number of students of each school.
+ `Total School Budget` : Total budget of each school.
+ `Per Student Budget` : Average budget per student.
+ `Average Math Score` : Average math score of each school.
+ `Average Reading Score` :  Average reading score of each school.
+ `% Passing Math` : Percentage of students that scored 70% or better in math.
+ `% Passing Reading` : Percentage of students that scored 70% or better in reading.
+ `% Overall Passing` : Percentage of students that scored 70% or better in math and reading.

#### Original Summary

![Original](https://user-images.githubusercontent.com/29410712/183508170-0c6a13e1-8d39-43c1-a8c6-70d9c8f55d63.png)

#### Updated Summary

![Refactored](https://user-images.githubusercontent.com/29410712/183508207-7eb49026-2fa0-42c7-9515-652ec580a60b.png)

As we can see, removing the data for academic dishonesty did impact the school summary. Specifically the row for Thomas High School. By including the data for academic dishonesty, we can see that the scores were much higher for the `% Passing Math`, `% Passing Reading`, and `% Overall Passing`. With the data excluded, the passing scores are lower and will reflect a more accurate analysis. 


