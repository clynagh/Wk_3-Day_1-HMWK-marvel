# SQL Homework

The Dominion Cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'
```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:
```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1. Return ALL the data in the 'movies' table.
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:45
  2 | The Incredible Hulk                 | 2008 | 13:45
  3 | Iron Man 2                          | 2010 | 13:20
  4 | Thor                                | 2011 | 14:45
  5 | Captain America: The First Avenger  | 2011 | 16:25
  6 | Avengers Assemble                   | 2012 | 22:35
  7 | Iron Man 3                          | 2013 | 15:50
  8 | Thor: The Dark World                | 2013 | 19:25
  9 | Batman Begins                       | 2005 | 23:15
 10 | Captain America: The Winter Soldier | 2014 | 18:50
 11 | Guardians of the Galaxy             | 2014 | 13:00
 12 | Avengers: Age of Ultron             | 2015 | 13:25
 13 | Ant-Man                             | 2015 | 13:30
 14 | Captain America: Civil War          | 2016 | 20:50
 15 | Doctor Strange                      | 2016 | 16:45
(15 rows)

2. Return ONLY the name column from the 'people' table
marvel=# SELECT name FROM people;
        name        
--------------------
 Adam  Baxter
 Alice Loudon
 Chris Brown
 Colin Farquhar
 David  Hale
 Douglas Crooke
 Ewen Carr
 Ferdinando Sendyka
 Craig Morton
 Andrew
 Andrew
 Graeme Bell
 Josef Meszaros
 Km North
 Leon-Paul Hart
 Lewis Brown
 Richard Page Croft
 Rob Flett
 Robert Ball
 Robert Brice
 Ross Crichton
 Simon Smith
 Suzanne Aitchison
(23 rows)

marvel=# 

3.Oops! Someone at CodeClan spelled Kim's name wrong! Change it to reflect the proper spelling (change 'Km North' to 'Kim North').

marvel=# UPDATE people SET name = 'Kim North' WHERE id=14;
UPDATE 1
marvel=# SELECT * FROM people;

 id |        name        
----+--------------------
  1 | Adam  Baxter
  2 | Alice Loudon
  3 | Chris Brown
  4 | Colin Farquhar
  5 | David  Hale
  6 | Douglas Crooke
  7 | Ewen Carr
  8 | Ferdinando Sendyka
  9 | Craig Morton
 10 | Andrew
 11 | Andrew
 12 | Graeme Bell
 13 | Josef Meszaros
 15 | Leon-Paul Hart
 16 | Lewis Brown
 17 | Richard Page Croft
 18 | Rob Flett
 19 | Robert Ball
 20 | Robert Brice
 21 | Ross Crichton
 22 | Simon Smith
 23 | Suzanne Aitchison
 14 | Kim North
(23 rows)



4. Return ONLY your name from the 'people' table - My name in this case is Ewen Carr.

marvel=# SELECT name FROM people WHERE name = 'Ewen Carr';
   name    
-----------
 Ewen Carr
(1 row)

marvel=# 


5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

marvel=# DELETE FROM movies WHERE title = 'Batman Begins';
DELETE 1
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:45
  2 | The Incredible Hulk                 | 2008 | 13:45
  3 | Iron Man 2                          | 2010 | 13:20
  4 | Thor                                | 2011 | 14:45
  5 | Captain America: The First Avenger  | 2011 | 16:25
  6 | Avengers Assemble                   | 2012 | 22:35
  7 | Iron Man 3                          | 2013 | 15:50
  8 | Thor: The Dark World                | 2013 | 19:25
 10 | Captain America: The Winter Soldier | 2014 | 18:50
 11 | Guardians of the Galaxy             | 2014 | 13:00
 12 | Avengers: Age of Ultron             | 2015 | 13:25
 13 | Ant-Man                             | 2015 | 13:30
 14 | Captain America: Civil War          | 2016 | 20:50
 15 | Doctor Strange                      | 2016 | 16:45
(14 rows)

marvel=# 

6. Create a new entry in the 'people' table with the name of one of the instructors.

marvel=# INSERT INTO people (name) VALUES ('John Harper');
INSERT 0 1
marvel=# SELECT * FROM people;
 id |        name        
----+--------------------
  1 | Adam  Baxter
  2 | Alice Loudon
  3 | Chris Brown
  4 | Colin Farquhar
  5 | David  Hale
  6 | Douglas Crooke
  7 | Ewen Carr
  8 | Ferdinando Sendyka
  9 | Craig Morton
 10 | Andrew
 11 | Andrew
 12 | Graeme Bell
 13 | Josef Meszaros
 15 | Leon-Paul Hart
 16 | Lewis Brown
 17 | Richard Page Croft
 18 | Rob Flett
 19 | Robert Ball
 20 | Robert Brice
 21 | Ross Crichton
 22 | Simon Smith
 23 | Suzanne Aitchison
 14 | Kim North
 24 | John Harper
(24 rows)

marvel=# 

7. Craig Morton, has decided to hijack our movie evening, Remove him from the table of people.

marvel=# DELETE FROM people WHERE name = 'Craig Morton';
DELETE 1
marvel=# SELECT * FROM people;
 id |        name        
----+--------------------
  1 | Adam  Baxter
  2 | Alice Loudon
  3 | Chris Brown
  4 | Colin Farquhar
  5 | David  Hale
  6 | Douglas Crooke
  7 | Ewen Carr
  8 | Ferdinando Sendyka
 10 | Andrew
 11 | Andrew
 12 | Graeme Bell
 13 | Josef Meszaros
 15 | Leon-Paul Hart
 16 | Lewis Brown
 17 | Richard Page Croft
 18 | Rob Flett
 19 | Robert Ball
 20 | Robert Brice
 21 | Ross Crichton
 22 | Simon Smith
 23 | Suzanne Aitchison
 14 | Kim North
 24 | John Harper
(23 rows)

marvel=# 

8. Somehow the list of people includes two people named 'Andrew'. Change these entries to the proper names ('Jeff 4', 'Jeff 5')
marvel=# UPDATE people SET name = 'Jeff 4' WHERE id = 10;
UPDATE 1
marvel=# SELECT * FROM people;
 id |        name        
----+--------------------
  1 | Adam  Baxter
  2 | Alice Loudon
  3 | Chris Brown
  4 | Colin Farquhar
  5 | David  Hale
  6 | Douglas Crooke
  7 | Ewen Carr
  8 | Ferdinando Sendyka
 11 | Andrew
 12 | Graeme Bell
 13 | Josef Meszaros
 15 | Leon-Paul Hart
 16 | Lewis Brown
 17 | Richard Page Croft
 18 | Rob Flett
 19 | Robert Ball
 20 | Robert Brice
 21 | Ross Crichton
 22 | Simon Smith
 23 | Suzanne Aitchison
 14 | Kim North
 24 | John Harper
 10 | Jeff 4
(23 rows)

marvel=# UPDATE people SET name = 'Jeff 5' WHERE id = 11;
UPDATE 1
marvel=# SELECT * FROM people;
 id |        name        
----+--------------------
  1 | Adam  Baxter
  2 | Alice Loudon
  3 | Chris Brown
  4 | Colin Farquhar
  5 | David  Hale
  6 | Douglas Crooke
  7 | Ewen Carr
  8 | Ferdinando Sendyka
 12 | Graeme Bell
 13 | Josef Meszaros
 15 | Leon-Paul Hart
 16 | Lewis Brown
 17 | Richard Page Croft
 18 | Rob Flett
 19 | Robert Ball
 20 | Robert Brice
 21 | Ross Crichton
 22 | Simon Smith
 23 | Suzanne Aitchison
 14 | Kim North
 24 | John Harper
 10 | Jeff 4
 11 | Jeff 5

9. The cinema has just heard that they will be holding an exclusive midnight showing of 'Guardians of the Galaxy 2'!! Create a new entry in the 'movies' table to reflect this.

marvel=# INSERT INTO movies (title, year, show_time) VALUES ('Guardians of the Galaxy 2', 2017, '24:00'); 
INSERT 0 1
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 13:15
  2 | The Incredible Hulk                 | 2008 | 12:50
  3 | Iron Man 2                          | 2010 | 15:35
  4 | Thor                                | 2011 | 13:35
  5 | Captain America: The First Avenger  | 2011 | 16:10
  6 | Avengers Assemble                   | 2012 | 13:30
  7 | Iron Man 3                          | 2013 | 18:35
  8 | Thor: The Dark World                | 2013 | 19:25
  9 | Batman Begins                       | 2005 | 17:25
 10 | Captain America: The Winter Soldier | 2014 | 12:40
 11 | Guardians of the Galaxy             | 2014 | 18:00
 12 | Avengers: Age of Ultron             | 2015 | 21:45
 13 | Ant-Man                             | 2015 | 16:30
 14 | Captain America: Civil War          | 2016 | 18:30
 15 | Doctor Strange                      | 2016 | 22:20
 16 | Guardians of the Galaxy 2           | 2017 | 24:00
(16 rows)

marvel=# 


10. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 12:10 to 21:30

marvel=# UPDATE movies SET show_time = '21:30' WHERE title  = 'Guardians of the Galaxy' AND id = 11;
UPDATE 1
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time 
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 13:15
  2 | The Incredible Hulk                 | 2008 | 12:50
  3 | Iron Man 2                          | 2010 | 15:35
  4 | Thor                                | 2011 | 13:35
  5 | Captain America: The First Avenger  | 2011 | 16:10
  6 | Avengers Assemble                   | 2012 | 13:30
  7 | Iron Man 3                          | 2013 | 18:35
  8 | Thor: The Dark World                | 2013 | 19:25
  9 | Batman Begins                       | 2005 | 17:25
 10 | Captain America: The Winter Soldier | 2014 | 12:40
 12 | Avengers: Age of Ultron             | 2015 | 21:45
 13 | Ant-Man                             | 2015 | 16:30
 14 | Captain America: Civil War          | 2016 | 18:30
 15 | Doctor Strange                      | 2016 | 22:20
 16 | Guardians of the Galaxy 2           | 2017 | 24:00
 11 | Guardians of the Galaxy             | 2014 | 21:30
(16 rows)

marvel=# 


## Extension

1. Research how to delete multiple entries from your table in a single command.

marvel=# DELETE FROM movies WHERE year BETWEEN 2010 AND 2015;
DELETE 20
marvel=# SELECT * FROM movies;
 id |           title            | year | show_time 
----+----------------------------+------+-----------
  1 | Iron Man                   | 2008 | 13:15
  2 | The Incredible Hulk        | 2008 | 12:50
  9 | Batman Begins              | 2005 | 17:25
 14 | Captain America: Civil War | 2016 | 18:30
 15 | Doctor Strange             | 2016 | 22:20
 16 | Guardians of the Galaxy 2  | 2017 | 24:00
 17 | Iron Man                   | 2008 | 13:15
 18 | The Incredible Hulk        | 2008 | 12:50
 25 | Batman Begins              | 2005 | 17:25
 30 | Captain America: Civil War | 2016 | 18:30
 31 | Doctor Strange             | 2016 | 22:20
(11 rows)

marvel=# 
