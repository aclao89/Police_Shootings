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


### Manner of death
![piechart](https://github.com/aclao89/Police_Shootings/blob/master/Images/pie_shot_taser.png)

According to this [policy](https://www.aclu.org/sites/default/files/field_document/30099-30102%20Taser%20policy.pdf), the primary purpose for employing the Taser is to protect human lives and prevent injury to officers and citizens. Since it's less lethal, we can assume that a taser was deployed as a first sign of warning toward the aggressor. Only 5% of cases had a taser deployed then subsequently shot. On the contrary, 95% of cases were just shot.

This calls into question on police tactics and funding. This metric can be used to formulate mandatory tactical self-defense skill as a less-lethal approach to subdue/deescalate situations to reduce deaths.


### Manner of death by race

![shot and tasered](https://github.com/aclao89/Police_Shootings/blob/master/Images/shot_taser.jpg)

No significant difference among the racial groups. Since only 5% were tasered and shot, it seems evenly distributed amongst the groups.

### Weapon by race

![weapons](https://github.com/aclao89/Police_Shootings/blob/master/Images/weapon_by_race.jpg)

Obviously, a gun is a commonly used weapon and also considered an immediate threat to law enforcement. However, unarmed African Americans are shot at
a higher rate than any other race. One might argue that unarmed does not equate to less threat which is true. This call into question regarding police accurately assessing threat levels and tactics to subdue the perp instead of killing.


### Deaths of each race
![death race](https://github.com/aclao89/Police_Shootings/blob/master/Images/race_deaths.png)


- Percent of Whites Killed: 52%
- Percent of Blacks Killed: 26%
- Percent of Asians Killed: 2%
- Percent of Hispanics Killed: 18%
- Percent of Native Americans Killed: 2%

![us_total_demo](https://github.com/aclao89/Police_Shootings/blob/master/Images/us_demo_pop.png)

At first glance, Whites were shot at an astonishing rate of 51%. However, this should be taken with a grain of salt since White Americans comprise two-thirds of the US total population. African Americans, however, account for 26% of those fatally shot and killed by the police despite being just 12% of the U.S. population.

### Poverty of each state
![poverty state](https://github.com/aclao89/Police_Shootings/blob/master/Images/poverty_state.jpg)

Twenty five of the population of Mississippi and Arizona are below the poverty rate.

### Demographic percentage of each state
![demo_state](https://github.com/aclao89/Police_Shootings/blob/master/Images/demographic_state.jpg)

Mississippi has the second highest African American population behind Washington DC. Crime and poverty are often correlated; One way poverty causes crime is the way most people think of it: Some people in desperate need of money commit crimes.


### African Americans killed by the police: Age, frequency, and map

![blackshot](https://github.com/aclao89/Police_Shootings/blob/master/Images/blacks_shot.png)

- California, Texas and Florida has recorded most black people deaths.
- There are more darker side on East side of US too. Perhaps those East Coast States have a higher African American population.
- Annually, the police kill an average of 212 African Americans every year.

- Sadly, there are 109 minors (10-19) who have been victims.
- Montana, Wyoming, and North/South Dakotas were the only states with no reported deaths.
- Most of the victims were between 20-40 years old. It seems younger African Americans are targeted compared to the average age of Caucasians (30-50 years old).

### Caucasians killed by the police: Age, frequency, and map

![white shot](https://github.com/aclao89/Police_Shootings/blob/master/Images/white_shot.png)

- Since White American comprise nearly 66% of the US total population, they have a higher chance of being shot due to the sheer difference in population.
- California, Texas, and Florida have higher rates, possibly due to the size and density of each state.
- Most victims were between 30-50 years old.
