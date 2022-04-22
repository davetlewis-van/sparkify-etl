# Sparkify ETL Pipleine

Welcome to our Sparkify ETL pipeline documentation!

## About this project

The purpose of this project is to define and populate an analytics database for Sparkify data analysts to perform song play analysis.

## Getting started with the project

1. Clone or fork the repository.
2. Create a virutal environment and run a requirements.txt command to install dependancies
3. For the jupyter notebook files, run ...
4. For the .py files, run ...

## Source Data

The source data for this project is two collections of JSON files from the Sparkify music streaming app.

### song_data

### log_data

## ETL pipline files

The following files implement the extract, transform, load (ETL) pipline for the Sparkify data model:

- `sql_queries.py` - Contains all of the SQL code used in the pipeline including SQL queries to create and drop the data model tables and insert data into the tables.
- `create_tables.py` - Script to automate the process of deleting ETL tables from the previous run and creating the required tables for the Sparkify data model.
- `etl.ipynb` - Runs the ETL process for a single record in each table. Implements functions to extract data from the `log_data` and `song_data` files, transform the data to the required format for the data schema, and insert the data into the appropriate tables in the Sparkify database.
- `etl.py` - Runs the ETL process on all files in the `log_data` and `song_data` subfolders. Implements functions to extract data from the `log_data` and `song_data` files, transform the data to the required format for the data schema, and insert the data into the appropriate tables in the Sparkify database. - test.ipynb`- Contains tests to ensure that the `INSERT` statments are adding the intended values to tables, and checks for primary keys, column types, and constraints.

## Data Model

Here is the schema of our data model:

### Songplays

Fact table that contains a row for each song played.

| column      | type                     | notes                            |
| ----------- | ------------------------ | -------------------------------- |
| songplay_id | INT                      | Primary key.                     |
| start_time  | TIMESTAMP WITH TIME ZONE | Not null and unique constraints. |
| user_id     | BIGINT                   | Not null constraint.             |
| level       | VARCHAR                  |                                  |
| song_id     | VARCHAR                  |                                  |
| artist_id   | VARCHAR                  |                                  |
| session_id  | INT                      |                                  |
| location    | VARCHAR                  |                                  |
| user_agent  | VARCHAR                  |                                  |

### Users

Dimension table that contains a row for each Sparkify user.

| column     | type    | notes       |
| ---------- | ------- | ----------- |
| user_id    | BIGINT  | Primary key |
| first_name | VARCHAR |             |
| last_name  | VARCHAR |             |
| gender     | VARCHAR |             |
| level      | VARCHAR |             |

### Songs

Dimension table that contains a row for each song in the Sparkify catalog.

| column    | type    | notes                |
| --------- | ------- | -------------------- |
| song_id   | VARCHAR | Primary key.         |
| title     | VARCHAR | Not null constraint. |
| artist_id | VARCHAR |                      |
| year      | INT     |                      |
| duration  | NUMERIC | Not null constraint. |

### Artists

Dimension table that contains a row for each artist in the Sparkify catalog.

| column    | type             | notes                |
| --------- | ---------------- | -------------------- |
| artist_id | VARCHAR          | Primary key.         |
| name      | VARCHAR          | Not null constraint. |
| location  | VARCHAR          |                      |
| latitude  | DOUBLE PRECISION |                      |
| longitude | DOUBLE PRECISION |                      |

### Time

Dimension table that contains a row for each timestamp, with columns with pre-prosessed dimensions including day, month, and year to simplify and optimize date-based analytic queries.

| column     | type                     | notes        |
| ---------- | ------------------------ | ------------ |
| start_time | TIMESTAMP WITH TIME ZONE | Primary key. |
| hour       | INT                      |              |
| day        | INT                      |              |
| week       | INT                      |              |
| month      | INT                      |              |
| year       | INT                      |              |
| weekday    | INT                      |              |
