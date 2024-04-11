# CIS 421 Project - Video Game Marketplace Database
## Contributors
- Alex Parsons, Dan Hallanger
## Overview
This database project serves as a gaming marketplace platform, providing users with a platform to buy, and discuss games. Users can browse a variety of games, purchase them, review them, and interact with other users through discussion threads. The project includes tables for developers, genres, user accounts, games, reviews, transactions, threads, and more.

## Features
- Users can register and create accounts with various payment methods.
- Users can browse, review, and purchase games.
- Users can participate in discussion threads related to games.
- Users can buy and sell in-game items.
- Detailed information about games, including minimum and recommended system requirements, is provided.
- Users can interact with each other through reviews and threads.

## Database Schema
The database consists of the following tables:
- **Developer:** Stores information about game developers.
- **Genre:** Contains various game genres.
- **UserAcct:** Stores user account information.
- **Game:** Contains details about games, including developer, genre, price, release date, and system requirements.
- **Reviews:** Stores user reviews for games.
- **Transactions:** Records user transactions for purchasing games.
- **Threads:** Contains discussion threads and posts created by users.
- **Library:** Records the games owned by users.

## Setup
To set up the database, execute the provided SQL script in your SQLite database management tool. Ensure that foreign key constraints are enabled to maintain referential integrity.
We used VSCode with three plugins to help with SQLite: SQLite, SQLite Viewer, and SQLite3 Editor.

## Sample Queries
Here are some sample queries you can execute on the database:
1. Retrieve the names of games along with their minimum and recommended requirements:
   
    ```
    SELECT Game.Name, Minimum_Requirements.MinStorage, Minimum_Requirements.MinCPU, Minimum_Requirements.MinRam, Recommended_Requirements.RecStorage, Recommended_Requirements.RecCPU, Recommended_Requirements.RecRam
    FROM Game
    INNER JOIN Minimum_Requirements ON Game.MinimumRequirementID = Minimum_Requirements.MinimumRequirementID
    INNER JOIN Recommended_Requirements ON Game.RecommendedRequirementID = Recommended_Requirements.RecommendedRequirementsID;
    ```
2. Get the total number of games sold for each developer:
    ```
    SELECT Developer.Name, SUM(Game.NumSold) AS TotalGamesSold
    FROM Developer
    INNER JOIN Game ON Developer.DevID = Game.DevID
    GROUP BY Developer.Name;
   ```
