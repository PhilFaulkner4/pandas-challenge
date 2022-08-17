# pandas-challenge

![Money-Crayons.jpg](attachment:Money-Crayons.jpg)

## Py School Conclusions

Money Spent Versus Overall Passing Rate
While the logical conclusion might be that the more funds spent for the education of a student would result in a higher passing percentage rate.  However, the scores for Spending per student analysis proves this to be a false conclusion.  This analysis shows that money is not necessarily an indication of the overall passing rate percentage.  The highest overall passing percentage rate occured with the schools who spent the lessor amounts of money per student with an average spend amount of less tha $621 (Cell 41) per student versus the other schools spending greater $619 per student.

Charter versus Public Distric Schools Overall Passing Rate
In the analysis comparing the Charter versus District schools overall passing rate, the charter school has a significatly higher rate at 95 percent versus the district schools 74 percent (Cell 43). Although the teacher to student ratio is not available for this analysis and could add more context to this analysis.

# Dependencies and Setup
import pandas as pd
import numpy as np

# File to Load (Remember to Change These)
school_data_to_load = "Resources/schools_complete.csv"
student_data_to_load = "Resources/students_complete.csv"

# Read School and Student Data File and store into Pandas Data Frames
school_data = pd.read_csv(school_data_to_load)
student_data = pd.read_csv(student_data_to_load)

# Combine the data into a single dataset
school_data_complete = pd.merge(student_data, school_data, how="left", on=["school_name", "school_name"])
School Summary
District Summary
Calculate the total number of schools

Calculate the total number of students

Calculate the total budget

Calculate the average math score

Calculate the average reading score

Calculate the percentage of students with a passing math score (70 or greater)

Calculate the percentage of students with a passing reading score (70 or greater)

Calculate the percentage of students who passed math and reading (% Overall Passing)

Create a dataframe to hold the above results

Optional: give the displayed data cleaner formatting

Total_Students = len(school_data_complete)

Budget_List = school_data_complete.groupby("school_name").mean()
Total_Budget = Budget_List["budget"].sum()
Total_Budget = '${:,.2f}'.format(Total_Budget)

Avg_Math = school_data_complete["math_score"].mean()

Avg_Read = school_data_complete["reading_score"].mean()

Overall_Passing = (Avg_Math + Avg_Read)/2

Passing_Math = school_data_complete.loc[school_data_complete["math_score"] >=70,:]
MathPct = Passing_Math["math_score"].count() / Total_Students * 100
MathPct

Passing_Read = school_data_complete.loc[school_data_complete["reading_score"] >=70,:]
ReadPct = Passing_Read["reading_score"].count() / Total_Students * 100
ReadPct

Total_Students = '{:,.0f}'.format(Total_Students)

Summary0DF = pd.DataFrame({"Total Schools" : [Total_Schools,1], "Total Students" : [Total_Students,1],
                         "Total Budget": [Total_Budget, 1],
                           "Average Math Score" : [Avg_Math,1], "Average Reading Score" : [Avg_Read,1],
                          "% Passing Math" : [MathPct,1], "% Passing Reading" : [ReadPct,1], 
                          "% Overall Passing Rate" : [Overall_Passing,1]})

SummaryDF = Summary0DF.drop([1])

SummaryDF

Total Schools	Total Students	Total Budget	Average Math Score	Average Reading Score	% Passing Math	% Passing Reading	% Overall Passing Rate
0	15	39,170	$24,649,428.00	78.985371	81.87784	74.980853	85.805463	80.431606
