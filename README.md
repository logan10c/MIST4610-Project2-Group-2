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

<img width="511" height="636" alt="image" src="https://github.com/user-attachments/assets/40587a66-2ed5-4599-84bb-9f4a899da02a" />

Model Explanation:

Our model is based on the structure of the NFL, particularly for the 2024 season. The team entity represents one of the thirty-two NFL teams. Each team can have many players, and a player can also have many teams (if a player gets cut or traded), which is shown by a many-to-many relationship. We used the associative entity team_has_player to track the start and end dates of when the player joined each team. The attribute end_date has the ability to be null as a player can be without an end date for a team if he is still playing for that team.
A team also has a stadium, but in some instances, teams share a stadium (NYJ and NYG or LAC and LAR). This is represented by a one-to-many relationship from stadium to team. Throughout the season, stats are recorded to track how a team is performing on a field. We used a one to many relationship between team and seasonStats to represent their connection; a team possesses multiple statistical records, but a specific stat belongs to only one team, that team that it is tracking. Further, a team also has multiple coaches, and coaches can have only one team. Coaches do not get traded during a season, so they cannot be part of multiple teams. This is shown by a one-to-many relationship from team to coaches. Coaches also have a hierarchy—a coach can be the boss of many other coaches, but a coach can only have one boss. This is identified through a one-to-many recursive relationship. Boss_id has the ability to be null since a head coach does not have another coach that is above him.
A team plays 18 regular-season games each year. Therefore, in our model, a team has many games. A game can only have one winner and one loser. This is modeled by two one-to-many relationships. A game must also have referees. A game can have only one referee crew and a referee crew can officiate many games over the season. This is shown by a one to many relationship from refereeCrew to game. A referee Crew can have many referees but a referee can only have one referee crew that they work with. A referee crew also has one chief referee.
Similarly, a game can have more than one broadcaster, and a broadcaster can call more than one game each season. This is yet another many-to-many relationship, which creates the associative entity broadCastCrew, tracking which broadcasters call each game.
Players in the NFL can have mentors throughout the league who help them develop their game. A player can only have one mentor but can have many other players whom they mentor. This is shown by a one-to-many recursive relationship between players. An instance in the attribute can be null since a player does not have to have a mentor. We also modeled the 2024 NFL draft. A player can be only one draft pick, and a draft pick can be only one player, so we showed this relationship using a one-to-one relationship labeled draft pick. The relationship between player and draft pick is non-identifying because of the modality. A draft pick must belong to a certain player, but a player does not have to have an instance of draft pick since players can be undrafted. The college attribute can also be null if a player is from overseas and did not attend a traditional american college. Teams, however, can have more than one draft pick, so to show this relationship, there is a one-to-many from team to draft. Players also play a specific position. We modeled this with a one to many relationship between positions and players, with a position being able to be played by multiple players and a player playing only one position. Although there are times where a player can play multiple positions, each player in the NFL has only one position listed as their primary position.


