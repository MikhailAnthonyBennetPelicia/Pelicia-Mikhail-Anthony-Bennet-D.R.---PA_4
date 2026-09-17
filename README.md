# Pelicia-Mikhail-Anthony-Bennet-D.R.---PA_4
### Name: PELICIA, Mikhail Anthony Bennet D.R.
### Section: 2ECE-C
### Date Submitted: 03/09/2026

## Problem A. Visayas Communication Datarame
#### This problem asks you to create a data frame called "VisComm" with only those whose Hometown is Visayas and whose Track is Communication based on the boards2 Excel file. To do this, I first loaded the Excel file into a data frame called "ece". Then I calculated the average for "Math, Electronics, GEAS, and Communication which will be used or the other dataframes. And to get the information for the specific Track and Hometown, I used ".loc" 
#### Here's the code that was used:
````
#This reads the excel file
ece = pd.read_excel('board2.xlsx')
ece

#This calculates the average and places into its own column
ece['Average'] = ece[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
ece

#This filters and displays the data according to the conditions of those from Visayas and whose track is Communication
VisComm = ece.loc[(ece['Track'] == 'Communication') & (ece['Hometown'] == 'Visayas'), ['Name', 'Gender', 'Math', 'Electronics', 'Average']]
VisComm
````
## Problem B. Visayas Female Dataframe
#### The instructions were to create a data frame titled "VisFemale", which contains the information for Name, Track, GEAS, Electronics, and Average. And whose Hometown is Visayas and Gender is Female. Then display those whose Average is >= to 60. To do this, I used .loc to select the specific columns and then added the specific conditions. 
#### Here's the code that was used:
````
#This filters out those whose Gender is Female and whose Hometwon is Visayas
VisFemale = ece.loc[(ece['Gender'] == 'Female') & (ece['Hometown'] == 'Visayas'), ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
VisFemale

#This displays those whose Average is >= 60
VisFemale[VisFemale['Average'] >= 60]
````
## Category Average Visualization
#### a & b.) The goal is to get the mean of Average for each category and then compare them in a plot. To do this, I used ".groupby" to sort each into their own categories, "as_index=False" to keep them as dateframes, and ".mean" to get the mean
#### c & d.) For this problem, the objective was to create visualizations to display Track, Gender, and Hometown and the Average for each. The visualizations were created using bar charts, which display the average grade for each category within these features. Using groupby() to sort the information according to track, gender, and hometown and .mean() to get the average of the sorted data. And plt.figure to get the size of the figure, plt. title to give the graph a title, plt.ylabel to add a label on the y-axis, .sharey=True to line up their y-axis, axes[] to place them in a row, and .bar to plot it as a bar graph.
#### Here's the code that was used:
````
import matplotlib.pyplot as plt

tm = ece.groupby('Track', as_index=False)['Average'].mean()
gm = ece.groupby('Gender', as_index=False)['Average'].mean()
hm = ece.groupby('Hometown', as_index=False)['Average'].mean()

display(tm)
display(gm)
display(hm)

#This creates a figure with 3 different subplots
fig, axes = plt.subplots(1, 3, figsize=(16, 5), sharey=True)

#Track
axes[0].bar(tm['Track'], tm['Average']) #This takes the average from each Track
axes[0].set_title('Mean Average by Track') #This sets the title
axes[0].set_xlabel('Track') #This sets the label for the x-axis
axes[0].set_ylabel('Mean Average Score') #This sets the label for the y-axis

#Gender
axes[1].bar(gm['Gender'], gm['Average']) #This takes the average from each Gender
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Gender')

#Hometown
axes[2].bar(hm['Hometown'], hm['Average']) #This takes the average from each Hometown
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown')

plt.show()
````
