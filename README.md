# Board Game Analysis 
## A brief look into the features of a few top board games, using SQL and Tableau.
This projects presents some of the most liked board games along with features like minimum play time, minimum number of players, average rating etc, so that the users can buy their next favourite board game after going through the statistics. Data was taken from [Kaggle](https://www.kaggle.com/datasets/andrewmvd/board-games).

### Oldest board games (in AD)
•	A list of some of the oldest board games (in AD) from the board game dataset:

![image](https://github.com/user-attachments/assets/38f7f0f0-de88-4ff0-99c4-a4c237502a4b)

#### Query
```
select Name, Year_Published from `board_games.details`
where Year_Published is not null and Year_Published>0
order by Year_Published 
limit 25;
```
### Top 5 games released every year(2010 to 2022)
•	Top 5 games released every year based on the number of user ratings, along with their avg ratings, min and max players, and play time from 2010 to 2022
![image](https://github.com/user-attachments/assets/ec18fb9f-5dbd-4e7f-adff-32277d48876e)
![image](https://github.com/user-attachments/assets/55d4b301-74e6-4a23-93e3-c10ec537ef22)
![image](https://github.com/user-attachments/assets/52a1bc3b-8d46-463a-a502-d0afb0e3de7e)
![image](https://github.com/user-attachments/assets/b910ef26-c256-4319-9a22-3f0af89e93bf)
#### Query
```
select Name, Year_Published, Users_Rated,Rating_Average,Min_Players,Max_Players,Play_Time 
from( select  Name, Year_Published, Users_Rated,
dense_rank()over(partition by Year_Published order by Users_Rated desc) as top,
Rating_Average,Min_Players,Max_Players,Play_Time
from `board_games.details`)t
where top<=5 and Year_Published >=2010
order by Year_Published, Users_Rated desc;
```

### Games with the highest number of user ratings(2010-2022)
•	Games with the highest number of user ratings in 2010-2022, a graphical representation using Tableau
![image](https://github.com/user-attachments/assets/2298fd09-99f6-4335-9f9b-43f1a5ad9da5)

### 10 most rated games of all time
•	Top 10 most rated games of all time along with their avg rating, min and max players
![image](https://github.com/user-attachments/assets/36e5ecf9-5262-4982-81bf-b4312756e7af)

#### Query
```
select Name, Users_Rated, Year_Published, Rating_Average,Min_Players,Max_Players from(
select Name, Users_Rated,Year_Published,Rating_Average, Min_Players,Max_Players from `board_games.details`
group by Users_Rated, Name,Year_Published, Rating_Average,Min_Players,Max_Players)t 
order by Users_Rated desc
limit 10;
```
### Top 25 Board games with 2 minimum players
•	 Top 25 Board games where minimum number of players is 2, along with their playtime, average rating
![image](https://github.com/user-attachments/assets/abd9d0fd-e5d8-4f4d-b2e5-eb0e20855271)
![image](https://github.com/user-attachments/assets/c5dfdba9-4f80-4eb0-ae69-a8f985a971dd)
#### Query
```
select Name,Users_Rated,Rating_Average,Min_Players,Max_Players,Play_Time 
from `board_games.details`
where Min_Players =2
Order by Users_Rated desc
limit 25;
```
### Top 10 user-rated games
•	Top 10 user-rated games and the minimum number of players, a graphical representation using Tableau
![image](https://github.com/user-attachments/assets/3486af9a-4112-4681-bec2-450d6b71d1e4)

### Highest rated games and the minimum age
•	Highest rated games and the minimum age, a graphical representation using Tableau
![image](https://github.com/user-attachments/assets/de97de25-e8c3-4e94-983f-f26c3fda4b88)
![image](https://github.com/user-attachments/assets/ed8297eb-7179-4314-b3ac-108b286c06c6)



