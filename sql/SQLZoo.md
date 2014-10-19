# SQLZoo SQL TUTORIAL AND QUIZZES

### [http://sqlzoo.net/wiki/Main_Page](http://sqlzoo.net/wiki/Main_Page)

## SELECT basics

Show the population of Germany

```sql
SELECT population FROM world
  WHERE name = 'Germany'
```

The query shows the population density population/area for each country WHERE the area is over 5,000,000 km2.

```sql
SELECT name, population/area FROM world
  WHERE area > 5000000
```

Show the name and per capita gdp: gdp/population for each country WHERE the area is over 5,000,000 km2

```sql
SELECT name, gdp/population FROM world
  WHERE area > 5000000
```

We use AND to ensure that two or more conditions hold true.
Show the name and continent WHERE the area is less than 2000 and the gdp is more than 5000000000

```sql
SELECT name , continent
  FROM world
  WHERE area < 2000
  AND gdp > 500000000
```

Checking a list The word IN allows us to check if an item is in a list. The example shows the name and population for the countries 'Ireland', 'Iceland' and 'Denmark'

```sql
SELECT name, population FROM world
  WHERE name IN ('Ireland', 'Iceland', 'Denmark')
```

What are the countries beginning with G? The word LIKE permits pattern matching - % is the wildcard. The examples shows countries beginning with D

```sql
SELECT name FROM world
  WHERE name LIKE 'D%'
```

Which countries are not too small and not too big? Show the country and the area for countries with an area between 200000 and 250000. BETWEEN allows range checking - note that it is inclusive.

```sql
SELECT name, area FROM world
  WHERE area BETWEEN 250000 AND 300000
```

Show the country and the area for countries with an area between 200000 and 250000. BETWEEN allows range checking - note that it is inclusive.

```sql
SELECT name, area FROM world
  WHERE area BETWEEN 250000 AND 300000
```

## SELECT FROM WORLD Tutorial

Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.

```sql
SELECT name FROM world
  WHERE population>=200000000
```

Give the name and the per capita GDP for those countries with a population of at least 200 million.

```sql
SELECT name, gdp/population FROM world
  WHERE population >= 200000000
```

Show the name and population in millions for the countries of the continent 'South America'. Divide the population by 1000000 to get population in millions.

```sql
SELECT name,population/1000000 FROM world
  WHERE continent = 'South America'
```

Show the name and population for 'France', 'Germany', 'Italy'

```sql
SELECT name,population FROM world
  WHERE name IN ('France','Germany','Italy')
```

Show the countries which have a name that includes the word 'United'

```sql
SELECT name FROM world
  WHERE name LIKE '%United%'
```

Shows the year,subject and winner FROM the nobel table for the year 1960

```sql
SELECT yr, subject, winner
  FROM nobel
  WHERE yr = 1960
```




## SELECT FROM Nobel Tutorial

Show who won the 1962 prize for Literature.

```sql
SELECT winner
  FROM nobel
  WHERE yr = 1962
  AND subject = 'Literature'
```

Show the year and subject that won 'Albert Einstein' his prize.

```sql
SELECT yr,subject FROM nobel
  WHERE winner = 'Albert Einstein'
```

Give the name of the 'Peace' winners since the year 2000, including 2000.

```sql
SELECT winner FROM nobel
  WHERE subject ='Peace'
  AND yr >=2000
```

Show all details (yr, subject, winner) of the Literature prize winners for 1980 to 1989 inclusive.

```sql
SELECT yr,subject,winner FROM nobel
  WHERE subject='Literature'
  AND yr BETWEEN 1980 AND 1989
```

Show all details of the presidential winners: ('Theodore Roosevelt', 'Woodrow Wilson', 'Jed Bartlet', 'Jimmy Carter')

```sql
SELECT * FROM nobel
 WHERE winner IN ('Theodore Roosevelt',
                  'Woodrow Wilson',
                  'Jed Bartlet',
                  'Jimmy Carter')
```

Show the winners with first name John

```sql
SELECT winner FROM nobel
  WHERE winner LIKE 'John%'
```

In which years was the Physics prize awarded but no Chemistry prize.

```sql
SELECT DISTINCT yr FROM nobel
  WHERE subject = 'Physics'
  AND yr NOT IN (SELECT DISTINCT yr FROM nobel
                 WHERE subject='Chemistry')
```

Pick the code which shows the name of winner's names beginning with C and ending in n

```sql
SELECT winner FROM nobel
  WHERE winner LIKE 'C%'
  AND winner LIKE '%n'
```

Select the code that shows how many Chemistry awards were given between 1950 and 1960

```sql
SELECT COUNT(subject) FROM nobel
  WHERE subject = 'Chemistry'
  AND yr BETWEEN 1950 AND 1960
```

Pick the code that shows the amount of years WHERE no Medicine awards were given

```sql
SELECT COUNT(DISTINCT yr) FROM nobel
  WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel
                   WHERE subject = 'Medicine')
```

```sql
SELECT subject, winner FROM nobel
  WHERE winner LIKE 'Sir%'
  AND yr LIKE '196%'
```
| Subject  | Winner          |
|----------|-----------------|
| Medicine | Sir John Eccles |
| Medicine | Sir Frank Macfarlane Burnet |

Select the code which would show the year when neither a Physics or Chemistry award was given

```sql
SELECT yr FROM nobel
  WHERE yr NOT IN(SELECT yr FROM nobel
                  WHERE subject IN ('Chemistry','Physics'))
```

Select the code which shows the years when a Medicine award was given but no Peace or Literature award was

```sql
SELECT DISTINCT yr FROM nobel
  WHERE subject='Medicine'
  AND yr NOT IN(SELECT yr FROM nobel
                WHERE subject='Literature')
  AND yr NOT IN (SELECT yr FROM nobel
                 WHERE subject='Peace')
```

```sql
SELECT subject, COUNT(subject)
  FROM nobel
  WHERE yr ='1960'
  GROUP BY subject
```
| Subject | COUNT(Subject) |
|---------|----------------|
| Chemistry | 1 |
| Literature | 1 |
| Medicine | 2 |
| Peace | 1 |
| Physics | 1 |


## SUM and COUNT

Show the total population of the world.
world(name, continent, area, population, gdp)

```sql
SELECT SUM(population) FROM world
```

List all the continents - just once each.

```sql
SELECT DISTINCT continent FROM world
```

Give the total GDP of Africa

```sql
SELECT SUM(gdp) FROM world
  WHERE continent = 'Africa'
```

How many countries have an area of at least 1000000

```sql
SELECT COUNT(name) FROM world
  WHERE area>= 1000000
```

What is the total population of ('France','Germany','Spain')

```sql
SELECT SUM(population) FROM world
  WHERE name IN('France','Germany','Spain');
```

For each continent show the continent and number of countries.

```sql
SELECT continent,COUNT(name) FROM world
  GROUP BY continent
```

For each continent show the continent and number of countries with populations of at least 10 million.

```sql
SELECT continent,COUNT(name) FROM world
  WHERE population>=10000000
  GROUP BY continent
```

List the continents that have a total population of at least 100 million.

```sql
SELECT continent FROM world
  GROUP BY continent
  HAVING SUM(population) >= 100000000
```

Select the statement that shows the SUM of population of all countries in 'Europe'

```sql
SELECT SUM(population) FROM bbc
  WHERE region = 'Europe'
```

Select the statement that shows the number of countries with population smaller than 150000

```sql
SELECT COUNT(name) FROM bbc
  WHERE population < 150000
```

Select the full set of SQL aggregate functions

```sql
AVG(), COUNT(), FIRST(), LAST(), MAX(), MIN(), SUM()
```

```sql
SELECT region, SUM(area)
  FROM bbc
  WHERE SUM(area) > 15000000
  GROUP BY region
```

No result due to invalid use of the WHERE function

Select the statement that shows the average population of 'Poland', 'Germany' and 'Denmark'

```sql
SELECT AVG(population) FROM bbc
  WHERE name IN ('Poland', 'Germany', 'Denmark')
```

Select the statement that shows the medium population density of each region

```sql
SELECT region, SUM(population)/SUM(area) AS density FROM bbc
  GROUP BY region
```

Select the statement that shows the name and population density of the country with the largest population

```sql
SELECT name, population/area AS density FROM bbc
  WHERE population = (SELECT MAX(population) FROM bbc)
```

## The JOIN operation

Show matchid and player name for all goals scored by Germany. teamid = 'GER'

```sql
SELECT matchid,player FROM goal
  WHERE teamid = 'GER'
```

Show id, stadium, team1, team2 for game 1012

```sql
SELECT id,stadium,team1,team2
  FROM game
  WHERE id = 1012
```

You can combine the two steps into a single query with a JOIN. You will get all the game details and all the goal details if you use

```sql
SELECT *
  FROM game JOIN goal ON (id=matchid)
```

Show the player, teamid and mdate and for every German goal. teamid='GER'

```sql
SELECT player,teamid,mdate
  FROM game JOIN goal ON (id=matchid)
  WHERE teamid='GER'
```

Show the team1, team2 and player for every goal scored by a player called Mario player LIKE 'Mario%'

```sql
SELECT team1,team2,player
  FROM goal join game on (id=matchid)
  WHERE player LIKE 'Mario%'
```

The table eteam gives details of every national team including the coach. You can JOIN goal to eteam using the phrase goal JOIN eteam on teamid=id

Show player, teamid, coach, gtime for all goals scored in the first 10 minutes gtime<=10

```sql
SELECT player, teamid, coach, gtime
  FROM goal JOIN eteam ON (id = teamid)
  WHERE gtime<=10
```

To JOIN game with eteam you could use either
game JOIN eteam ON (team1=eteam.id) or game JOIN eteam ON (team2=eteam.id)

Notice that because id is a column name in both game and eteam you must specify eteam.id instead of just id

List the the dates of the matches and the name of the team in which 'Fernando Santos' was the team1 coach.

```sql
SELECT mdate,teamname
  FROM game JOIN eteam ON (team1 = eteam.id)
  WHERE coach = 'Fernando Santos'
```

List the player for every goal scored in a game WHERE the stadium was 'National Stadium, Warsaw'

```sql
SELECT player
  FROM goal JOIN game ON (id=matchid)
  WHERE stadium = 'National Stadium, Warsaw'
```

The example query shows all goals scored in the Germany-Greece quarterfinal.

```sql
SELECT player, gtime
  FROM game JOIN goal ON matchid = id
  WHERE (team1='GER' AND team2='GRE')
```

Instead show the name of all players who scored a goal against Germany.

show the name of all players who scored a goal against Germany.

```sql
SELECT DISTINCT player
  FROM game JOIN goal ON matchid = id
    WHERE (team1='GER' OR team2='GER')
    AND teamid!='GER'
```

Show teamname and the total number of goals scored.
You should COUNT(*) in the SELECT line and GROUP BY teamname

```sql
SELECT teamname, COUNT(*) AS Goals
  FROM eteam JOIN goal ON id=teamid
  GROUP BY teamname
```

For every match involving 'POL', show the matchid, date and the number of goals scored.

```sql
SELECT  matchid,mdate AS Date, COUNT( teamid) AS Goals
  FROM game JOIN goal ON matchid = id
  WHERE (team1 = 'POL' OR team2 = 'POL' )
  GROUP BY matchid
```

You want to find the stadium WHERE player 'Dimitris Salpingidis' scored. Select the JOIN condition to use:

game  JOIN goal ON (id=matchid)

You JOIN the tables goal and eteam in an SQL statement. Indicate the list of column names that may be used in the SELECT line:

matchid, teamid, player, gtime, id, teamname, coach
Select the code which shows players, their team and the amount of goals they scored against Greece(GRE).

```sql
SELECT player, COUNT(*), teamid
  FROM game JOIN goal ON matchid = id
    WHERE (team1 = "GRE" OR team2 = "GRE")
    AND teamid != 'GRE'
    GROUP BY player
```

Select the result that would be obtained FROM this code:

```sql
SELECT teamid, mdate FROM goal JOIN game ON matchid = id
  WHERE mdate = '9 June 2012'
```

| teamid | mdate |
|-----|-------------|
| DEN | 9 June 2012 |
| GER | 9 June 2012 |

Select the code which would show the player and their team for those who have scored against Poland(POL) in National Stadium, Warsaw.

```sql
SELECT DISTINCT player, teamid
  FROM game JOIN goal ON matchid = id
  WHERE stadium = 'National Stadium, Warsaw'
  AND mdate IN (SELECT mdate FROM game
                WHERE team1 = 'POL'
                OR team2 = 'POL')
  AND teamid != 'POL'
```

Select the code which shows the player, their team and the time they scored, for players who have played in Stadion Miejski (Wroclaw) but not against Italy(ITA).

```sql
SELECT DISTINCT player, teamid, gtime
  FROM game JOIN goal ON matchid = id
    WHERE stadium = 'Stadion Miejski (Wroclaw)'
    AND team1 != 'ITA'
    AND team2 !='ITA'
```

Select the result that would be obtained FROM this code:

```sql
SELECT teamname, COUNT(*)
  FROM eteam JOIN goal ON teamid = id
  GROUP BY teamname HAVING COUNT(*) < 3
```

| teamname | COUNT(*) |
|------------|------|
| Netherlands | 2 |
| Poland | 2 |
| Republic of Ireland | 1 |
| Ukraine | 2 |


Show the stadium and the number of goals scored in each stadium.

```sql
SELECT stadium,COUNT(*)
  FROM game JOIN goal ON id=matchid
  GROUP BY STADIUM
```

For every match involving 'POL', show the matchid, date and the number of goals scored.

```sql
SELECT matchid,mdate, COUNT(teamid)
  FROM game JOIN goal ON matchid = id
  WHERE (team1 = 'POL' OR team2 = 'POL')
  GROUP BY matchid
```

For every match WHERE 'GER' scored, show matchid, match date and the number of goals scored by 'GER'

```sql
SELECT matchid,mdate, COUNT(teamid)
  FROM game JOIN goal ON id=matchid
  WHERE (teamid='GER' )
  GROUP BY matchid
```

List every match with the goals scored by each team as shown. This will use "CASE WHEN" which has not been explained in any previous exercises.

| mdate  | team1  | score1  |  team2  | score2 |
|--------|--------|--------|---------|----|
| 1  | July  | 2012  | ESP  | 4  | ITA  | 0 |
| 10  | June  | 2012  |  ESP  | 1  | ITA  | 1 |
| 10  | June  | 2012  |  IRL  | 1  | CRO  |3 |
| ... | | | | | | |

Notice in the query given every goal is listed. If it was a team1 goal then a 1 appears in score1, otherwise there is a 0. You could SUM this column to get a count of the goals scored by team1. Sort your result by mdate, matchid, team1 and team2.

```sql
SELECT mdate,
  team1, SUM(CASE WHEN teamid=team1 THEN 1 ELSE 0 END) score1,
  team2, SUM(CASE WHEN teamid=team2 THEN 1 ELSE 0 END) score2
  FROM game LEFT JOIN goal ON matchid = id
  GROUP BY id
  ORDER BY mdate,matched,team1,team2
```

## SELECT within SELECT Tutorial

List each country name WHERE the population is larger than 'Russia'.
world(name, continent, area, population, gdp)

```sql
SELECT name FROM world
  WHERE population >
     (SELECT population FROM world
      WHERE name='Russia')
```

Show the countries in Europe with a per capita GDP greater than 'United Kingdom'.

```sql
SELECT name FROM world
  WHERE continent='Europe'
  AND (gdp/population) >
    (SELECT gdp/population FROM world
    WHERE name='United Kingdom')
```

List the name and continent of countries in the continents containing 'Belize', 'Belgium'.

```sql
SELECT name,continent
  FROM world
  WHERE continent IN ( SELECT continent FROM world
                       WHERE name = 'Belize' OR name = 'Belgium' )
```

Which country has a population that is more than Canada but less than Poland? Show the name and the population.

```sql
SELECT name,population FROM world
  WHERE population > (SELECT population FROM world
                      WHERE name = 'Canada')
  AND population < (SELECT population FROM world
                    WHERE name = 'Poland')
```

Which countries have a GDP greater than every country in Europe? Give the name only. (Some countries may have NULL gdp values)

```sql
SELECT name FROM world
  WHERE gdp > ALL
    ( SELECT gdp FROM world
      WHERE continent = 'Europe'
      AND gdp IS NOT NULL)
```

```sql
SELECT continent, name, population FROM world x
  WHERE population >= ALL
    (SELECT population FROM world y
      WHERE y.continent = x.continent
      AND population > 0)
```

Find the largest country (by area) in each continent, show the continent, the name and the area:

```sql
SELECT continent, name, area FROM world x
  WHERE area >= ALL
    (SELECT area FROM world y
      WHERE y.continent = x.continent
      AND area > 0)
```

The same query can be written as:

```sql
SELECT continent, name, area FROM world y
    WHERE area =
    ( SELECT MAX(area) FROM world x
      WHERE x.continent = y.continent)
```

Find each country that belongs to a continent WHERE all populations are less than 25000000. Show name, continent and population.

```sql
SELECT name,continent,population FROM world x
  WHERE 25000000 >= ALL (
    SELECT population FROM world y
     WHERE x.continent = y.continent
       AND y.population>0)
```

Some countries have populations more than three times that of any of their neighbours (in the same continent). Give the countries and continents.

```sql
SELECT name,continent FROM world x
  WHERE population > ALL (
    SELECT population * 3 FROM world y
      WHERE x.continent = y.continent
        AND x.name!=y.name )
```


### SELECT within SELECT Quizzes

1. Select the code that shows the name, region and population of the smallest country in each region

```sql
 SELECT region, name, population FROM bbc x
  WHERE population <= ALL (SELECT population FROM bbc y
                            WHERE y.region=x.region
                            AND population>0)
 ```

2. Select the code that shows the countries belonging to regions with all populations over 50000

```sql
 SELECT name,region,population FROM bbc x WHERE 50000 <= ALL (SELECT population FROM bbc y WHERE x.region=y.region AND y.population>0)
 ```

3. Select the code that shows the countries with a less than a third of the population of the countries around it

```sql
 SELECT name, region FROM bbc x WHERE population < ALL (SELECT population/3 FROM bbc y WHERE y.region = x.region AND y.name != x.name)
 ```

4. Select the result that would be obtained from the following code:

```sql
SELECT name FROM bbc
 WHERE population >
       (SELECT population
          FROM bbc
         WHERE name='United Kingdom')
   AND region IN
       (SELECT region
          FROM bbc
         WHERE name = 'United Kingdom')
```

| Table-D |
|----------|
| France |
| Germany |
| Russia |
| Turkey |



5. Select the code that would show the countries with a greater GDP than any country in Africa

```sql
 SELECT name FROM bbc WHERE gdp > ALL (SELECT MAX(gdp) FROM bbc WHERE region = 'Africa' AND gdp IS NOT NULL)
```

6. Select the code that shows the countries with population smaller than Russia but bigger than Denmark

```sql
 SELECT name FROM bbc WHERE population < (SELECT population FROM bbc WHERE name='Russia') AND population > (SELECT population FROM bbc WHERE name='Denmark')
 ```

7. Select the result that would be obtained from the following code:

```sql
SELECT name FROM bbc
 WHERE population > ALL
       (SELECT MAX(population)
          FROM bbc
         WHERE region = 'Europe')
   AND region = 'South Asia'
```

| Table-B |
|---|
| Bangladesh |
| India |
| Pakistan |


## More JOIN operations

### More JOIN operations Tutorial

1. List the films where the yr is 1962 [Show id, title]

```sql
SELECT id, title
 FROM movie
 WHERE yr=1962
```

2. Give year of 'Citizen Kane'.

```sql
SELECT yr FROM movie
  WHERE title = 'Citizen Kane'
```

3. List all of the Star Trek movies, include the id, title and yr (all of these movies include the words Star Trek in the title). Order results by year.

```sql
SELECT id, title, yr FROM movie
  WHERE title LIKE '%Star Trek%'
  ORDER BY yr
```

4. What are the titles of the films with id 11768, 11955, 21191

```sql
SELECT title FROM movie
  WHERE id IN (11768, 11955, 21191)
```

5. What id number does the actor 'Glenn Close' have?

```sql
SELECT id FROM actor
  WHERE name = 'Glenn Close'
```

6. What is the id of the film 'Casablanca'

```sql
SELECT id FROM movie
  WHERE title = 'Casablanca'
```

7. Obtain the cast list for 'Casablanca'. Use the id value that you obtained in the previous question.

```sql
SELECT name FROM actor
  JOIN casting ON actor.id = actorid
  JOIN movie ON movie.id = movieid
    WHERE movie.id = 11768
```

8. Obtain the cast list for the film 'Alien'

```sql
SELECT name FROM actor
  JOIN casting ON actor.id = actorid
  JOIN movie ON movie.id = movieid
    WHERE title = 'Alien'
```

9. List the films in which 'Harrison Ford' has appeared

```sql
SELECT title FROM movie
  JOIN casting ON movie.id = movieid
  JOIN actor ON actor.id = actorid
    WHERE name = 'Harrison Ford'
```

10. List the films where 'Harrison Ford' has appeared - but not in the star role. [Note: the ord field of casting gives the position of the actor. If ord=1 then this actor is in the starring role]

```sql
SELECT title FROM movie
  JOIN casting ON movie.id = movieid
  JOIN actor ON actor.id = actorid
    WHERE name = 'Harrison Ford'
    AND ord <> 1
```

11. List the films together with the leading star for all 1962 films.

```sql
SELECT title, name FROM movie
  JOIN casting ON movie.id = movieid
  JOIN actor ON actor.id = actorid
    WHERE yr = 1962
    AND ord = 1
```

12. Which were the busiest years for 'John Travolta', show the year and the number of movies he made each year for any year in which he made more than 2

```sql
SELECT yr,COUNT(title) FROM movie
  JOIN casting ON movie.id=movieid
  JOIN actor   ON actorid=actor.id
    WHERE name='John Travolta'
    GROUP BY yr
    HAVING COUNT(title) = ( SELECT MAX(c) FROM
                          ( SELECT yr,COUNT(title) AS c FROM movie
                             JOIN casting ON movie.id=movieid
                             JOIN actor   ON actorid=actor.id
                               WHERE name='John Travolta'
                               GROUP BY yr) AS t )
```
simpler way of writing a query that would return the result as per question. The result may be different depending on data in the db because the original solution uses `SELECT MAX` instead of `> 2`

```sql
SELECT yr,COUNT(title) FROM movie
  JOIN casting ON movie.id=movieid
  JOIN actor   ON actorid=actor.id
    WHERE name='John Travolta'
    GROUP BY yr
    HAVING COUNT(title) > 2
```

13. List the film title and the leading actor for all of the films 'Julie Andrews' played in.

```sql
SELECT title, name FROM movie
 JOIN casting ON movie.id=movieid
 JOIN actor   ON actorid=actor.id
  WHERE movieid IN (
    SELECT movieid FROM casting
      JOIN actor ON actorid=actor.id
      WHERE name='Julie Andrews')
  AND ord = 1
```

14. Obtain a list in alphabetical order of actors who've had at least 30 starring roles.

```sql
SELECT name FROM actor
  JOIN casting ON actor.id = actorid
    WHERE ord = 1
    GROUP BY name
    HAVING COUNT(ord) >= 30
```

15. List the films released in the year 1978 ordered by the number of actors in the cast.

```sql
SELECT title, COUNT(actorid) AS actors FROM movie
  JOIN casting ON id = movieid
    WHERE yr = 1978
    GROUP BY title
    ORDER BY actors DESC
```

16. List all the people who have worked with 'Art Garfunkel'.

```sql
SELECT name FROM actor
  JOIN casting ON id=actorid
    WHERE movieid IN ( SELECT movieid FROM casting
                         JOIN actor ON id=actorid
                           WHERE name = 'Art Garfunkel')
    AND name <> 'Art Garfunkel'
```
