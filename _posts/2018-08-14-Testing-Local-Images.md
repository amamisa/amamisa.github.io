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

To start working on the data we have used pandas to upload the data with parsing the DATE-TIME. Then we decided to create a unique identifier for each turnstile by combining UNIT and SCP.
As we mentioned above we have to calculate total number of traffic In order to do so we subtracted each rows of the cumulative entries and exits. We will then add them together to create the total traffic column.
After we apply all the cleaning part we saved our data in a pickle file to reduce amount of time and to 
read_pickle

### Data Exploration and Analysis


### Conclusion
we come up with clear points after explorations that 
our recomendations to the team is to 

### Future Improvements
to expand data exploration over the whole year to get a more useful insights.
to use other data sets to improve qulity of the descion making
to focus on the exits over the entries

```
---
layout: post
title: Zach's Test Post
---
```

[This is a link](http://thisismetis.com)

![Image test]({{ site.url }}/images/AlanLeeShireGandalf.JPG)

### Other things
* Like
* lists
* and 
* stuff
