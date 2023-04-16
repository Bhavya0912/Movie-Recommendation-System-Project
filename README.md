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

## Output:
![image](https://user-images.githubusercontent.com/75235293/232290063-b11344fb-0851-4115-9160-0d4751a8aca1.png)
![image](https://user-images.githubusercontent.com/75235293/232290092-30f796c2-4b40-4370-9c20-74e2d7c767f2.png)
![image](https://user-images.githubusercontent.com/75235293/232290113-7ddfc717-66bc-476c-aaac-1b6ed5b46a1a.png)
![image](https://user-images.githubusercontent.com/75235293/232290132-171eda97-ea69-456d-8d13-49fab4b2d2cd.png)
![image](https://user-images.githubusercontent.com/75235293/232290151-31331c1b-1428-4940-8fa7-430085a71c20.png)
![image](https://user-images.githubusercontent.com/75235293/232290162-2f4be00f-e1ce-48f8-8c5d-8e6a8ed42fa2.png)
