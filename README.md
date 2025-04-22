Database Structure  

In this assignment, you will use the following tables:  

players 

games 

scores 

 
    1.  Players table: Information about players. 
        - id (INTEGER, Primary Key) 
        - name (VARCHAR) 
        - join_date (DATE) 

    2.  Games table: Details of games available. 
        - id (INTEGER, Primary Key) 
        - title (VARCHAR) 
        - genre (VARCHAR) 

    3.  Scores table: Tracks scores of players in different games. 
        - id (INTEGER, Primary Key) 
        - player_id (INTEGER, Foreign Key to players) 
        - game_id (INTEGER, Foreign Key to games) 
        - score (INTEGER) 
        - date_played (DATE) 
     

Step 1: Setting Up  

Before you start, make sure your Docker containers are running with PostgreSQL and pgAdmin. Create the tables above using the given structure and insert some sample data to practice with. 

Step 2: The Challenges  

Now, it's time to write some queries to answer the questions below. 

Task 1: List All Players and Their Scores  

Write a query that uses an INNER JOIN to display all players along with the games they have played and their scores. Include the player’s name, game title, and score. 

Task 2: Find High Scorers  

Use GROUP BY and ORDER BY to find the top 3 players with the highest total scores across all games. 

Task 3: Players Who Didn’t Play Any Games  

Use a LEFT OUTER JOIN  to list all players who haven’t played any games yet. 

Task 4: Find Popular Game Genres  

Use GROUP BY and COUNT() to find out which game genre is the most popular among players. 

Task 5: Recently Joined Players  

Write a query to find all players who joined in the last 30 days. Use the WHERE clause to filter by the `join_date`. 

Bonus Task: Players' Favorite Games  

Use JOIN and GROUP BY to find out which game each player has played the most times. Show the player’s name and the game title.