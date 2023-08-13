# Entry-Level Data Analyst
##### Technical skills: R programming, SQL, Tableau, Spreadsheets, Slides

### Education
* Coursera Inc. 2023 *Google Data Analytics Certificate*
* University of Nigeria 2018 *B.Eng Electrical Engineering*

### Projects
<details>
  <summary>##### Case study 1: How Does a Bike-Share Company Navigate Speedy Success?</summary>
  <br>
INTRODUCTION
This is an analytics report for Cyclistic Bike-Share fictional Company in Chicago. This report would analyze how annual members and casual riders use Cyclistic bikes differently. The purpose of this script is to consolidate downloaded Cyclistic data into a single dataframe and then conduct simple analysis to help answer the key question: “In what ways do members and casual riders use Cyclistic’s bikes differently?”. Lily Moreno, the Director of Marketing has a hypothesis that suggests that Cyclistic’s future success depends on maximizing the number of annual memberships. There are three questions guiding the future marketing program of the company. These are: * How do annual members and casual riders use cyclistic bikes differently? * Why would casual riders buy cyclistic annual memberships? * How can Cyclistic use digital media to influence casual riders to become members?
The Cyclistic Marketing Analytics team have been tasked with answering these questions. The first question has been assigned to me which is the business task of this report stated clearly below. The insights from this analysis would prove or disprove Lily Moreno’s hypothesis.
I have decided to use R programming language on the RStudio to carry out the business task because of the following reasons; it allows me perform all my analysis in one place, it is designed to handle large datasets, it makes it easy to reproduce my work on different datasets, it allows me create detailed visualizations and it can work with data that is spread across multiple categories or groups like the one I am to work with. I realized that upon opening the sixth file, my microsoft excel crashes. This can only mean that I would have to spend lot of time working on individual files before combining them into one I could analyze to answer the business question more effectively. RStudio can save me the trouble.
To be able to use functions in R, I must install and load the packages in R that are associated with those functions. For Data Analysis, I would install and load “tidyverse”,“skimr”, “janitor”, “dplyr”, “readr”, and “ggplot2” packages using the install.packages() and library() functions.
library(tidyverse) helps wrangle data library(lubridate) helps wrangle date attributes library(ggplot2) helps visualize data getwd() displays my working directory
ASK PHASE: COLLECT DATA
I would be working with the dataset from the past twelve months in Cyclistic database. They are all in CSV file formats. I would import them into individual dataframes that I would work with and then bring them together. The past twelve months ranges from July 2022 to June 2023. I use the following codes to import the downloaded data into RStudio.
library(readr)
jul_2022_data <- read_csv("R-4.3.1/cyclistic_trip_data/202207-cyclistic-tripdata.csv")
## Rows: 823488 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
aug_2022_data <- read_csv("R-4.3.1/cyclistic_trip_data/202208-cyclistic-tripdata.csv")
## Rows: 785932 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
sep_2022_data <- read_csv("R-4.3.1/cyclistic_trip_data/202209-cyclistic-tripdata.csv")
## Rows: 701339 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
oct_2022_data <- read_csv("R-4.3.1/cyclistic_trip_data/202210-cyclistic-tripdata.csv")
## Rows: 558685 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
nov_2022_data <- read_csv("R-4.3.1/cyclistic_trip_data/202211-cyclistic-tripdata.csv")
## Rows: 337735 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
dec_2022_data <- read_csv("R-4.3.1/cyclistic_trip_data/202212-cyclistic-tripdata.csv")
## Rows: 181806 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
jan_2023_data <- read_csv("R-4.3.1/cyclistic_trip_data/202301-cyclistic-tripdata.csv")
## Rows: 190301 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
feb_2023_data <- read_csv("R-4.3.1/cyclistic_trip_data/202302-cyclistic-tripdata.csv")
## Rows: 190445 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
mar_2023_data <- read_csv("R-4.3.1/cyclistic_trip_data/202303-cyclistic-tripdata.csv")
## Rows: 258678 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
apr_2023_data <- read_csv("R-4.3.1/cyclistic_trip_data/202304-cyclistic-tripdata.csv")
## Rows: 426590 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
may_2023_data <- read_csv("R-4.3.1/cyclistic_trip_data/202305-cyclistic-tripdata.csv")
## Rows: 604827 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
jun_2023_data <- read_csv("R-4.3.1/cyclistic_trip_data/202306-cyclistic-tripdata.csv")
## Rows: 719618 Columns: 13
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (7): ride_id, rideable_type, start_station_name, start_station_id, end_...
## dbl  (4): start_lat, start_lng, end_lat, end_lng
## dttm (2): started_at, ended_at
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
PREPARE PHASE: STATE BUSINESS TASK AND COMBINE DATASET
BUSINESS TASK: UNDERSTANDING THE DIFFERENT USAGE OF BIKES BY MEMBERS AND CASUAL RIDERS
The twelve data frames involved in this business task were sourced from Cyclistic database. (Note: The datasets have a different name because as stated in the introduction of this report, Cyclistic is a fictional company, it is non-existent. So it is assumed that the data belong to Cyclistic, hence our data is first-party data. For the purposes of this case study, the datasets are appropriate and will enable me answer the business questions. The data has been made available by Motivate International Inc. under this license. The data was downloaded into my computer and stored in a folder titled cyclistic_trip_data. All twelve data frames have thirteen consistent variables with different number of observations. We can confirm this by using the colnames() function to preview each dataset.
colnames(jul_2022_data)
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(aug_2022_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(sep_2022_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(oct_2022_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(nov_2022_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(dec_2022_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(jan_2023_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(feb_2023_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(mar_2023_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(apr_2023_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(may_2023_data) 
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
colnames(jun_2023_data)
##  [1] "ride_id"            "rideable_type"      "started_at"        
##  [4] "ended_at"           "start_station_name" "start_station_id"  
##  [7] "end_station_name"   "end_station_id"     "start_lat"         
## [10] "start_lng"          "end_lat"            "end_lng"           
## [13] "member_casual"
Now I proceed to stack all twelve data frames into one big data frame I have named year_rides which is needed to answer the business question.
library(dplyr)
## 
## Attaching package: 'dplyr'
## The following objects are masked from 'package:stats':
## 
##     filter, lag
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
year_rides <- bind_rows(jul_2022_data, aug_2022_data, sep_2022_data, oct_2022_data, nov_2022_data, dec_2022_data, jan_2023_data, feb_2023_data, mar_2023_data, apr_2023_data, may_2023_data, jun_2023_data)
To test for data integrity, I first look at the structure of the data to check for inconsistent data types before plotting a bar graph to get a visual of what bike_type is most preferred by riders.
str(year_rides)
## spc_tbl_ [5,779,444 × 13] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
##  $ ride_id           : chr [1:5779444] "954144C2F67B1932" "292E027607D218B6" "57765852588AD6E0" "B5B6BE44314590E6" ...
##  $ rideable_type     : chr [1:5779444] "classic_bike" "classic_bike" "classic_bike" "classic_bike" ...
##  $ started_at        : POSIXct[1:5779444], format: "2022-07-05 08:12:47" "2022-07-26 12:53:38" ...
##  $ ended_at          : POSIXct[1:5779444], format: "2022-07-05 08:24:32" "2022-07-26 12:55:31" ...
##  $ start_station_name: chr [1:5779444] "Ashland Ave & Blackhawk St" "Buckingham Fountain (Temp)" "Buckingham Fountain (Temp)" "Buckingham Fountain (Temp)" ...
##  $ start_station_id  : chr [1:5779444] "13224" "15541" "15541" "15541" ...
##  $ end_station_name  : chr [1:5779444] "Kingsbury St & Kinzie St" "Michigan Ave & 8th St" "Michigan Ave & 8th St" "Woodlawn Ave & 55th St" ...
##  $ end_station_id    : chr [1:5779444] "KA1503000043" "623" "623" "TA1307000164" ...
##  $ start_lat         : num [1:5779444] 41.9 41.9 41.9 41.9 41.9 ...
##  $ start_lng         : num [1:5779444] -87.7 -87.6 -87.6 -87.6 -87.6 ...
##  $ end_lat           : num [1:5779444] 41.9 41.9 41.9 41.8 41.9 ...
##  $ end_lng           : num [1:5779444] -87.6 -87.6 -87.6 -87.6 -87.7 ...
##  $ member_casual     : chr [1:5779444] "member" "casual" "casual" "casual" ...
##  - attr(*, "spec")=
##   .. cols(
##   ..   ride_id = col_character(),
##   ..   rideable_type = col_character(),
##   ..   started_at = col_datetime(format = ""),
##   ..   ended_at = col_datetime(format = ""),
##   ..   start_station_name = col_character(),
##   ..   start_station_id = col_character(),
##   ..   end_station_name = col_character(),
##   ..   end_station_id = col_character(),
##   ..   start_lat = col_double(),
##   ..   start_lng = col_double(),
##   ..   end_lat = col_double(),
##   ..   end_lng = col_double(),
##   ..   member_casual = col_character()
##   .. )
##  - attr(*, "problems")=<externalptr>
The data types seem to be consistent, however, some variable names are not very intuitive. I proceed to rename them: member_casual to user_type, ended_at to end_time, started_at to start_time, ride_id to bike_id, and rideable_type to bike_type.
year_rides <- rename(year_rides, user_type= member_casual, end_time = ended_at, start_time = started_at, bike_id=  ride_id, bike_type = rideable_type)
To quickly check for data integrity, I run the data through the following code chunk.
library(ggplot2)
ggplot(data=year_rides)+ geom_bar(mapping=aes(x=bike_type, fill=user_type))+ labs(title = "Cyclistic Bike Usage", subtitle = "Three Bikes Samples", caption = "Data from Cyclistic's Database")
 
To test for the data integrity, I bring the observations to life by comparing a bar chart of the different kinds of bikes as this would indicate inclusivity. Cyclistic is a bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.Cyclistic claimed to have 8% of their customers using the assistive options-reclining bikes, hand tricycles, and cargo bikes. Their data however, did not suggest that they have assistive options nor do their customers use them. The Y-axis which R defaults to count is not clear in the sense that the numbers do not add up to the total number of observations in the year_rides data frame, this shows that our data has lots of errors, ranging from negative values to incomplete data . So our data do not ROCCC(Reliable, Original, Complete, Cited, Comprehensive) entirely. The Data source however, is reliable as it was gotten from a real company that we decided to use to represent our fictional company for the case of this case study. The data is Original as it belongs to the company. The data is comprehensive as all critical information needed to answer the business question are contained in it BUT incomplete. The data is Current because they are information of the very recent past twelve months which is July 2022 to June 2023.The data is cited, the link can be found above.The dataset was created by the company we are working for(hypothetically),It is part of a credible organization and it was last refreshed Jul 13th 2023, 10:22:44 pm. Since our dataset are reliable, original, current, cited BUT not comprehensive, then, our data do not ROCCC! We were already permitted to use this data as seen in the license agreement above. Our data just has a lot of missing information in some month’s data.
I proceed to organize our data. I sort the data by when the ride started, which is the start_time variable so the data is organized in a chronological order according to how they were taken so I can proceed to check for duplicate data.
year_rides <- arrange(year_rides, start_time)
PROCESS PHASE: DATA CLEANING AND MANIPULATION
I have decided to use R programming language on the RStudio to carry out the business task because of the following reasons; it allows me perform all our analysis in one place, it is designed to handle large dataset, it makes it easy to reproduce my work on different datasets, it allows me create detailed visualizations and it can work with data that is spread across multiple categories or groups like the one I am to work with. I realized that upon opening the sixth file, my microsoft excel crashes. This can only mean that I would have to spend lot of time working on individual files before combinimg them into one I could analyze to answer the business question more effectively. RStudio can save me the trouble. The bar chart above suggests that the data has some errors. I proceed to clean my data. First I check for duplicates. Then I create new variables that would help answer the business question.
I need to ensure that the unique data are relevant to the business task. I proceed to remove the irrelevant variables and make some calculations to create new columns. The data can only be aggregated at the ride-level, which is too granular. I will proceed to add some additional columns of data – such as day_of_week and ride_length – that provide additional opportunities to aggregate the data. Sunday=1, Monday=2, Tuesday=3, Wednesday=4, Thursday=5, Friday=6, and Saturday=7. I will proceed to add a calculated field for length of ride since the data did not have the “trip_duration” column. I will add “ride_length” to the entire dataframe for consistency which I would calculate by subtracting start_time from end_time.
library(lubridate)
## 
## Attaching package: 'lubridate'
## The following objects are masked from 'package:base':
## 
##     date, intersect, setdiff, union
year_rides_1 <- year_rides %>% select(bike_id, bike_type, start_time, end_time, user_type) %>% mutate(ride_length= difftime(end_time, start_time, units = "secs"), day_of_week= wday(start_time))
I would remove bad data with the drop_na() function in our future analysis as they are bad data. I learnt more about this from here I proceed to inspect the structure of the columns of the new_year_rides data frame. I test for data integrity again by plotting the bar graph again.
The dataframe includes a few hundred entries when bikes were taken out of docks and checked for quality by Cyclistic or ride_length was negative.
colnames(year_rides_1)
## [1] "bike_id"     "bike_type"   "start_time"  "end_time"    "user_type"  
## [6] "ride_length" "day_of_week"
str(year_rides_1)
## tibble [5,779,444 × 7] (S3: tbl_df/tbl/data.frame)
##  $ bike_id    : chr [1:5779444] "7EA7A3AEAAB5F621" "AAB8184C169FF64E" "C60D39A2484F33FB" "B153121FD7B6B014" ...
##  $ bike_type  : chr [1:5779444] "classic_bike" "electric_bike" "electric_bike" "electric_bike" ...
##  $ start_time : POSIXct[1:5779444], format: "2022-07-01 00:00:01" "2022-07-01 00:00:02" ...
##  $ end_time   : POSIXct[1:5779444], format: "2022-07-01 00:11:06" "2022-07-01 00:41:27" ...
##  $ user_type  : chr [1:5779444] "casual" "casual" "member" "casual" ...
##  $ ride_length: 'difftime' num [1:5779444] 665 2485 442 546 ...
##   ..- attr(*, "units")= chr "secs"
##  $ day_of_week: num [1:5779444] 6 6 6 6 6 6 6 6 6 6 ...
library(tidyr)
year_rides_2<- year_rides_1
year_rides_2 = year_rides_1[year_rides_1$ride_length > 0, ]
drop_na(year_rides_2)
## # A tibble: 5,778,870 × 7
##    bike_id          bike_type  start_time          end_time            user_type
##    <chr>            <chr>      <dttm>              <dttm>              <chr>    
##  1 7EA7A3AEAAB5F621 classic_b… 2022-07-01 00:00:01 2022-07-01 00:11:06 casual   
##  2 AAB8184C169FF64E electric_… 2022-07-01 00:00:02 2022-07-01 00:41:27 casual   
##  3 C60D39A2484F33FB electric_… 2022-07-01 00:00:16 2022-07-01 00:07:38 member   
##  4 B153121FD7B6B014 electric_… 2022-07-01 00:00:27 2022-07-01 00:09:33 casual   
##  5 FDBFB9BD7A38F66D electric_… 2022-07-01 00:00:48 2022-07-01 00:07:34 casual   
##  6 56C6CCD4EE89184D classic_b… 2022-07-01 00:00:51 2022-07-01 00:20:17 casual   
##  7 F6689D438A3AC26A classic_b… 2022-07-01 00:01:19 2022-07-01 00:10:32 member   
##  8 150FDF9587B688D9 electric_… 2022-07-01 00:01:24 2022-07-01 00:27:39 casual   
##  9 D5F2F535B4AE0B59 electric_… 2022-07-01 00:01:29 2022-07-01 00:22:38 member   
## 10 AB15FB3DE29FE40C electric_… 2022-07-01 00:01:34 2022-07-01 00:14:15 member   
## # ℹ 5,778,860 more rows
## # ℹ 2 more variables: ride_length <drtn>, day_of_week <dbl>
Now to ensure the data’s integrity, I plot a bar graph yet again with the dataset with no “NA” values and no negative ride length values.
ggplot(data= year_rides_2)+ geom_bar(mapping = aes(x = bike_type, fill = user_type))+ labs(title = "Cyclistic Bike Usage", subtitle = "Three Bikes Samples", caption = "Data from Cyclistic's Database")
 
The number of observations in the new_year_rides dataset is Five million,seven hundred and seventy nine thousand, four hundred and fourteen(5,779,414). That is pretty big. R can give counts in scientific notation formats such as “0e+00”, “1e+06”, “3e+06”. This can help our labeling look neat. To translate the meaning of these numbers, it gives: * 0e+00= 010^0=01=0 * 1e+06=110^6=11000000=1000000(0ne Million) * 2e+06=210^6=21000000=2000000(Two Million) * 3e+06=310^6=31000000=3000000(Three Million)
I decide to take a look at the structure of my new_year_dataset one more time, to be certain that all variables are formatted accurately.
str(year_rides_2)
## tibble [5,778,870 × 7] (S3: tbl_df/tbl/data.frame)
##  $ bike_id    : chr [1:5778870] "7EA7A3AEAAB5F621" "AAB8184C169FF64E" "C60D39A2484F33FB" "B153121FD7B6B014" ...
##  $ bike_type  : chr [1:5778870] "classic_bike" "electric_bike" "electric_bike" "electric_bike" ...
##  $ start_time : POSIXct[1:5778870], format: "2022-07-01 00:00:01" "2022-07-01 00:00:02" ...
##  $ end_time   : POSIXct[1:5778870], format: "2022-07-01 00:11:06" "2022-07-01 00:41:27" ...
##  $ user_type  : chr [1:5778870] "casual" "casual" "member" "casual" ...
##  $ ride_length: 'difftime' num [1:5778870] 665 2485 442 546 ...
##   ..- attr(*, "units")= chr "secs"
##  $ day_of_week: num [1:5778870] 6 6 6 6 6 6 6 6 6 6 ...
All data types are matched accurately
ANALYZE PHASE: DESCRIPTIVE ANALYSIS
Now I conduct a descriptive analysis to better understand what has happened in Cyclistic with our data. I would create a summary or abstraction that would support further investigation, analysis or actions. I would summarize using ride_length, day_of_week and user_type so as to see patterns, identify anomalies, improve planing and compare things. First, I calculate the mean of ride_length, median of ride_length, maximum of ride_length, minimum of ride_length and the mode of day_of_week.
•	The mean of ride length calculates the average of the total ride_length.
•	The median of ride_length calculates the midpoint number in the ascending array of ride_length.
•	The maximum of ride_length calculates the longest ride in the past year.
•	The minimum of ride_length calculates the shortest ride in the past year.
•	The mode of day_of_week calculates the best day riders prefer
library(DescTools)
library(dplyr)
year_rides_summary <- year_rides_2 %>%
  group_by(user_type) %>%
  summarise(mean_ride_length= mean(ride_length), median_ride_length= median(ride_length), longest_ride= max(ride_length), shortest_ride= min(ride_length), mode_day= Mode(day_of_week))
The mean_ride_length, median_ride_length for member riders are 1,663.9669secs, 720secs and Day 7 respectively. The mean_ride_length, median_ride_length and mode_day for casual riders are 743.0477secs, 513secs and Day 4 respectively. I proceed to add the average ride time by each day for members vs casual users to the year_rides_summary data frame. I got directions on how to write the code from here
library(tidyr)
year_rides_summary_1<- year_rides_2 %>%
  drop_na() %>%
  group_by(user_type, day_of_week) %>%
  summarise(mean_ride_length= mean(ride_length), median_ride_length= median(ride_length), longest_ride= max(ride_length), shortest_ride= min(ride_length), mode_day_of_week= Mode(year_rides_2$day_of_week), .groups = 'drop')
All shortest ride_lengths for both members and casual riders is 1 second. I do not think that this is accurate because a trip would be calculated by how long it would take a rider to move from one docking station to another or from one docking station back to the same docking station. However, I would leave the data like that as this is a case study of a fictional company and I can not contact my stakeholder, Lily Moreno to lay out my concern. The year_rides_summary_1 data frame gives the, mean, median and mode of ride_length by the day_of_week which have been assigned numeric representation, Sunday=1, Monday=2, Tuesday=3, Wednesday=4, Thursday=5, Friday=6, Saturday=7. The most frequent day_of_week, the mode is the day 7 which is Saturday. The longest ride_length for casual riders goes to day 7 with a total of two million, four hundred and eighty three thousand, two hundred and thirty five seconds(2,483,235 secs), an average ride length of approximately one thousand, nine hundred and forty two seconds(1,941.7318secs), and a median of 00:14:09. The longest ride_length for member riders goes to day 7 with a total of ninety three thousand, five hundred and eighty seconds(93,580secs), an average ride length of approximately eight hundred and thirty eight seconds(837.5520secs) and a median of 00:09:32.
I proceed to visualize the count of rides by weekday
library(ggplot2)
ggplot(data= year_rides_2)+ geom_bar(mapping = aes(x = day_of_week, fill = user_type))+ labs(title = "Cyclistic Bike Usage", subtitle = "Seven Days of the Week", caption = "Data from Cyclistic's Database")
 
We can see clearly that casual riders have higher ride_lengths all through the week even on the least popular day being Sunday.Next I create a visualization for mean_ride_length for each day of the week.
ggplot(data= year_rides_summary_1)+ geom_col(mapping = aes(x = day_of_week, y= mean_ride_length, fill = user_type), position = "dodge")+ labs(title = "Cyclistic Average Bike Usage", subtitle = "Average Ride Length Per Day", caption = "Data from Cyclistic's Database")
## Don't know how to automatically pick scale for object of type <difftime>.
## Defaulting to continuous.
 
The column chart has given us a clear visual on the huge differences between the average ride lengths for member riders and casual riders on each day of the week. It is evident that the casual riders spend way more time on the bikes as compared to the member riders.
SHARE PHASE: EXPORT SUMMARY FILE FOR FURTHER ANALYSIS
I proceed to create a csv file that I will visualize in Excel, Tableau, or any presentation software. I learnt how to export data from here
write.csv(year_rides_summary_1, "C:\\Users\\hp\\Downloads\\User_type_summary.csv", row.names=FALSE)
</details>

##### Case Study 2: How Can a Wellness Technology Company Play it Smart?
##### Case Study 3: What Makes a Book on Amazon a Best Seller?

### Work Experience 
##### Nene International Private School, Enugu *Teaching Assistant (April 2019 - March 2020)*
In my home countrty, there is a one year compulsory National Youth Service Corp (NYSC). During this time, I taught Mathematics to JSS1, JSS2 and JSS3 students. Collaborated with other science teachers to administer tests and curriculum instructions to students. I maintained constant communication with staffs and superiors. 

##### ASO Radio and Television, Abuja  *Interactive Field Experience (May 2017 - November 2017)*
Designed and simulated a transmitter of 93.5MHZ using Proteus Simulation Tool. Replaced faulty components of Transmitters, Amplifiers, UPS, Equalizers e.t.c. Serviced and cleaned up Air Conditioners, Generators and Audio Cables. Assisted in the installation of an Antenna

##### Amasons Stores, Abuja *Cashier (August 2012 - January 2014)*
Monitored sales activities to ensure that customers received satisfactory services and quality goods. Created a positive atmosphere for clientele, responding to customer enquiries and complaints. Monitored, directed and prioritized all store front end activities in a fast paced environment.
