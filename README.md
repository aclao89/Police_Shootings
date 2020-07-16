# To shoot or not to shoot?: An Exploratory Data Analysis into trends of police shootings from 2015-2020.

![cover pic](https://github.com/aclao89/Police_Shootings/blob/master/Images/readme_cover.jpg)
## ABSTRACT

In 2015, The Washington Post began tracking more than a dozen details about each killing — including the race of the deceased, the circumstances of the shooting, whether the person was armed and whether the victim was experiencing a mental-health crisis — by pulling local news reports, law enforcement websites and social media and by monitoring independent databases such as [Killed by Police](https://killedbypolice.net/) and [Fatal Encounters](https://fatalencounters.org/).

The Post is documenting only those shootings in which a police officer, in the line of duty, shot and killed a civilian — the circumstances that most closely parallel the 2014 killing of Michael Brown in Ferguson, Missouri, which began the protest movement culminating in Black Lives Matter and an increased focus on police accountability nationwide. The Post is not tracking deaths of people in police custody, fatal shootings by off-duty officers or non-shooting deaths.

The FBI and the Centers for Disease Control and Prevention log fatal shootings by police, but officials acknowledge that their data is incomplete. In 2015, The Post documented more than two times more fatal shootings by police than had been recorded by the FBI.

According the Las Vegas Review-Journal: Deadly Force, "The nation’s leading law enforcement agency [FBI] collects vast amounts of information on crime nationwide, but missing from this clearinghouse are statistics on where, how often, and under what circumstances police use deadly force. In fact, no one anywhere comprehensively tracks the most significant act police can do in the line of duty: take a life."


In hopes to be more informed on this matter, I would like to investigate:

1. Due to the current climate around Black Lives Matter, are African-Americans shot a higher rate?
2. What are the type of weapons in possession of the victim? Does it differ among racial groups?
3. What are the differences, if any, in age group among the racial groups?
4. Identify any trends in shooting on a monthly and yearly basis.
5. Due to the rise in police brutality claims and proven videos, have police departments increased body camera footage to ensure accountability on tactics?


## METHODS

### Datasets

1. [Police Killing](https://www.washingtonpost.com/graphics/investigations/police-shootings-database/) - a database maintained by the Washington Post

2. [State Demographic Population](https://www.census.gov/data/datasets/time-series/demo/popest/2010s-state-total.html) - US Census data regarding racial demographic on US total population

3. [Race Population by City](https://www.kaggle.com/kwullum/fatal-police-shootings-in-the-us) - US Census data regarding racial demographic in all US cities

4. [Below Poverty Level](https://www.kaggle.com/kwullum/fatal-police-shootings-in-the-us) - US Census data regarding percentage of people under the poverty level

### Libraries Used

1. Plotly - Python graphic library for interactive charts and maps

2. Matplotlib - A comprehensive library for creating static, animated, and interactive visualizations in Python

3. Folium -  Python library that helps you create several types of Leaflet maps

4. Pandas - An open source data analysis and manipulation tool, built on top of the Python programming language


## Data Cleaning

Rows: 5416
Columns: 13

df.info()

Data columns (total 13 columns):
name                       5416 non-null object
date                       5416 non-null object
manner_of_death            5416 non-null object
armed                      5189 non-null object
age                        5181 non-null float64
gender                     5414 non-null object
race                       4895 non-null object
city                       5416 non-null object
state                      5416 non-null object
signs_of_mental_illness    5416 non-null bool
threat_level               5416 non-null object
flee                       5167 non-null object
body_camera                5416 non-null bool
dtypes: bool(2), float64(1), object(10)

Given the current climate on police brutality, it's concerning that race has the most null values. This further compounds the fact law enforcement agencies are purposely hiding race to deflate actual data trends. Since each column with null values is less than 10% then we can continue with dropping those rows since it wont significantly impact the analysis.

![missing matrix](https://github.com/aclao89/Police_Shootings/blob/master/Images/missinginfo.jpg)

After dropping all rows with NaN values:

Rows: 4399

## Data Analysis

### Yearly victims in police shootings
![year deaths](https://github.com/aclao89/Police_Shootings/blob/master/Images/yearly_count.png)

This graph shows that the rate of killing per year has never looked down except 2016.
It has an average of 983 per year. Almost 1000 people are killed every year.
We are in mid of 2020 and we have already reached 432 death counts as of now. Will this year also be the same story as before?


### Cumulative deaths per month from 2015 to 2020.
![monthly deaths](https://github.com/aclao89/Police_Shootings/blob/master/Images/deaths_per_month.jpg)

January, February and March have recorded most cases, averaging well over 400 per month. That is approximately 13 deaths every day! :(


### Calendar Heat Map to see the distribution of shootings over the span from 2015 to 2020.
![calendar map](https://github.com/aclao89/Police_Shootings/blob/master/Images/calheatmap.jpg)


### Manner of Death
![piechart](https://github.com/aclao89/Police_Shootings/blob/master/Images/pie_shot_taser.png)

According to this [policy](https://www.aclu.org/sites/default/files/field_document/30099-30102%20Taser%20policy.pdf), the primary purpose for employing the Taser is to protect human lives and prevent injury to officers and citizens. Since it's less lethal, we can assume that a taser was deployed as a first sign of warning toward the aggressor. Only 5% of cases had a taser deployed then subsequently shot. On the contrary, 95% of cases were just shot.

This calls into question on police tactics and funding. This metric can be used to formulate mandatory tactical self-defense skill as a less-lethal approach to subdue/deescalate situations to reduce deaths. 
