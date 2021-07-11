
# Data Modeling with Postgres Udacity project

## Goal of this project 
The goal of this project is to create an ETL process to extract, transform and load data from existing JSON log and song files to Postgres tables with star schema. This will simplify the whole process of analysing data for data analysts by simpliefied queries from created Postgres tables. My personal goal in this project is to gain experience in building such ETL pipelines.

# Tables structure and datatypes

Star schema which is used in this project enables quickly get needed data with simple SQL queries. Names and data types which are used to create tables listed are below. Fact table contains all metrics of data which is extracted from JSON logs and songs files. Dimention tables contain all information of particular metric from fact table.

> ### Fact table
1. **songplays** - records in log data associated with song plays i.e. records with page NextSong

> - **songplay_id** SERIAL PRIMARY KEY, **start_time BIGINT**, **user_id** INT, **level** VARCHAR, **song_id** VARCHAR, **artist_id** VARCHAR, **session_id** INT, **location** VARCHAR, **user_agent** TEXT

> ### Dimention tables

2. **users** - users in the app

> - **user_id** INT, **first_name** VARCHAR, **last_name** VARCHAR, **gender** VARCHAR, **level** VARCHAR

3. **songs** - songs in music database

> - **song_id** VARCHAR, **title** VARCHAR, **artist_id** VARCHAR, **year** INT, **duration** FLOAT

4. **artists** - artists in music database

> - **artist_id** VARCHAR, **name** VARCHAR, **location** VARCHAR, **latitude** DECIMAL(9,6), **longitude** DECIMAL(9,6)

5. **time** - timestamps of records in **songplays** broken down into specific units

> - **start_time** BIGINT, **hour** INT, **day** INT, **week** INT, **month** INT, **year** INT, **weekday** VARCHAR,


# Datasets

## Song Dataset

This dataset is a subset of real data from the [Million Song Dataset](https://labrosa.ee.columbia.edu/millionsong/).
Example of JSON file in data/songs directory:

{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}

## Log Dataset

This dataset represents activities of users which are then stored in JSON log files.
Example of JSON file in data/logs directory:

{"artist":null,"auth":"Logged In","firstName":"Adler","gender":"M","itemInSession":0,"lastName":"Barrera","length":null,"level":"free","location":"New York-Newark-Jersey City, NY-NJ-PA","method":"GET","page":"Home","registration":1540835983796.0,"sessionId":248,"song":null,"status":200,"ts":1541470364796,"userAgent":"\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.78.2 (KHTML, like Gecko) Version\/7.0.6 Safari\/537.78.2\"","userId":"100"}


# Project Files Structure Description

1. **sql_queries.py** - contains SQL (**CREATE TABLE**, **INSERT INTO**, **DROP TABLE**) statements for each Fact and Dimentions tables

2. **create_tables.py** - executes queries from **sql_queries.py**, creates/connects to DB

3. **test.ipyng** - executes queries **SELECT** (first 5 rows)  of each table to prove, that data inserted correctly 

4. **etl.ipyng** - this file is used for development purposes to analyse datasets before running **etl.py** file

5. **etl.py** - extract transform and load data from logs and songs datasets to created SQL tables


## How to run

Run **create_tables.py** before running **etl.py** to reset your tables. Run **test.ipynb** to confirm your records were successfully inserted into each table.




