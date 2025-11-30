# MIST4610-Project2-Group-2
SQL Project 2 - 2024 NFL season
- Logan Collins
- Rett Sams
- Eli Burt
- Noelle Rocheteau

Description:
The objective of this project is to design, model, and implement a comprehensive relational database for the 2024 NFL season. The core focus of the system is the NFL Team entity, which is connected to related entities such as Players, Coaches, Referees, Broadcasters, and other operational components of the league.
The project focuses on:
- Developing a complete Entity-Relationship model that accurately represents the structure and interactions of NFL organizations during the 2024 season.


- Populating the database with detailed and realistic season data, including team rosters, game schedules, officiating crews, broadcast assignments, and statistical outcomes.


- Writing and executing SQL queries to efficiently retrieve meaningful insights from the database, such as team performance metrics, player statistics, and game reporting details.
- Creating Data Visualizations to effectively and easily convey the information contained within our database.

By the end of the project, we will have a fully functioning database system that provides valuable visibility into the dynamics and analytics of the 2024 NFL season.
Note that we could not find complete accurate data for Broadcasting Crews and Player Start +  End Dates.

Data Model:



Model Explanation:

- Our model is based on the structure of the NFL, particularly for the 2024 season. The team entity represents one of the thirty-two NFL teams. Each team can have many players, and a player can also have many teams (if a player gets cut or traded), which is shown by a many-to-many relationship. We used the associative entity team_has_player to track the start and end dates of when the player joined each team. The attribute end_date has the ability to be null as a player can be without an end date for a team if he is still playing for that team.

- A team also has a stadium, but in some instances, teams share a stadium (NYJ and NYG or LAC and LAR). This is represented by a one-to-many relationship from stadium to team. Throughout the season, stats are recorded to track how a team is performing on a field. We used a one to many relationship between team and seasonStats to represent their connection; a team possesses multiple statistical records, but a specific stat belongs to only one team, that team that it is tracking. Further, a team also has multiple coaches, and coaches can have only one team. Coaches do not get traded during a season, so they cannot be part of multiple teams. This is shown by a one-to-many relationship from team to coaches. Coaches also have a hierarchy—a coach can be the boss of many other coaches, but a coach can only have one boss. This is identified through a one-to-many recursive relationship. Boss_id has the ability to be null since a head coach does not have another coach that is above him.

- A team plays 18 regular-season games each year. Therefore, in our model, a team has many games. A game can only have one winner and one loser. This is modeled by two one-to-many relationships. A game must also have referees. A game can have only one referee crew and a referee crew can officiate many games over the season. This is shown by a one to many relationship from refereeCrew to game. A referee Crew can have many referees but a referee can only have one referee crew that they work with. A referee crew also has one chief referee.
Similarly, a game can have more than one broadcaster, and a broadcaster can call more than one game each season. This is yet another many-to-many relationship, which creates the associative entity broadCastCrew, tracking which broadcasters call each game.

- Players in the NFL can have mentors throughout the league who help them develop their game. A player can only have one mentor but can have many other players whom they mentor. This is shown by a one-to-many recursive relationship between players. An instance in the attribute can be null since a player does not have to have a mentor. We also modeled the 2024 NFL draft. A player can be only one draft pick, and a draft pick can be only one player, so we showed this relationship using a one-to-one relationship labeled draft pick. The relationship between player and draft pick is non-identifying because of the modality. A draft pick must belong to a certain player, but a player does not have to have an instance of draft pick since players can be undrafted. The college attribute can also be null if a player is from overseas and did not attend a traditional american college. Teams, however, can have more than one draft pick, so to show this relationship, there is a one-to-many from team to draft. Players also play a specific position. We modeled this with a one to many relationship between positions and players, with a position being able to be played by multiple players and a player playing only one position. Although there are times where a player can play multiple positions, each player in the NFL has only one position listed as their primary position.

Data Dictionary:

Table: player

<img width="589" height="504" alt="image" src="https://github.com/user-attachments/assets/20e56a06-6a89-454f-bab3-1a85b1db947b" />

Table: team_has_player

<img width="477" height="232" alt="image" src="https://github.com/user-attachments/assets/24592d3a-b7f7-4e2b-9733-d0fd87f1af38" />

Table: stadium

<img width="537" height="262" alt="image" src="https://github.com/user-attachments/assets/47f0b76e-8556-4cb3-952d-f410e6994af2" />

Table: coach

<img width="573" height="261" alt="image" src="https://github.com/user-attachments/assets/978d614e-5058-4a4c-a8f9-77fbd992af82" />

Table: team

<img width="487" height="219" alt="image" src="https://github.com/user-attachments/assets/483c8735-7147-43af-8fac-63be9fc0f995" />

Table: draftPick

<img width="497" height="226" alt="image" src="https://github.com/user-attachments/assets/c480b757-7549-4bf5-8ce7-e446efaf2a85" />

Table: game

<img width="570" height="463" alt="image" src="https://github.com/user-attachments/assets/cf4bfc7b-94cf-4d05-8f53-98c4afb5a937" />

Table: refereeCrew

<img width="515" height="213" alt="image" src="https://github.com/user-attachments/assets/c33b923c-1246-42bd-8885-143c78898246" />

Table: referee

<img width="559" height="291" alt="image" src="https://github.com/user-attachments/assets/ccbe32fa-c7b6-49b1-806f-4e5d562fd013" />

Table: broadcastCrew

<img width="514" height="179" alt="image" src="https://github.com/user-attachments/assets/b30d29df-5ed2-40a6-b22f-7f2bc23a8a48" />

Table: broadcaster

<img width="600" height="224" alt="image" src="https://github.com/user-attachments/assets/4c13101a-1a8b-441f-b6dd-63c9a02f26f4" />

Table: position

<img width="654" height="180" alt="image" src="https://github.com/user-attachments/assets/8cd22d4f-b786-4edf-8df4-b85df33314b8" />

Table: seasonStats

<img width="695" height="237" alt="image" src="https://github.com/user-attachments/assets/62e4bce9-494a-415e-8dff-bcb00a2b50b4" />





