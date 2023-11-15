### LESSON 1: SELECT QUERIES
                    
Task  | Answer
------------- | -------------
Find the title of each film   | `SELECT title FROM movies;`
Find the director of each film   | `SELECT director FROM movies;`
Find the title and director of each film  | `SELECT title, director FROM movies;`
Find the title and year of each film | `SELECT title, year FROM movies;`
Find all the information about each film  | `SELECT * FROM movies;`


### LESSON 2: Queries with constraints (Pt. 1) 

Task  | Answer
------------- | -------------
Find the movie with a row ***id*** of 6   | `SELECT * FROM movies WHERE id=6;`
Find the movies released in the ***year***s between 2000 and 2010   | `SELECT * FROM movies WHERE year BETWEEN 2000 AND 2010;`
Find the movies ***not*** released in the ***year***s between 2000 and 2010  | `SELECT * FROM movies WHERE year NOT BETWEEN 2000 AND 2010;`
Find the first 5 Pixar movies and their release ***year*** | `SELECT * FROM movies WHERE id IN (1,2,3,4,5);` `SELECT * FROM movies WHERE id < 6;`


### LESSON 3: Queries with constraints (Pt. 2) 

Task  | Answer
------------- | -------------
Find all the Toy Story movies   | `SELECT * FROM movies WHERE title LIKE'Toy Story%';`
Find all the movies directed by John Lasseter | `SELECT * FROM movies WHERE director='John Lasseter';`
Find all the movies (and director) not directed by John Lasseter | `SELECT * FROM movies WHERE director!='John Lasseter';`
Find all the WALL-* movies | `SELECT * FROM movies WHERE title LIKE 'WALL-_';`
