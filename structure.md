### Daylily Data Science Portfolio

### FLow
 Problem → Data → EDA → Modeling / Statistics → Validation → Recommendation

### Define The Problem

With 100 years of intesive hybridization of Daylily in North America and across the world that has resulted in over 102,000 registered varieties within the American Daylily Society database, there is significant variation in flower color and shape, as well as a many different growth habits, heights, and even regional specialization. 

Collectors and hybridizers have a seemingly endless number of varieties to choose from with thousands of new introductions each year. While exciting, this presents a unique problem where more involved screening and filtering becomes necessary to find the "best" plants. 

New and Experinced hybridizers face an even larger dilema... how do you pick the best breeding stock? There a vareity of strategies that hybridizers employ. 
 - Some choose only award winning varieties as parents
 - Others will only select varieties with a specifc trait of interest
 - Even fewer will select parents based on a few numeric traits outside of the flower qualities
 - A rare minority will coduct intesive screening trials and select for only varieites that perform well based on growth habit as well as disease and pest resistance. 
 - A vast majority, however, will utilize whatever they have on hand and will cross two pretty flowers together and hope for the best. 

 While there have been some truly excellent varieties that have been created, a data-driven approach could drastically improve hybridizing outcomes, and jumpstart new hybridizers by decreasing the time it takes to identify parent varieites that have strong general combine-ability, specific unique trait combinations, statisitcal breeding value, or even varieties with strong deviations from the norm.

 Currently no such data-driven techniques are employed beyond simple filtering. By performing an in-depth analysis, the wider daylily community could benefit from having a new and distinct perspective as well as reducing the time high potential breeding material discovery takes. 

### Data Accessibility Limitations 

The American Daylily Society database is the only accessible and relatively complete record of all daylily trecords to date. The database is accessible through the societies website (https://daylilies.org/) with some advanced filtering options based on data fields. This presents significant limitations for analyzing the data base as if it where a data set. 

In an effort to acquire a dataset to perform trend analysis on the database, I decided it would be best to iteratively scrape the database using the requests module, through a proxy, at night (off peak hours) and only requesting 10 entries at a time to avoid over extending the servers or negatively impacting other users experiences. 

The scraping process was broken down into two iterations, the first was to acquire all identified text fields and their contents, and the second was to collect all available images. The text portion took approximately 3-4 nights to complete, and the image collection took approximately 3 nights and under 4 GB of memory. 

< See Script>

### Data Overview 

The data set that was acquired had duplicates that where removed, leaving unique records of over 100,000 distinct vareities, with varying degrees of field completions which is typical of the database. 

< insert fields /+ completion stats>

### Exploratory Data Analysis




### Modeling / Stats


### Validation 



### Recommendations 
