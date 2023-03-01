# Exploratory Data Analysis  
# About Dataset
This dataset contains information on car accidents that occurred in the contiguous United States from February 2016 to December 2021. The data was collected from multiple APIs that provide streaming traffic incident data from a variety of sources, including transportation departments, law enforcement agencies, traffic cameras, and traffic sensors.

Currently, the dataset includes approximately *2.8 million accident records*. This dataset can be used for a wide range of applications, including real-time accident prediction, studying accident hotspots, casualty analysis, and extracting cause-and-effect rules to predict car accidents. The most recent release of the dataset can also be used to study the impact of COVID-19 on traffic behavior and accidents.

```
# Identify the hours with the highest number of accidents
hourly_accidents = df.groupby(df['Start_Time'].dt.hour).size()

highest_hours = hourly_accidents.loc[hourly_accidents == hourly_accidents.max()].index

# Create a barplot of the number of accidents by hour using seaborn
sns.set_style("whitegrid")
plt.figure(figsize=(10, 6))
sns.barplot(x=hourly_accidents.index, y=hourly_accidents.values, palette = "PuBuGn")
plt.xlabel('Hour of the Day')
plt.ylabel('Number of Accidents')
plt.title('Number of Accidents by Hour')

# Highlight the hours with the highest number of accidents using red color
for i in highest_hours:
    plt.axvline(x = i, color='red', linestyle='--')
    
# Add label arrows pointing at the hours of maximum danger
for j in highest_hours:
    plt.annotate('peaking hour', xy=(j, hourly_accidents[j]), xytext=(j+2, hourly_accidents[j]+80), 
                 arrowprops=dict(facecolor='black', shrink=0.35))
    
plt.annotate('workday start',xy=(6,0),xytext=(3,25000),arrowprops= dict(facecolor='black', shrink=0.25), fontsize=11)
plt.annotate('workday end',xy=(16,0),xytext=(18,25000),arrowprops=dict(facecolor='black', shrink=0.25), fontsize=11)


plt.show() ```

![alt text]([https://github.com/[username]/[reponame]/blob/[branch]/image.jpg?raw=true](https://github.com/yasmina-99/Exploratory_data_analysis/blob/branch/number_accidents.png))

# Acknowledgements

Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, and Rajiv Ramnath. “A Countrywide Traffic Accident Dataset.”, 2019.
Moosavi, Sobhan, Mohammad Hossein Samavatian, Srinivasan Parthasarathy, Radu Teodorescu, and Rajiv Ramnath. "Accident Risk Prediction based on Heterogeneous Sparse Data: New Dataset and Insights." In proceedings of the 27th ACM SIGSPATIAL International Conference on Advances in Geographic Information Systems, ACM, 2019.


