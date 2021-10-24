---
layout: post
title: "Report outlining the venues and costs of living in Austin, Tx."
subtitle: "This report outlines the capstone project for the IBM Data Science Professional Certificate"
date: 2020-01-31 10:45:13 -0400
background: '/img/posts/06.jpg'
---

## A. Introduction

* * *

## A.1 Background on this project

This peer-reviewed capstone report and presentation/blog post is the final report for the [IBM Data Science Professional Certification](https://www.ibm.com/blogs/ibm-training/data-science-ibm-coursera/). This course is a nine-part course that covers the fundamentals of data science, open-source tools for data science, data science methodology, Python for data science and AI, databases, and SQL for data science, data analysis with Python, data visualization with Python, and machine learning with Python. All of these courses have been completed using the Jupyter Labs notebook in [IBM's Cognitive Class Laboratories](https://labs.cognitiveclass.ai/) and are stored on GitHub. This report was typed using Markdown formatting.

The link to the GitHub repository for this study can be [found here](https://github.com/jeff-mos-def/Coursera_Capstone/tree/master/Applied%20Data%20Science%20Capstone/BoTN%20Final).

## A.2 Topic Selection Data Description

Austin, Tx is the technology centerpiece of the State of Texas. Nested north of San Antonio, Tx, and south of Dallas/Fort Worth, Tx Austin serves as the capital of the state with a population of [790,390 and a population density of 3,182/sq mi](https://en.wikipedia.org/wiki/Austin,_Texas). The city has seen growth within the last decade due to large technology and software companies coming into the Central Texas Region. From 2007 - 2017 alone, the percentage population growth of the City of [Austin rivaled that of the State of Texas and the United States](https://www.austinchamber.com/economic-development/austin-profile/population/overview).

### [Population Growth from 2007 - 2017](https://cdn1.austinchamber.com/archive/images/ed/chart-population-growth.jpg?mtime=20190620093848)

<img width="432" height="324" src="https://media-exp1.licdn.com/dms/image/C5612AQHg1HEO43LiTg/article-inline_image-shrink_1000_1488/0/1588796600849?e=1640822400&v=beta&t=uBzHUME4Nkjf2sJrzqW9W3aCBkqExUyPUyf0m0-DY2A"/>

With this knowledge known, the focus here is to educate any interested party that would be coming to the City of Austin for work or leisure would like to know about some particular venues or hotspots within the city. Any business owners that may want to start a business in a given section of a city would also want to know what the current popular venues are in each respectable neighborhood. Those looking to buy a home would want to see what the median cost of a home would be in each community.

These problems will are considered, and a map will be created with an informational view of clustered venues and median real estate values.

## B. Methodology

* * *

In order to find all of this data, several sources will be used:

- Google Sheets scripts for quickly obtaining zip codes and latitudinal and longitudinal coordinates
- [Foursquare API](https://developer.foursquare.com/) to scrape the local area for venues in each neighborhood
- [GEOJson file](https://geo.nyu.edu/) for mapping of the Austin, Tx area
- A regional area analysis of housing prices obtained through [DemographicsNow](https://library.austintexas.gov/database/gale-business-demographicsnow)

First, the latitudinal and longitudinal coordinates of each neighborhood would be needed. The zip codes and names of these neighborhoods would be found on Wikipedia and independently scraped using an external Jupyter Notebook utilizing [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), a web scraper. Once the zip codes were identified, latitudinal and longitudinal coordinates were found via a [GSheets script](https://raw.githubusercontent.com/jeff-mos-def/Coursera_Capstone/master/Applied%20Data%20Science%20Capstone/BoTN%20Final/Snapshots/ziploc.jpg). This was stored in a GSheets file, and using the scraped data previously acquired. The neighborhoods had their names concatenated with "Tx" so the [zip codes were then able to be matched](https://raw.githubusercontent.com/jeff-mos-def/Coursera_Capstone/master/Applied%20Data%20Science%20Capstone/BoTN%20Final/Snapshots/geo2zip.jpg) to the scraped communities. Areas containing the same zip codes were then matched and strung together.

Next, the report of median housing costs would be needed. Fortunately, the Austin Virtual Library has access to [DemographicsNow](https://library.austintexas.gov/database/gale-business-demographicsnow), a tool that could be used to quickly obtain all relevant data in regards to median housing prices. Immediate housing prices were not available, so the data used was taken in 2018. The housing cost data was then added to the neighborhood listings.

All data was stored in a GitHub repository and IBM Cognitive Class Laboratory. The data was saved as a CSV and called into a dataframe using Pandas. This resulted in the working dataframe to be used:

<img width="432" height="132" src="https://media-exp1.licdn.com/dms/image/C5612AQEkGAHC7_SflQ/article-inline_image-shrink_1000_1488/0/1588796711630?e=1640822400&v=beta&t=h2K4vawE8ofvIDPImk9C1kKEkoSOe-avXSOXroqHr4E"/>

[Folium](https://python-visualization.github.io/folium/) was used to map the local Austin area. Markers were overlayed to designate which areas consisted of neighborhoods, as identified by latitudinal and longitudinal coordinates.

<img width="432" height="492" src="https://media-exp1.licdn.com/dms/image/C5612AQGuwu7RPlnpNw/article-inline_image-shrink_1000_1488/0/1588796759105?e=1640822400&v=beta&t=SfU7A5NFOo4Kd229yVGdR0usnxfBIMJ6CKb54gNZkeE"/>

In a previous exercise, it was learned that the FourSquare API could be utilized to explore the contents of boroughs, here defined as neighborhoods, and segment them into a local area search. Due to the broad area of Austin, a radius of 5500 meters (34.18 miles) was used as a visitor may want to drive across Austin to see various sights. Venues were limited at 100 for this exercise. When FourSquare was called upon, the head() of the call brought the following venues:

<img width="432" height="163" src="https://media-exp1.licdn.com/dms/image/C5612AQHtw1cZELMQaQ/article-inline_image-shrink_1000_1488/0/1588796822123?e=1640822400&v=beta&t=xV-7bpuIwBG8EJbLLyF32OUepts8jYVXqdSM4vOPOZM"/>

When this data was looked at as a whole, it was discovered that FourSquare included gas stations, convenience stores, and bus stops in the API feedback. Ultimately, this was left in the whole of the data as some gas stations and convenience stores in Austin have bespoke goods or services. Bus stations and street intersections were also left in to keep the whole of the FourSquare data.

When checked, a total of 720 separate venues within the city was met. This table was then merged with the table of the neighborhoods.

<img width="744" height="177" src="https://media-exp1.licdn.com/dms/image/C5612AQEOYYPicmS9wA/article-inline_image-shrink_1000_1488/0/1588796873181?e=1640822400&v=beta&t=S1Mbce9t01ZqN_uG_N0KIVZsMPdxYPUdfutcElxBI88"/>

When the data were pooled for evaluation, there were some interesting findings. Only one neighborhood hit the limit of 100 venues per zip code, despite the fact that this is a merged zip code list. This could be due to incorrect identification by the business itself, or by not enough FourSquare reviews in certain areas.

It was also found that the zip codes of specific neighborhoods (Westlake Hills, NorthWest Austin, and RiverPlace) were producing errors in the data analysis and returning 0 venues. These zip codes were removed for venue analysis but kept for housing cost analysis.

The original bar graph generated had shortened neighborhood names. Full names are listed for complete viewing.

<img width="744" height="284" src="https://media-exp1.licdn.com/dms/image/C5612AQGdEddATDRklg/article-inline_image-shrink_1000_1488/0/1588796915172?e=1640822400&v=beta&t=v-daalmpIRbQ0p4FrjmfIkx72PUINPsw071yX2FfaXE"/>

Out of all the venues polled by Foursquare, the noise needed to be cleared out for further analysis. A "Top 10" venue list was created for each neighborhood.

<img width="744" height="151" src="https://media-exp1.licdn.com/dms/image/C5612AQH7gSDE1y6gsg/article-inline_image-shrink_1000_1488/0/1588796985453?e=1640822400&v=beta&t=jkesFPucwHRjkfGC81hYFzB87h_a1XVYwp3Ic3N96gc"/>

Further analysis would need to be done to group our neighborhoods by common venues. Unsupervised K-Means clustering will be used in this instance. To consolidate our venues, we will need to know what our optimal k value would be for clustering. The elbow method will be used to find this optimal k value.

<img src="https://media-exp1.licdn.com/dms/image/C5612AQFw_VcN6AyNaA/article-inline_image-shrink_1000_1488/0/1588797015140?e=1640822400&v=beta&t=atwaGo1Q5qaUpunAEMvAEPaseRPC37J18r6e57nY0Yo"/>

The optimal k value would be 2 in this case. This is not an optimal case for k value cluster visualization. All venues across Austin would be grouped into two bins. Despite what the data is saying, the k value selected will be 5 for visual purposes.

The venues were grouped in a "Top 10" fashion, yielding this table:

<img src="https://media-exp1.licdn.com/dms/image/C5612AQHtw1cZELMQaQ/article-inline_image-shrink_1000_1488/0/1588796822123?e=1640822400&v=beta&t=xV-7bpuIwBG8EJbLLyF32OUepts8jYVXqdSM4vOPOZM"/>

The 1st Most Common Venue can also be displayed via a bar chart.

<img width="744" height="314" src="https://media-exp1.licdn.com/dms/image/C5612AQFYEIblQFSL8g/article-inline_image-shrink_1000_1488/0/1588797143845?e=1640822400&v=beta&t=lS9XFk_6JIRqf-Nw4bKobQjPbcGSSnU4Xyrjil570iQ"/>

Clusters were then labeled according to their contents:

- Cluster 0: Pizza/Coffee
- Cluster 1: Home Stores
- Cluster 2: Total Austin
- Cluster 3: Indian Restaurants
- Cluster 4: Parks

Housing costs were also a point of concern in this study. Referring back to our first dataset, we can put the housing prices in Austin in a histogram for visualization:

<img src="https://media-exp1.licdn.com/dms/image/C5612AQGviTuS5Ael9g/article-inline_image-shrink_1000_1488/0/1588797185336?e=1640822400&v=beta&t=iQ9c1M_rDm-czjzxdhm7_7O9Vt7KjcdSU00D1Y_AJO0"/>

Housing costs were then binned in the following ranges:

- Less than 150,000 USD
- Ranging from 150,001-300,000 USD
- Ranging from 300,001-450,000 USD
- Ranging from 450,001-600,000 USD
- Greater than 600,000 USD

## C. Results

* * *

The data is now able to be displayed in a centralized table for final viewing and visualization.

First, the clusters are added into the "Top 10" table:

<img width="744" height="234" src="https://media-exp1.licdn.com/dms/image/C5612AQHevMZW4gJjFg/article-inline_image-shrink_1000_1488/0/1588797226020?e=1640822400&v=beta&t=V10XjZypGdJSSfAP5KPtbVjQAW19P-plei_6Su9CQ-Q"/>

Now the kmeans clustered and grouped zip codes are clearly defined on the generated map:

<img width="432" height="380" src="https://media-exp1.licdn.com/dms/image/C5612AQHit-jCb3cFyg/article-inline_image-shrink_1000_1488/0/1588797268833?e=1640822400&v=beta&t=3t7e0vV53vXcpraic1EQoLhKkQKEaRMiLBlVxg_fJTI"/>

In the final map, we have a combined representation of all the data pulled and grouped for this project. A GEOJson file was downloaded from the Spatial Data Repository and used for this purpose. This map was then overlayed with the following information:

- Neighborhood name
- Cluster name
- Top 3 venues
- Color-coded representation of median housing cost

<img width="432" height="709" src="https://media-exp1.licdn.com/dms/image/C5612AQGbk4p93jzEeQ/article-inline_image-shrink_1000_1488/0/1588797299509?e=1640822400&v=beta&t=pm2u8PeUOLrJ0zekYqO0JiRmDZab-at-WsQBKzhGs_c"/>

## D. Discussion

* * *

With the continuous influx of people relocating to Austin, Tx, this information could be valuable. Austin is a growing city with many different neighborhoods that sport many various venues and costs associated with each location.

The methods of grouping and clustering venues throughout the city remains in question. Although using the elbow method to identify the optimal k value to be used for k means clustering is the tried and true way of partitioning observations, it would not have yielded much to visualize in this scenario. With k = 5, the clustering was forced to group more venues into separate clusters. This method created a more visually attainable view of the data.

The median home values were also taken from 2018, as this was the most current data available. However, this would still provide the reader with an overall view of the median value distribution over the city. When newer data is available, the code can be updated.

This information would also be of knowledge that investors, small business owners, and budding entrepreneurs would like to see. By seeing the top businesses in a given area, along with the surrounding areas, one could quickly call back the dataframe containing the raw data to see each separate business to forecast investment, construction, marketing, or advertising.

## E. Conclusion

* * *

Planning a visit, move, or business venture always requires research. With a quick overview, one could get at a bird's eye view of the data of the Austin, Tx area. It could be seen what to expect when coming to this city. This gives a look-ahead to investors, property managers, or city planners as well.

## F. References

* * *

1.  “Austin, Texas.” Wikipedia, Wikimedia Foundation, 4 May 2020, [en.wikipedia.org/wiki/Austin,_Texas](http://en.wikipedia.org/wiki/Austin,_Texas).
2.  Egan, John. “This Is How Much Austin's Population Could Surge through 2029, Study Says.” CultureMap Austin, 15 Jan. 2020,[austin.culturemap.com/news/city-life/01-15-20-austin-population-growth-through-2029-cushman-wakefield/](http://austin.culturemap.com/news/city-life/01-15-20-austin-population-growth-through-2029-cushman-wakefield/).
3.  “Foursquare Developer.” Foursquare Developer, [developer.foursquare.com/](http://developer.foursquare.com/).
4.  Gale Business: Demographics Now, [www.gale.com/c/business-demographicsnow](http://www.gale.com/c/business-demographicsnow).
5.  NYU Spatial Data Repository, [geo.nyu.edu/](http://geo.nyu.edu/).
6.  “Population Overview.” Austin Chamber of Commerce, [www.austinchamber.com/economic-development/austin-profile/population/overview](http://www.austinchamber.com/economic-development/austin-profile/population/overview).