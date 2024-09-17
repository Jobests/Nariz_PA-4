# Nariz_PA-4
Data Wrangling and Data Visualization

### Instructions
Download the ECE Board Exam 2 dataset found on this link: bit.ly/ECEBoardExamDataset and write a
Python script/code in the Jupyter Notebook to do the given problems

## 1. ECE BOARD EXAM PROBLEM
Using data wrangling and data visualization technique with
storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

### CODE
```python
import pandas as pd #Import Pandas library
ece_board = pd.read_excel('board2.xlsx') #Read the file
```
```python
instru = ece_board[(ece_board['Track'] == 'Instrumentation') & #filters track to only instrumentation
                    (ece_board['Hometown'] == 'Luzon') & #filters hometown to only Luzon
                    (ece_board['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']] #Filters Electronics with scores greater than 70 and outputs the variables

print(instru) #print Dataframe
```
### OUTPUT
```output
Name  GEAS  Electronics
0    S1    75           89
7    S8    64           81
29  S30    57           81
```

### CODE
```python
ece_board['Average'] = ece_board[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) #determining the average of scores; grabs the values across all columns and averages it

mindy = ece_board[(ece_board['Gender'] == 'Female') & #filters hometown to only Mindanao
                    (ece_board['Hometown'] == 'Mindanao') & #filters gender to only female
                    (ece_board['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']] #Filters out averages less than 55 and outputs the variables

print(mindy) #print dataframe
```
### OUTPUT
```output
Name             Track  Electronics  Average
1    S2     Communication           75    67.25
2    S3   Instrumentation           74    72.75
14  S15  Microelectronics           41    59.00
16  S17  Microelectronics           79    70.50
19  S20     Communication           60    66.50
```
## 2. VISUALIZAITON PROBLEM
Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

### CODE
```python
#Create a visualization that shows how the different features contributes to average grade. 
#Visualization for 
import matplotlib.pyplot as plt #allows access to plot graphs
import seaborn as sns #allows access for creative statistical graphics

sns.boxplot(x ='Track', y ='Average', hue ='Gender', data = ece_board) ##Creates a boxplot that correlates Gender and Track to the average grade 
plt.title('Correlation between Gender and Track to their Average Grades') #display title
plt.show() #displays the boxplot 
```
### OUTPUT
![image](https://github.com/user-attachments/assets/72d6dd28-693b-44fe-b35f-de7f178403ff)

### CODE
```python
sns.boxplot(x='Hometown', y='Average', hue='Hometown', data=ece_board) #Creates a boxplot that correlates hometown and average
plt.title('Correlation between Hometown and Average Grades') #displays title 
plt.show() #displays the boxplot
```
### OUTPUT

![image](https://github.com/user-attachments/assets/302f96e8-d356-4008-b07f-756bc95291bb)

### Library used
* Pandas
* Matplotlib.pyplot
* Seaborn

### Author
Joshua Nariz
