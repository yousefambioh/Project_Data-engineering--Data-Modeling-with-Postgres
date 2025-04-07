# Project_Data-engineering--Data-Modeling-with-Postgres
 Sparkify Music Streaming Data Analysis


This project involves building a data pipeline to analyze user activity and song plays on Sparkify, a music streaming app. The data is stored in JSON log files, and the project leverages PostgreSQL to build a star schema for analysis. The ETL (Extract, Transform, Load) pipeline, implemented in Python, processes song, artist, user, and songplay data to populate the database.

Project Structure:
sql_queries.py: Contains SQL queries for building tables, inserting data, and selecting song and artist IDs based on song name, artist name, and song length.

create_tables.py: Connects to PostgreSQL, creates the sparkify database if it doesn't exist, and builds the tables using SQL queries from sql_queries.py.

etl.py: Processes JSON files (song, artist, user, and songplay data) and loads the data into the database. Uses the Pandas library for some ETL operations.

etl.ipynb: A Jupyter notebook implementing the same ETL logic as etl.py but for processing a single song and log file.

test.ipynb: Contains SQL queries for testing the results of the ETL process and verifying the contents of the tables.

How to Run:
To create or reset the schema (drop and rebuild tables):

nginx
Copy
Edit
python create_tables.py
To run the ETL process and load data into the database:

nginx
Copy
Edit
python etl.py
To test the results using some sample queries (from test.ipynb):

Combine artist name and song title:

sql
Copy
Edit
SELECT name, title FROM songs NATURAL JOIN artists LIMIT 5;
View rows from all 5 tables:

sql
Copy
Edit
SELECT * FROM songplays
JOIN songs ON songplays.song_id = songs.song_id
JOIN artists ON songplays.artist_id = artists.artist_id
JOIN time ON songplays.start_time = time.start_time
JOIN users ON songplays.user_id = users.user_id
LIMIT 5;
Check for song IDs in songplays:

sql
Copy
Edit
SELECT * FROM songplays WHERE song_id != 'None' LIMIT 5;
This project is intended to support the Sparkify analytics team in understanding user interactions with the platform, particularly focusing on songplays and related metadata.
