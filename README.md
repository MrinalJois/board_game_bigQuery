# Board Game Analysis 
## A brief look into the features of a few top board games, using SQL and Tableau.
This projects presents some of the most liked board games along with features like minimum play time, minimum number of players, average rating etc, so that the users can buy their next favourite board game after going through the statistics. Data was taken from [Kaggle](https://www.kaggle.com/datasets/andrewmvd/board-games).

### Oldest board games (in AD)
•	A list of some of the oldest board games (in AD) from the board game dataset:

![image](https://github.com/user-attachments/assets/38f7f0f0-de88-4ff0-99c4-a4c237502a4b)

#### Query
select Name, Year_Published from `board_games.details`
where Year_Published is not null and Year_Published>0
order by Year_Published 
limit 25;




### Top 5 games released every year(2010 to 2022)
### Games with the highest number of user ratings(2010-2022)
### 10 most rated games of all time 
### Top 25 Board games with 2 minimum players
### Top 10 user-rated games
### Highest rated games and the minimum age

