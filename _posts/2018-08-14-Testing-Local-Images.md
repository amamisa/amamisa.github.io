---
layout: post
title: MTA NYC Subway Data Analytics
---

In this post we're going to present the data analytics applied on the MTA subway data.

![subway image]({{ site.url }}/images/mta-subway.jpg)

As a first project deliverable of metis, we have been asked for working on the New York City MTA Turnstile data. 
So, for the purpose of this project we have used Pandas, MatplotLib, seaborn and pickle to support the exploratory data analysis process and to come up with a visualization of our results.

### Business Understanding:
WomenTechWomenYes (WTWY) has a street teams that start working on every summer targeting the most contributions to thier annual OMGYN Gala. In order to optimize thier team, they are trying to deploy thier street teams in different NYC subway stations. The street teams will collect email addresses and those who sign up are sent free tickets to the gala.
Our job is to analyze the MTA data set and give recommendations on which subway stations to deploy their street teams for maximum signatures.

### Used Approach
In order to find the appropriate dates for each station to deploy the street team we have to atchive the listed points below:

* First we have to point the stations with the highest traffic records
* Locate the highest traffic subway stations which are closer to the tech companies.
* Find out the most weekdays traffic at the month of May to concentrate their efforts on them.

### Data Acquisition
In this project we used the turnstile data from 2019 for the month of May you can find the data sets from [here](http://web.mta.info/developers/turnstile.html). in the following there are more explainations for all the columns of the data set.

**C/A** – The Control Area is the operator booth in a station.

**UNIT** – The Remote Unit, which is the collection of turnstiles. A station may have more than one Remote Unit.

**SCP** – The Subunit Channel Position represents the turnstile and the number used may repeat across stations.

> The **UNIT** and **SCP** together is a unique identifier of a turnstile.

**DATE** – The date of the recording formatted in (MM/DD/YYYY).

**TIME** – The time for a recording, formatted in: (HH:MM:SS).

**DESC** – The type of event of the reading. The turnstiles submit “Regular” readings every four hours.

**ENTRIES** - Are a cumulative count of turnstile entrances. Note, it continues to increase until it reaches the device limit and then resets to zero.

**EXITS** - The EXITS are a cumulative count of the turnstile exits.

### Pre-processing and Data Cleaning

To start working on the data we have used pandas to upload the data with parsing the DATE-TIME. Then we decided to create a unique identifier for each turnstile by combining UNIT and SCP. Part of the cleaning process as well to droped the unnecessary columns C/A, LINENAME, DIVISION, DESC and to extract the dates which out of our scope.

As we mentioned above we have to calculate the total number of traffic. In order to do so we subtracted each rows of the cumulative entries and exits so we can add them together to create the total traffic column.

One of the important steps in data cleaning, dealing with outliers by calculating thr IQR for the total traffic. 
After we apply all the cleaning part we saved our data in a pickle file to reduce the amount of time in processing the data and to reach it at anytime when it's needed.

### Data Exploration and Visualization

After cleaning the data and creating the “total traffic” column we were able to start analyzing the data. The following figures support us to assist WTWY on where to deploy their street teams.

![top20 image]({{ site.url }}/images/top-20.png)

From the previous bar chart, we can see the top 20 stations with the highest traffic for the month of May in 2019. 

![weekdays image]({{ site.url }}/images/days-per-month.png)

In the above graph we select 34 ST-PENN STA to find out the traffic per weekdays on the month of May 2019.

![map image]({{ site.url }}/images/map.png)

The previous map shows the top stations which are the closest from the tech companies.

### Conclusion

After the exploration part, we come up with clear points that 
we recommend the WTWY’s(WomenTechWomenYes) to deploy their street teams on the following stations on the weekdays, which our analysis shows them the best choices to collect the most signatures. listed bellow:

1. 34 ST-PEEN STA
2. GRD CNTRL-42 ST
3. 23 ST
4. TIMES SQ-42 ST

### Future Improvements

To improve the decision making process, we think its important to work on the bellow steps: 

* Expanding our data scope exploration targeting the month of May over the past 3 years to get a more useful insights.
* Gather demographics data to identify areas with most tech related residents.
* Determine the exact hours of the day where station are crowded the most.
* Concentrates on the exits over the entries. If we assume that people would be more willing to contribute to the gala when they are about to exit the station. On the contrary when people enter the station they tend to hurry up in catching up the metro going to thier work.

