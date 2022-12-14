# School District Analysis

## Project Overview
We are tasked to analyze data on student funding and student standardized test scores. We will be aggregating the data to showcase trends and school performance. In this analysis, we will assist the school board and superintendent in making decisions regarding the school budgets and priorities. Additionally, we are aware of the Family Educational Rights and Privacy Act of 1974 (FERPA) which protects the privacy of student education records. This law applies to all schools that receive funds under an applicable program of the U.S. Department of Education. Therefore, we will be data mining using general education data to predict trends and performances.

We will also address an issue that was brought to light by the school board wherein there is evidence of academic dishonesty. We will also clean the data and disregard grades before conducting the final analysis.

## Resources

+ Data Source 1: [schools_complete.csv](https://github.com/dosanity/school_district_analysis/files/9284310/schools_complete.csv)

+ Data Source 2: [students_complete.csv](https://github.com/dosanity/school_district_analysis/files/9284312/students_complete.csv)

+ Software: Python 3.10, Jupyter Lab 3.4.4

## Results

### Academic Dishonesty

As stated before, we will clean the data and disregard grades due to academic dishonesty. We replaced the ninth graders' math and reading scores from Thomas High School and this can be seen the updated analysis.

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

As we can see, removing the data for academic dishonesty did not impact the school district summary. This is due to the analysis not focusing on one student and accounting for the overall school district. There were slight changes in the `Average Math Score`, `% Passing Math`, `% Passing Reading`, and `% Overall Passing`. 

### School Summary

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

![Original Summary](https://user-images.githubusercontent.com/29410712/183518466-084d8969-e646-4f92-b151-d64ed1269968.png)

#### Updated Summary

![Updated Summary](https://user-images.githubusercontent.com/29410712/183518485-15044c5e-e320-4b15-ac9f-93e2229ad123.png)


As we can see, replacing the data for academic dishonesty with `NaN` did impact the school summary. Specifically the row for Thomas High School. By including the data for academic dishonesty, we can see that the scores were much higher for the `% Passing Math`, `% Passing Reading`, and `% Overall Passing`. With the data excluded, the passing scores are lower. 

### Top 5 Schools

#### Original Top Schools

![Original Top](https://user-images.githubusercontent.com/29410712/183519322-0fa402aa-1ab3-4901-b3fe-b14dbefb14bf.png)

#### Updated Top Schools

![Updated Top](https://user-images.githubusercontent.com/29410712/183519340-8b6edfa1-f0a7-4c28-bdfd-f18f6aeac22b.png)

As we can see, Thomas High School was in the top 5 schools before replacing the data for academic dishonesty. The updated version clearly shows that Thomas High School's performance relative to the other schools was significantly impacted.

### Math & Reading Scores by Grade

To get a more accurate result, we will be analyzing the 10th - 12th grade for Thomas High School. 

<img width="1009" alt="Thomas-other" src="https://user-images.githubusercontent.com/29410712/183526040-e4b6f374-4763-4f8e-8916-e54e0db30276.png">

#### Original Math Scores

<img src="https://user-images.githubusercontent.com/29410712/183521490-d43658c3-ab1c-4010-b3cc-3510632f9649.png"  width=50% height=50%>

#### Updated Math Scores

<img src="https://user-images.githubusercontent.com/29410712/183521561-41c31f49-3687-4a89-892a-10162e863233.png"  width=50% height=50%>

#### Original Reading Scores

<img src="https://user-images.githubusercontent.com/29410712/183521503-becff801-cbf4-4fa1-aa8f-b699d0af9e16.png"  width=50% height=50%>

#### Updated Reading Scores

<img src="https://user-images.githubusercontent.com/29410712/183521597-385950ee-e19b-47a6-96ff-0cd6dd6a496c.png"  width=50% height=50%>

Replacing the scores affects the math and reading scores by grade. The data simply becomes `nan` or null. All other data is left untouched for the other schools. Only Thomas High School is affected in the data that shows scores by grade.

### Scores by School Spending

![Scores Spending](https://user-images.githubusercontent.com/29410712/183523367-3907a5d2-dd63-45d4-b0d2-87b420b2baf3.png)

#### Spending Summary

![Spending Summary](https://user-images.githubusercontent.com/29410712/183523492-29795ba2-ca7d-4f58-9efe-70f555e3109f.png)

Since we only replaced math and reading scores, school spending remains the same. Thomas High School???s spending range is still between $630 - $644.

### Scores by School Size

![Size](https://user-images.githubusercontent.com/29410712/183523608-c7353e1c-968e-42de-9dc3-cc83a7f84453.png)

#### School Size Summary

![Size Summary](https://user-images.githubusercontent.com/29410712/183523692-bd7db97f-d6d8-465b-aa79-185da3c03688.png)

Again, since we only replaced math and reading scores, school size also remains the same. Thomas High School???s size remains in the Medium Range (1000 - 2000).

### Scores by School Type

![School Type](https://user-images.githubusercontent.com/29410712/183523802-6c07d007-2382-4a8d-b1eb-24961736a18c.png)

Finally, we analyzed the scores for school type. There was no impact on these scores since we are only including 10th - 12th grade for our analysis. If we left the 9th grade in, it would take into account those scores and would lower the averages. 

## Summary

Based on these results, there are many changes to the school district analysis after we addressed the issue that was brought to light by the school board wherein there is evidence of academic dishonesty. Some major changes are:

+ Replacing the 9th grade values brought average scores lower for Thomas High School due to the inclusion of `NaN` values in the data set. By looking at just the 10th - 12th grade data, the averages were higher.
+ By removing the 9th grade data, Thomas High School was a high-performing school once more. 
+ The `% Passing Math` increased from 66.9% to 93% by only analyzing 10th - 12th grade data.
+ The `% Passing Reading` increased from 69.6% to 97% by only analyzing 10th - 12th grade data.
+ The `% Overall Passing` increased from 65% to 90% by only analyzing 10th - 12th grade data.


