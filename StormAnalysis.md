---
output: html_document
---
Major storms and weather events in the United States
====================================================

##Synopsis
In this research involves exploring the U.S. National Oceanic and Atmospheric Administration's (NOAA) storm database. The database contains characteristics of large storms and weather events in the United States of America. The database also contains time and location where they occur, as well as estimates of any fatalities, injuries, and property damage. The data analysis addresses the types of events that are most harmful with respect to population health and the types of events that have the greatest economic consequences.


##Loading the required packages

```{r required packages}
library(knitr)
library(ggplot2)
library(dplyr)
```

Global knitr setup
```{r global knitr setup}
require(knitr)
opts_chunk$set(message=FALSE, fig.width = 6, fig.height = 6)
```


## Loading and preprocessing the data

###1. Load the data (i.e. read.csv())
Download the file and put in the 'data' folder:
```{r file download}
if(!file.exists("./data")){dir.create("./data")}
fileUrl <- "https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2FStormData.csv.bz2" 
download.file(fileUrl, destfile = "./data/StormData.csv.bz2")
```

Read the data:
```{r read data} 
if(!exists("Data")){
        Data <- read.csv("./data/StormData.csv.bz2")
}
```

###2. Data transformation

```{r transform data}
stormData <- Data[c("BGN_DATE", "EVTYPE", "FATALITIES", "INJURIES", "PROPDMG", "PROPDMGEXP", "CROPDMG", "CROPDMGEXP")]
```

```{r date}
stormData$BGN_DATE<-as.Date(stormData$BGN_DATE,format = "%m/%d/%Y")
```

```{r plot}
qplot (x = format(BGN_DATE,"%Y"), data = stormData, geom = "bar", fill = format(BGN_DATE,"%Y")>="1995") +
        ggtitle("Storm events registered per year") + 
        xlab("Year") +
        scale_x_discrete(breaks=seq(1950,2011,by = 10)) +
        guides(fill=FALSE)
```

###3. Results

####3.1 Across the United States, which types of events are most harmful with respect to population health?

```{r results population health}

```

####3.2 Across the United States, which types of events have the greatest economic consequences?

```{r restults economic consequences}

```