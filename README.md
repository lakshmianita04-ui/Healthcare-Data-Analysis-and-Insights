# Healthcare-Data-Analysis-and-Insights
Answers  

Data Cleaning:
Check for the number of missing values marked with '?' in each column of the “Medical Examinations” Table and "Hospitalization Details" Table.
By using the filter option, check and calculate the total = 16 or =countif(range, criteria))
=COUNTIF(A:I,"?")=14
=COUNTIF(A:H,"?")=2

Fill in the missing values of ‘month’ with Sep and ‘year’ with its average rounded to the nearest integer.
The missing values of ‘month’ with Sep are replaced with the value  by  Power Query. The missing value for ‘year’ is 1983, found by taking the median calculated, replaced by Power Query.


Determine the most frequently occurring values in the ‘smoker’, 'Hospital tier' and 'City tier' columns, and fill in the missing values accordingly.
The most frequently occurring values in the’ smoker ’-No, 'Hospital tier'-Tier 2, and 'City tier'-Tier 2 columns. This can be found using the filter option. The filtered options are present and can be seen in the corner. number of cells containing this is the most frequently occurring value. Fill in the missing values with the most frequently occurring values.

If any 'State ID' values are missing, consider filling them with 'Unknown' or using another appropriate strategy.
By Power Query, fill in the missing values with Unknown.


Split the ‘names’ column in the “Customer Names” Table into 3 meaningful columns: ‘Title’, ‘First Name’, and ‘Last Name’.
Split the ‘names’ in the  Power Query. By using delimiters ", "and".".


Convert the "NumberOfMajorSurgeries" column in the “Medical Examinations” Table to numerical data by replacing non-numeric characters with meaningful numerical values.
Convert the "NumberOfMajorSurgeries" column  to numerical data by replacing with 0.

Check for inconsistencies in the 'Heart Issues' and 'smoker' columns and propose corrective actions if necessary.
Capitalise each word in the inconsistencies. Go to Format and select Capitalise each word.




Create a new column named “Weight Status” that categorizes BMI into different categories as below:

IFS([@BMI]>=30,"Obesity", [@BMI]>=25,"Overweight",[@BMI]>=18.5,"Normal Weight",[@BMI]<18.5,"Underweight") By using this formula, categorize BMI into different categories.

Create a new column named “Diabetes Status” and fill it as per the information given below:
=IFS([@HBA1C]>=6.5,"Diabetes", [@HBA1C]>=5.7,"Prediabetes",[@HBA1C]<5.7,"Normal")By using this formula, categorize HBA1C into different categories.



Merge ‘year’, ‘month’ and ‘date’ columns in the “Hospitalization Details” Table into one column named ‘Date of Birth’ and format it in ‘DD-MMM-YYYY’ custom format.
=CONCATENATE([@date]," ", [@month]," ", [@year])By using this formula,Merge ‘year’, ‘month’ and ‘date’ columns in the “Hospitalization Details” Table into one column named ‘Date of Birth’.=CONCATENATE(text1,[text2]  )


Calculate the ‘Age’ of each customer based on their ‘Date of Birth’ and the date of collection of the dataset, which is 8thJune 2023.
Create a column and use datedif =DATEDIF([@[Date of Birth]],[@[Date of the dataset ]],"Y")& " Years "&DATEDIF([@[Date of Birth]],[@[Date of the dataset ]],"YM")& " Months "&DATEDIF([@[Date of Birth]],[@[Date of the dataset ]],"MD")& " Days " 

Format ‘charges’ column as currency ($).
On the number side, there is an option to change the format to currency

Data Exploration, Analysis & Visualization:
Create a new sheet named “Healthcare", combine all three tables into one, usingCustomer ID as the common column, utilizing VLOOKUP.
➢ Retain the following necessary columns: Customer ID, First Name, BMI, HBA1C, HeartIssues, Any Transplants, Cancer history, NumberOfMajorSurgeries, smoker, Weight
Status, Diabetes Status, Date of Birth, charges, Hospital tier, City tier, State ID, Age.


Created a new sheet named “Healthcare" with Customer ID as the common column
=VLOOKUP('Health care'!A2,'Hospitalisation Details (2)'!A:L,2,FALSE), and the column number has to be changed 
=VLOOKUP('Health care'!A3,'Hospitalisation Details (2)'!A:L,2,FALSE), and the column number has to be changed 
=VLOOKUP([@[Customer ID]],'Customer Names (2)'!A:D,2,FALSE)           = VLOOKUP(lookup_value,table_array,col_number,False)

Analysis using Pie/Donut Chart:
➢ What is the distribution of cancer history among smokers and non-smokers?
➢ How does the total number of major surgeries and average HbA1C differ between
patients with and without a history of transplants?
Row Labels	Count of Customer ID
No	1944
No	1538
Unknown	2
yes	404
Yes	391
No	307
yes	84
#N/A	8
#N/A	8
Grand Total	2343


Row Labels	Sum of NumberOfMajorSurgeries	Average of HBA1C
No	1417	6.670077626
Unknown	0	7.47
yes	162	5.187638889
#N/A	#N/A	#N/A
Grand Total	#N/A	#N/A


Analysis using Column/Bar Chart:
➢ How do healthcare charges vary based on different weight statuses and diabetes
statuses?
➢ Can you compare the average charges for each hospital tier within different states?
Row Labels	Sum of charges
Normal Weight	4305290.14
Diabetes	1730218.19
Normal	1714717.24
Prediabetes	860354.71
Obesity	20343646.82
Diabetes	8184059.06
Normal	8520712.93
Prediabetes	3638874.83
Overweight	5729141.77
Diabetes	2240235.2
Normal	2437209.03
Prediabetes	1051697.54
Underweight	1214279.88
Diabetes	483792.72
Normal	566702.46
Prediabetes	163784.7
#N/A	62109.32
#N/A	62109.32
Grand Total	31654467.93

R1011	11152049.7
tier - 1	4456975.76
tier - 2	5488841.18
tier - 3	1206232.76
R1012	7010595.38
tier - 1	1669754.22
tier - 2	3533293.29
tier - 3	1807547.87
R1013	6305061.57
tier - 1	1659071.43
tier - 2	3467453.78
tier - 3	1177836.36
Unknown	700
R1014	184608.47
tier - 1	77093.84
tier - 2	82200.7
tier - 3	25313.93
R1015	199931.11
tier - 1	116831.42
tier - 2	35338.13
tier - 3	47761.56
R1016	858261.47
tier - 1	202558.38
tier - 2	452994.39
tier - 3	202708.7
R1017	554453
tier - 1	241992.79
tier - 2	205317.66
tier - 3	107142.55
R1018	124210.67
tier - 1	34617.84
tier - 2	63352.46
tier - 3	26240.37
R1019	372299.41
tier - 1	67236.06
tier - 2	174201.05
tier - 3	130862.3
R1020	56885.82
tier - 2	12531
tier - 3	44354.82
R1021	642801.02
tier - 1	5028.15
tier - 2	283918.95
tier - 3	353853.92
R1022	153487.95
tier - 2	78868.36
tier - 3	74619.59
R1023	543583.79
tier - 1	130331.49
tier - 2	296206.64
tier - 3	117045.66
R1024	2001476.34
tier - 1	383642.12
tier - 2	1086336.42
tier - 3	531497.8
R1025	361087.67
tier - 2	99732.5
tier - 3	261355.17
R1026	1084478.84
tier - 1	148446.04
tier - 2	491916.52
tier - 3	444116.28
Unknown	43510.67
tier - 2	43510.67
(blank)	
(blank)	
Grand Total	31648782.88

Analysis using Line/Scatter Plot:
➢ Is there any correlation between age and both BMI and HbA1C in the dataset?
➢ Explore the relationship between age and healthcare charges.

Images are attached.
There is an increase in charges  on the age  32,30,45 and 54.




