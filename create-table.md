```sql

Create table Players, Games, Scores


CREATE TABLE Players (
    id INTEGER PRIMARY KEY,
    name VARCHAR(255),
    join_date DATE
);

CREATE TABLE Games (
    id INTEGER PRIMARY KEY,
    title VARCHAR(100),
    genre VARCHAR(100)
);

CREATE TABLE Scores (
    id INTEGER PRIMARY KEY,
    player_id INT NOT NULL,
    game_id INT NOT NULL,
    score INT NOT NULL,
    date_played DATE NOT NULL,
    FOREIGN KEY (player_id) REFERENCES Players(id),
    FOREIGN KEY (game_id) REFERENCES Games(id)
);


Insert data into tables


INSERT INTO Players (id, name, join_date) VALUES 
(1, 'Carmelo', '2025-04-22'),
(2, 'Vittorio', '2021-03-12'),
(3, 'Angelica', '2023-04-18'),
(4, 'Isabella', '2021-03-31'),
(5, 'Alexander', '2023-02-02'),
(6, 'Joe', '2025-04-22');

INSERT INTO Games (id, title, genre) VALUES
(1, 'Galactic Wars', 'Shooter'),
(2, 'Treasure Hunt', 'Adventure'),
(3, 'Tokio Drift', 'Racing'),
(4, 'Puzzle Puzzly no way', 'Puzzle'),
(5, 'Battle Royal 5.0', 'Action');

INSERT INTO Scores (id, player_id, game_id, score, date_played) VALUES
(1, 1, 1, 4200, '2025-04-21'),
(2, 2, 2, 3800, '2021-04-01'),
(3, 3, 3, 4500, '2023-05-10'),
(4, 4, 4, 3900, '2021-04-10'),
(5, 5, 5, 5100, '2023-02-20'),
(6, 1, 3, 4700, '2025-04-22'),
(7, 2, 1, 3600, '2021-04-03'),
(8, 3, 4, 4300, '2023-06-01'),
(9, 4, 2, 4000, '2021-05-05'),
(10, 5, 1, 5200, '2023-03-01');


List all players and their scores

SELECT Players.name, Games.title, Scores.score
FROM Scores
INNER JOIN Players ON Scores.player_id = Players.id
INNER JOIN Games ON Scores.game_id = Games.id;


Top 3 Players by Total Score

SELECT Players.name,
SUM(Scores.score) AS total_score
FROM Scores
INNER JOIN Players ON Scores.player_id = Players.id
GROUP BY Players.name
ORDER BY total_score DESC
LIMIT 3;

Players who have not played any game

SELECT Players.name
FROM Players
LEFT OUTER JOIN Scores ON Players.id = Scores.player_id
WHERE Scores.id IS NULL;


Most popular game

SELECT Games.genre, COUNT(Scores.id) AS games_played
FROM Scores
INNER JOIN Games ON Scores.game_id = Games.id
GROUP BY Games.genre
ORDER BY games_played DESC
LIMIT 1;


Player who joined in the last 30 days

SELECT Players.name, Players.join_date
FROM Players
WHERE Players.join_date >= CURRENT_DATE - INTERVAL '30 days';
