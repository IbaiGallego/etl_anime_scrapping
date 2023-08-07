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




## Scrapping Wikipedia with bs4

I want to create a funnction that extracts information such as director, producer and such. I will run through every link substituting the entry title with the anime title changing the ' ' with '_' using str.replace(). The structure in wikipedia always has a table (html table) where the **'th'** is **'directed by'** or **'produced by'** and the **'td'** is the name of the person. This way I can create a function with a try, except to collect the most part of the 17500 animes in the dataset. I will fisrt try using bs4 (beautiful soup) as it is faster than selenium.

### Process

1. The imports:
    * import pandas as pd
    * from bs4 import BeautifulSoup as bs
    * import pandas as pd (optional: pd.set_option('display.max_columns', None))
    * from joblib import Parallel, delayed
    * import numpy as np
    * imported both tqdm and multiprocessing  but ended up not using them.

    <br>

2. Read the .csv.

3. Created a function that requests the wikipedia url with beautifulsoup using the name of the anime with underscores in stead of spaces to find the director. 

    * It first tries to find the a table whose class can be either 'infobox' or 'infobox infobox_v2'.
    * It then loops through the rows of the table and finds the th with the heather 'directer by'. It is important to note that the spaces are '\xa0' so i replaced them with nothing.
    * When it finds that th it returns the td of said row.
    * The function was protected using a try except and returns 'fallo' for failure and unknnown if it works and it never finds the director.

4. Then I use joblib to parallelize and use 4 nucleus in my computer and add the collumn 'director' by appliying the function to each anime english name.

5. I then safe the datafram to a .csv named 'anime_2.csv'.

6. I repeat the process changing the 'directed by' with 'produced by'.

7. Delete the rows that dont have either the director and the producer.

8. Safe the df as anime_clean.

*Important note: This function could also be used with other inputs like the original name. Some anime don't have athe wikipedia page with the english name. From 17.500 animes i could onnly scrape around a thousand directors and producers resulting in 1759 rows with either director and or producer.*

*commit 4, 5 and 6*

## Scrapping IMDB with selenium

For this part of the project i will create a new database and store the rating from animes into a new df. I will scrape as much as i can from IMDB and later add the data into my anime dataframe.

*commit 7,8 and 9*

Created a jupiter notebook that starts a selenium driver and searches imdb top animations films annd series and scrapes the title, imdb rating, metacritic rating and directors/stars od the 400 first pages. this results in 20.000 rows of animated films.

I then safe the dataframe as 'anime_full.csv' (There was an anime half because the scraping was interrupted at around 13.000 films).

## Cleaning the IMDB

1. Create two functions, one to extract the year and another to remove the imdb indez and year.

2. Create functions to extract directors and stars.

3. Delete unnecessary columns.

4. Clean the votes_imdb function.

5. Create an imdb_trust column where if there are more than 100.000 votes we consider the rating trustworthy.

6. Save as imdb.csv

*commit 10 and 11*

## Combining datasets







