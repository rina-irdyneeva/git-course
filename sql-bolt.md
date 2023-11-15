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


### LESSON 4: Filtering and sorting Query results

Task  | Answer
------------- | -------------
List all directors of Pixar movies (alphabetically), without duplicates   | `SELECT DISTINCT director FROM movies ORDER BY director;'`
List the last four Pixar movies released (ordered from most recent to least) | `SELECT * FROM movies ORDER BY year DESC LIMIT 4;`
List the first five Pixar movies sorted alphabetically | `SELECT * FROM movies ORDER BY title LIMIT 5;`
List the next five Pixar movies sorted alphabetically | `SELECT * FROM movies ORDER BY title LIMIT 5 OFFSET 5;`


### LESSON 5: Review: Simple SELECT Queries

Task  | Answer
------------- | -------------
List all the Canadian cities and their populations   | `SELECT * FROM north_american_cities WHERE country='Canada';'`
Order all the cities in the United States by their latitude from north to south | `SELECT * FROM north_american_cities WHERE country='United States' ORDER BY latitude DESC;`
List all the cities west of Chicago, ordered from west to east | `SELECT * FROM north_american_cities WHERE longitude <-87.629798 ORDER BY longitude;`
List the two largest cities in Mexico (by population) | `SELECT * FROM north_american_cities WHERE country='Mexico' ORDER BY population DESC LIMIT 2;`
List the third and fourth largest cities (by population) in the United States and their population | `SELECT * FROM north_american_cities WHERE country='United States' ORDER BY population DESC LIMIT 2 OFFSET 2;`


### LESSON 6: Multi-table queries with JOINs

Task  | Answer
------------- | -------------
Find the domestic and international sales for each movie   | `SELECT * FROM movies LEFT JOIN boxoffice ON movies.id=boxoffice.movie_id;`
Show the sales numbers for each movie that did better internationally rather than domestically | `SELECT * FROM movies LEFT JOIN boxoffice ON movies.id=boxoffice.movie_id WHERE boxoffice.international_sales > boxoffice.domestic_sales;`
List all the movies by their ratings in descending order | `SELECT title, rating FROM movies LEFT JOIN boxoffice ON movies.id=boxoffice.movie_id ORDER BY boxoffice.rating DESC;`


### LESSON 7: OUTER JOINs

Task  | Answer
------------- | -------------
Find the list of all buildings that have employees   | `SELECT DISTINCT building FROM employees;`
Find the list of all buildings and their capacity | `SELECT * FROM buildings;`
List all buildings and the distinct employee roles in each building (including empty buildings) | `SELECT DISTINCT building_name, role FROM buildings LEFT JOIN employees ON building_name = building;` 


### LESSON 8: A short note on NULLs

Task  | Answer
------------- | -------------
Find the name and role of all employees who have not been assigned to a building   | `SELECT name, role FROM employees WHERE building IS NULL;`
Find the names of the buildings that hold no employees | `SELECT DISTINCT building_name FROM buildings LEFT JOIN employees ON building_name = building WHERE role IS NULL;` 


### LESSON 9: Queries with expressions

Task  | Answer
------------- | -------------
List all movies and their combined sales in ***millions*** of dollars   | `SELECT title, (domestic_sales + international_sales) / 1000000 AS gross_sales_millions FROM movies JOIN boxoffice ON movies.id = boxoffice.movie_id;`
List all movies and their ratings ***in percent*** | `SELECT title, rating * 10 AS rating_percent FROM movies JOIN boxoffice ON movies.id = boxoffice.movie_id;`
List all movies that were released on even number years | `SELECT title, year FROM movies WHERE year % 2 = 0;` 


### LESSON 10: Queries with aggregates (Pt. 1)

Task  | Answer
------------- | -------------
Find the longest time that an employee has been at the studio   | `SELECT MAX(years_employed) as Max_years_employed FROM employees;`
For each role, find the average number of years employed by employees in that role | `SELECT role, AVG(years_employed) as Average_years_employed FROM employees GROUP BY role;`
Find the total number of employee years worked in each building | `SELECT building, SUM(years_employed) as Total_years_employed FROM employees GROUP BY building;` 


### LESSON 11: Queries with aggregates (Pt. 2)

Task  | Answer
------------- | -------------
Find the number of Artists in the studio (without a ***HAVING*** clause)   | `SELECT role, COUNT(*) as Number_of_artists FROM employees WHERE role = "Artist";`
Find the number of Employees of each role in the studio | `SELECT role, COUNT(*) FROM employees GROUP BY role;`
Find the total number of years employed by all Engineers | `SELECT role, SUM(years_employed)FROM employees GROUP BY role HAVING role = "Engineer";` 


### LESSON 12: Order of execution of a Query

Task  | Answer
------------- | -------------
Find the number of movies each director has directed   | `SELECT director, COUNT(id) as Num_movies_directed FROM movies GROUP BY director;`
Find the total domestic and international sales that can be attributed to each director | `SELECT director, SUM(domestic_sales + international_sales) as Cumulative_sales_from_all_movies FROM movies INNER JOIN boxoffice ON movies.id = boxoffice.movie_id GROUP BY director;` 


### LESSON 13: Inserting rows

Task  | Answer
------------- | -------------
Add the studio's new production, ***Toy Story 4*** to the list of movies (you can use any director)   | `INSERT INTO movies VALUES (4, "Toy Story 4", "Lee Lasseter", 2015, 90);`
Toy Story 4 has been released to critical acclaim! It had a rating of ***8.7***, and made ***340 million domestically*** and ***270 million internationally***. Add the record to the BoxOffice table. | `INSERT INTO boxoffice VALUES (4, 8.7, 340000000, 270000000);`


### LESSON 14: Updating rows

Task  | Answer
------------- | -------------
The director for A Bug's Life is incorrect, it was actually directed by ***John Lasseter***   | `UPDATE movies SET director = "John Lasseter" WHERE id = 2;`
The year that Toy Story 2 was released is incorrect, it was actually released in ***1999*** | `UPDATE movies SET year = 1999 WHERE id = 3;`
Both the title and director for Toy Story 8 is incorrect! The title should be "Toy Story 3" and it was directed by ***Lee Unkrich*** | `UPDATE movies SET title = "Toy Story 3", director = "Lee Unkrich" WHERE id = 11;` 
