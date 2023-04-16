# Movie-Recommendation-System
## Algorithm:
### Step-1: Importing the necessary libraries.
### Step-2: In this project i have imported the numpy and pandas libraries.
### Step-3: Load the credits dataset from kaggle and find the information such as shape and info from the dataset.
### Step-4: Now Load the movies dataset from kaggle and find the shape and info.
### Step-5: Merge the two dataframes with commom column id.
### Step-6: find the mean of vote_average column it will give us the average rating of each movie.
### Step-7: movies having vote count greater than 80% from the list will be taken.
### Step-8: define the function as weighted rating based on the IMDB formula which will return (v/(v+m) * R) + (m/(m+v) * C) where v-vote count ,R-vote average,c-mean vote ,m-minimum votes required to be listed in chart.
### Step-9: Define a new feature 'score' and calculate its value with `weighted_rating()`.
### Step-10: Sort movies based on score calculated above.
### Step-11: Print the top 10 movies.
### Step-12: as per the popularity,budget,revenue we are getting these movies as the highest viewing rate.
## Source Code:
```
import numpy as np
import pandas as pd
df1 = pd.read_csv('credits.csv')
df1.head()
df1.shape
df1.info()
df2 = pd.read_csv('movies.csv')
df2.head()
df2.shape
df2.info()
df1.columns = ['id','title','cast','crew']
df2= df2.merge(df1,on='id')
df2.head()
df2.shape
df2.columns
mean= df2['vote_average'].mean()
mean
mov_grt= df2['vote_count'].quantile(0.8) #movies having vote count greater than 80% from the list will be taken
mov_grt
lists_movies = df2.copy().loc[df2['vote_count'] >= mov_grt]
lists_movies.shape
def weighted_rating(x, mov_grt=mov_grt, mean=mean):
    v = x['vote_count']
    R = x['vote_average']
    return (v/(v+mov_grt) * R) + (mov_grt/(mov_grt+v) * mean) 
 
lists_movies['score'] = lists_movies.apply(weighted_rating, axis=1)
lists_movies.head(3)
lists_movies.shape
lists_movies = lists_movies.sort_values('score', ascending=False)
lists_movies[['title_x', 'vote_count', 'vote_average', 'score']].head(10)
pop= df2.sort_values('popularity', ascending=False)
import matplotlib.pyplot as plt
plt.figure(figsize=(12,4))

plt.barh(pop['title_x'].head(6),pop['popularity'].head(6), align='center',
        color='m')
plt.gca().invert_yaxis()
plt.xlabel("Popularity")
plt.title("Popular Movies" )
df2.columns
pop= df2.sort_values('budget', ascending=False)
import matplotlib.pyplot as plt
plt.figure(figsize=(12,4))

plt.barh(pop['title_x'].head(6),pop['budget'].head(6), align='center',
        color='lightgreen')
plt.gca().invert_yaxis()
plt.xlabel("Popularity")
plt.title("High Budget Movies" )
pop= df2.sort_values('revenue', ascending=False)
import matplotlib.pyplot as plt
plt.figure(figsize=(12,4))

plt.barh(pop['title_x'].head(6),pop['revenue'].head(6), align='center',
        color='lightblue')
plt.gca().invert_yaxis()
plt.xlabel("Popularity")
plt.title("Revenue on Movies" )

```
## Output:
![image](https://user-images.githubusercontent.com/75235293/232290063-b11344fb-0851-4115-9160-0d4751a8aca1.png)
![image](https://user-images.githubusercontent.com/75235293/232290092-30f796c2-4b40-4370-9c20-74e2d7c767f2.png)
![image](https://user-images.githubusercontent.com/75235293/232290113-7ddfc717-66bc-476c-aaac-1b6ed5b46a1a.png)
![image](https://user-images.githubusercontent.com/75235293/232290132-171eda97-ea69-456d-8d13-49fab4b2d2cd.png)
![image](https://user-images.githubusercontent.com/75235293/232290151-31331c1b-1428-4940-8fa7-430085a71c20.png)
![image](https://user-images.githubusercontent.com/75235293/232290162-2f4be00f-e1ce-48f8-8c5d-8e6a8ed42fa2.png)
