# To review or not to review? That's the question

__Does the number of reviews that your listing is getting on AirBnB affect the actual review score? Does this effect differ between big or small cities in Spain?__

<p align="center">
  <img src="https://s3.amazonaws.com/blog4.0/blog/wp-content/uploads/Feature-Image_The-Ultimate-Guide-to-Airbnb-Reviews@2x-scaled.png" width="70%" />
</p>

## Motivation

We all know the feeling of opening an e-mail that asks you to leave a review on a product that you just bought or a listing that you stayed the night at. But do more reviews lead to a higher review score? Furthermore, this effect is examined at cities in Spain that differ in sizes, such as Malaga compared to the capital Madrid. This code is written in order to find answers to these questions.

The reason for diving into this problem is because review scores are an important factor for customers when they decide which listing to stay at. Hosts want a good review score and some push their guests to leave a review. The issue that arises is that more reviews may not necessarily lead to a higher review rating. This study is conducted in order to show hosts if they should or should not push their guests to leave reviews by analyzing the relationship between review score and the number of reviews, while taking certain moderators into account.

The study focusses on seven different cities in Spain. To be able to examine the differences between small and big cities, there are three categories; Big, Medium or Small. The number of residents determine the category of the city:
- A Big city has **more than** 1,000,000 residents.
- A Medium city has **more than** 500,000 residents.
- A Small city has **less than** 500,000 residents.


The cities:

_Big_: Barcelona and Madrid

_Medium_: Sevilla, Valencia and Malaga

_Small_: Menorca and Girona

## Method and results

<!--- First, introduce and motivate your chosen method, and explain how it contributes to solving the research question/business problem. -->
**Research method**

The research method that is used in this project is a regression analysis. This method is used to predict the influence of the independent variable amount of reviews on the dependent variable review score. In the model, the moderators city size, room type and the quasi-moderator superhost status are analysed. By using regression, there can or cannot be concluded if there is a correlation between the variables and what the exact regression is. With this information the research question is answered.

**Moderators**

The relationship between the number of reviews and actual review score may be influenced by other variables, which are integrated in the model as moderators. In this study, three moderators are considered, for which dummy coding is used.
1) City size. Each of the seven cities in Spain falls in either one of three categories; Big, Medium or Small, depending on the number of residents as was mentioned before. The base level of this variable is the "big" size. 
2) Room type. There are four categories in the dataset; Entire home/appartment, Hotel room, Private room or Shared room. In the dummy encoding, shared room is the base level. 
3) Superhost status. The dataset includes information on whether the host of the listing is a superhost or not. Experienced hosts can become a superhost upon fulfillin certain criteria, such as having a low cancellation rate, a high response rate as well as a high overall rating based on the last 365 days [[Source airbnb]](https://www.airbnb.co.uk/help/article/829/how-do-i-become-a-superhost?_set_bev_on_new_domain=1631260549_OThiYmUyZjJhOGFk).

![Conceptual model](https://user-images.githubusercontent.com/89775376/136206806-efc33fdf-0bee-4a14-beb6-8625d0972de1.png)

**Results**

The RMarkdown file contains tables that display the result of the study.
In these generated tables, it is shown that superhosts receive more reviews and higher ratings. Furthermore, the room types "private room" and "entire home" get almost double the amount of reviews compared to other room types, though there is no significant difference in terms of the rating. Additionally, the city sizes large and medium also receive more than double the amount of reviews but receive about the same rating as smaller cities on average.

In the regression model, the individual outputs for the moderators are interpreted. All the results are in the RMarkdown file.

_Moderator 1:_  The interaction effect is negative. Nonetheless, the predicted ratings for superhosts are higher and this effect is highly significant.

_Moderator 2:_ For the second moderator, room_type, the results are statistically insignificant (p=.95, p=.34, p=.83). Thus, no further work is needed on this moderator, as this moderator does not influence the relationship between the rating and the number of reviews.

_Moderator 3:_ In the last moderator, the small and medium sized cities are rated significantly higher than larger cities. However, looking at the interaction effects for these two columns, despite being statistically significant, they are so small that they only influence the relationship between the rating and number of reviews minimally. 

**Conclusion**

In conclusion, the moderators all have different impacts on the research question. Having the status superhost gives a higher predicted rating and it is shown that listings that have this status have more reviews. Although the room type does matter for the number of reviews a listing gets (a listing with a "shared room" of "hotel room" has almost half of the reviews an "entire home" or "private room" has), the effect is insignificant and does not influence the relationship between the rating and the number of reviews. Finally, the number of reviews is different per city size. Mostly, the smaller cities get less reviews. However, in the model it is shown that small and medium sized cities are rated significantly higher than larger cities. Despite the significant difference, the effect is small and influences the relationship between the rating and the number of reviews minimally. To conclude, the moderators can impact the relationship between the rating and the number of reviews but is for the most part significantly small.

## Repository overview
This repository consists of various files that will be explained in this section. 

The map source ("src") includes the code that is needed to download, clean and analyze the data. The makefile includes code that can easily run in the command prompt by typing "make". Doing so will automatically run the code in the src code and build the project. From this, two new directories are created: "data" and "gen" (generated). The gen folder consists of two sub-directories, namely "temp" and "output". Gitignore includes files that should be ignore by Git and remain untracked, such as csv files or Rhistory files.

Next, the repository includes a .Rproj file, which contains the options and settings of the project. Moreover, an RMarkdown file is included. This file includes all the tables and plots that were built in the analysis part and includes sections that explain certain phases of the project, such as the data collection and processing parts or the discussion of the results. The RMarkdown file is also knitted as a PDF document and committed to the repository, such that tables and figures that were created in the analysis part can be seen, without the need to run the source code. Finally, this repository has a readme file that contains information about the project, authors, packages used etc. 

## Running instructions
To run the files, [Make](https://tilburgsciencehub.com/get/make) is needed. The directory works with make which should be run in the terminal (Mac users) or in git bash (Windows users). Moreover, [R-studio](https://tilburgsciencehub.com/get/r) is needed to run the R-files. 
To run the code used in the study, the following packages need to be installed first:
```
install.packages("dplyr")
install.packages("ggplot2")
install.packages("googledrive")
install.packages("modelsummary")
install.packages("rlist")
install.packages("webshot")
```

<!---
Explain to potential users how to run/replicate your workflow. Touch upon, if necessary, the required input data, which (secret) credentials are required (and how to obtain them), which software tools are needed to run the workflow (including links to the installation instructions), and how to run the workflow. Make use of subheaders where appropriate.
-->
## Resources
The moderators can influence the relationship between the dependent variable and the independent variable. Each moderator can have a different effect. There are different studies that focus on either city size, room type, superhost or AirBnB in general.

The city size can influence the number of reviews a listing gets because of the people it attracts. Coyle and Yeung (2016) found that AirBnB listings in smaller cities bring more tourism to local communities, who otherwise would not come there. Whereas big and medium cities have listings that are more for economic and administrative functions (Adamiak et al. 2019). Big cities usually have more activities and more noise which, according to Cheng and Jin (2019), can lead to less (positive) reviews. 

The room type can also influence the amount of reviews a listing gets. The size of a city influences the room type. Big and medium cities usually have more hotel rooms, private rooms, or shared rooms, whereas smaller cities have more entire homes (Adamiak et al. 2019). The room type, and the people who chose for a certain room type, can influence the probability that they write a review for the listing.

The status “Superhost” has an effect on the number of reviews and rating a listing gets (Liang et al. 2017). When a host has different qualities, such as a personal profile picture, it gets a superhost badge. The qualities make people trust them more and because of that, they are more likely to leave reviews (Fleischer and Magen 2016; Liang et al. 2017). 

There are multiple studies that focus on reviews on AirBnB. Studies worth mentioning are:
- Bridges, J., & Vásquez, C. (2018). If nearly all Airbnb reviews are positive, does that make them meaningless?. Current Issues in Tourism, 21(18), 2057-2075.
  
In the study, the authors find that AirBnB reviews appear to be highly positive and, therefore, quite similar to one another. If reviews are quite similar, what is the added value that reviews bring to a listing? 
- Ert, E., Fleischer, A., & Magen, N. (2016). Trust and reputation in the sharing economy: The role of personal photos in Airbnb. Tourism management, 55, 62-73.

Fleischer and Magen find that the more trustworthy a host is perceived on their profile picture, the higher the price of the listing can be and the higher the probabilty of the listing being chosen. Furthermore, they find that the host's reputation and their online review score has less effect on the price or booking.
- Liang, S., Schuckert, M., Law, R., & Chen, C. C. (2017). Be a “Superhost”: The importance of badge systems for peer-to-peer rental accommodations. Tourism management, 60, 454-465. 

This study focuses on the label "Superhost", a label that is given by AirBnB for a host with certain qualities, and how this label can impact listings' review volume and ratings. "Superhosts" are more likely to receive reviews and higher ratings and guests are willing to pay more for these listings.
- Coyle, D., & Yeung, T. (2016). Understanding Airbnb in fourteen European cities. The Jean-Jacques Laffont Digital Chair Working Papers, 7088, 1-33.
- Adamiak, C., Szyda, B., Dubownik, A., & García-Álvarez, D. (2019). Airbnb offer in Spain—spatial analysis of the pattern and determinants of its distribution. ISPRS International Journal of Geo-Information, 8(3), 155.

<!---

Point interested users to any related literature and/or documentation.
-->
## About

This study is conducted by project group 2 of the [Data Preparation and Workflow Management course](https://github.com/hannesdatta/course-dprep) of the TISEM department of Tilburg University. 
The project is done in the fall 2021 version of the course. The project was part of a team project performed by Marketing Analytics master students. Professor [Hannes Datta](https://github.com/hannesdatta) contributed by providing helpful feedback during project feedback meetings.
The data used for this project is available at [Inside AirBnB](http://insideairbnb.com/get-the-data.html)
  

## Contributors
Team members: [Doria Wengting Wang](https://github.com/DoriaWW), [Inge Oostveen](https://github.com/IngeOostveen), [Ralph Delsing](https://github.com/RalphGit21), [Paulus Hovens](https://github.com/pphovens), [Wouter Floors](https://github.com/WouterFloors)

