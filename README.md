# ANIME ETL

![Alt Text](images/cover.png)

### sources: 

* Kaggle: https://www.kaggle.com/datasets/hernan4444/anime-recommendation-database-2020

* IMDB: https://www.imdb.com/search/title/?genres=Animation&explore=title_type%2Cgenres&ref_=ft_popular_2

* Wikipedia: https://www.wikipedia.org/

## Introduction

For this project I will get a kraggle csv containing information on animes and use scrapping techniques to complete th information. I will define a function that scraps the data from wikipedia and then annother function for IMDB. I will the upload my dataset to mongoDB (SQL if I don´t have time). 

## The Kraggle database

I am going to delete informationn that is not relevant to my study. This dataset is very complete. It has all the information needed. For the sake of the practice i will delete information from the table and i will later attempt to scrap it myself.

1. standardice the column names. (lowercase and '_')
2. Delete extra columns (eg. I have 10 column depicting the number of members scoring from 1 to 10 and a rating column, the avg. I will keep the rating)







## Scrapping Wikipedia

I want to create a funnction that extracts information such as director, producer and such. I will run through every link substituting the entry title with the anime title changing the ' ' with '_' using str.replace(). The structure in wikipedia always has a table (html table) where the **'th'** is **'directed by'** or **'produced by'** and the **'td'** is the name of the person. This way I can create a function with a try, except to collect the most part of the 17500 animes in the dataset. I will fisrt try using bs4 (beautiful soup) as it is faster than selenium.

### Process

1. The imports:
    * import pandas as pd
    * from bs4 import BeautifulSoup as bs
    * import pandas as pd (optional: pd.set_option('display.max_columns', None))
    * import multiprocessing as mp (for paralellization)

    <br>

2. Read the .csv
3. 



