# Single Table Design Recipe Template

_Copy this recipe template to design and create a database table from a specification._

## 1. Extract nouns from the user stories or specification

```
# EXAMPLE USER STORY:
# (analyse only the relevant part - here the final line).

As a person who loves movies,
So I can list all my favourite movies
I want to see a list of movies' titles.

As a person who loves movies,
So I can list all my favourite movies
I want to see a list of movies' genres.

As a person who loves movies,
So I can list all my favourite movies
I want to see a list of movies' release year.


Nouns:

id, movie_title, movie_genre, release_year
```

## 2. Infer the Table Name and Columns

Put the different nouns in this table. Replace the example with your own nouns.

| Record                | Properties          |
| --------------------- | ------------------  |
| movies                | movie_title, movie_genre, release_year

Name of the table (always plural): `students` 

Column names: `movie_title`, `movie_genre`, `release_year`

## 3. Decide the column types.

[Here's a full documentation of PostgreSQL data types](https://www.postgresql.org/docs/current/datatype.html).

Most of the time, you'll need either `text`, `int`, `bigint`, `numeric`, or `boolean`. If you're in doubt, do some research or ask your peers.

Remember to **always** have the primary key `id` as a first column. Its type will always be `SERIAL`.

```
# EXAMPLE:

id: SERIAL
movie_title: text
movie_genre: text
release_year: int

```

## 4. Write the SQL.

```sql
-- EXAMPLE
-- file: albums_table.sql

-- Replace the table name, columm names and types.

CREATE TABLE movies (
  id SERIAL PRIMARY KEY,
  movie_title text,
  movie_genre text,
  release_year int
);

--paste query into Table plus
--Refresh page


--INSERT statement used to verify work

INSERT INTO movies (
	movie_title, movie_genre, release_year)
VALUES ('Avatar: Way of the Water', 'Sci-fi', '2023');

```

## 5. Create the table.

```bash
psql -h 127.0.0.1 database_name < albums_table.sql
```

---