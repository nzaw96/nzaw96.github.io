## Visualizing COVID-19 In Different US States

**Project Description:** The goal of this project is to visualize the impact of COVID-19 on different US states (and territories) and their corresponding responses. The data for this project comes from Google's <a href="https://health.google.com/covid-19/open-data/raw-data">COVID-19 Open Data</a>. 
<br><br>
The interactive dashboard has been shared to Tableau Public and can be accessed <a href="https://public.tableau.com/app/profile/nay.zaw.aung.win/viz/Covid-19InDifferentUSStates/COVIDDASHBOARD?publish=yes">here</a>.

### 1. Project Motivation: I traveled from NY to NC in mid-2021 and noticed that most people in NC were no longer wearing masks.
In June 2021, I travelled down to Winston-Salem, NC from Troy, NY for a summer internship. Most people who were walking around in the streets of Troy were still wearing masks at the time. I even recalled a few times when I would forget to put a mask on before getting into an Uber in Troy and the Uber driver would remind me to put one on before I get in. However, when I landed in PTI airport in Greensboro, NC (Greensboro was the slightly larger city next to Winston-Salem and has an airport) and got inside an Uber, I started noticing the differences between the two states, in terms of the regulations and peoples' attitude toward them. I was wearing a mask but the Uber driver wasn't. He told me that he wouldn't mind if I didn't either. He asked me where I travelled in from and when I told him "New York", his response was "Oh, so guys are still wearing masks up there, huh? North Carolina just lifted its mask regulation last week". When I finally arrived at my apartment in downtown Winston-Salem, I decided to go down and check out the cafe across the street. There wasn't a single person inside the cafe, who was wearing a mask. Neither was anyone in the street.
<br><br>
So, does a state/territory with stricter COVID-19 regulations handle the impact of COVID-19 better than a state/territory with more relaxed regulations?

### 2. Project Workflow Chart
<img src="images/COVID_USstates_VizProj.png?raw=true"/>

### 3. Plots Created

1. The first plot created is an area graph with five measures on the vertical axis: (Fully) Vaccinated, Tested, Confirmed, Hospitalized and Deceased. On the horizontal axis, we have date. The values of the measures are monthly averaged figures for all of US. 
<br><br>
<img src="images/CovidProj_USOverallFigures.png?raw=true"/>

2. The second plot created is a map graph that shows the aggregates of the same five measures from above for each state (the values of the five measures are only visible when you hover over the interactive graph). The color of a state depends of the number of 'Deceased' in it. The higher the number of deaths in a state, the darker the color is on the graph.
<br><br>
<img src="images/CovidProj_StatesMapGraph.png?raw=true"/>
We can see that California, Texas and Florida are the states with the highest numbers of deaths from COVID.

3. The third plot created is the line graph representing the Case Fatality Rate (CFR) of different states, aggregated at the monthly level, since the beginning of the COVID-19 pandemic. CFR is defined as the number of deaths from COVID divided by the number of diagnosed COVID cases. CFR may not be the ideal metric of measure for how well a state is performing in handling the impact of COVID-19. One of the main reasons is because it's impossible to know the true number of diagnosed cases. So, we have to rely on the number of CONFIRMED cases, which is likely much less than the true number of cases. Read more about CFR in this <a href="https://ourworldindata.org/mortality-risk-covid">article</a>. 
<br><br>
<img src="images/CovidProj_StatesCFR.png?raw=true"/>

4. The final plot created is the line graph representing the Stringency Index score of different states over time, aggregated at the monthly level as well. The Stringency Index score is calculated on the basis of the following 13 metrics: school closures, work closures, cancellation of public events, restrictions on public gatherings, public transport closures, stay-at-home orders, public info campaigns, restrictions on internal movements, international travel restrictions, COVID-testing policy, contact tracing, mask mandate and vaccination policy. A Stringency Index score takes a value between 0 and 100, where 100 is the strictest. Read more about Stringency Index in this <a href="https://ourworldindata.org/covid-stringency-index#:~:text=The%20stringency%20index%20is%20a,100%20(100%20%3D%20strictest).&text=Response%20Tracker).,529%E2%80%93538%20(2021).">article</a>.
<br><br>
<img src="images/CovidProj_StatesStingIndex.png?raw=true"/>
