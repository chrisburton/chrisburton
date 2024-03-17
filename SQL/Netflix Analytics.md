# Netflix Analytics 
PostgreSQL was used to answer specific questions about TV and Movie content hosted on Netflix.

Dataset: [db-fiddle](https://www.db-fiddle.com/f/5XjDEBzg6DR1XzKVwNapdD/0)

<br>

## Analysis    

<br>

### How many movie titles are there in the database? (movies only, not tv shows)
```sql
SELECT 
  COUNT(titles.type)
FROM "netflix_titles_info" titles
WHERE titles.type = 'Movie';
```
<details>
  <summary><b><i>Show result</i></b></summary>

| count |
|:-----:|
| 8     |
</details>

<br>

### When was the most recent batch of tv shows and/or movies added to the database?
```sql
SELECT 
  MAX(DATE(date_added))
FROM "netflix_titles_info";
```
<details>
  <summary><b><i>Show result</i></b></summary>
    
| max                  |
|---------------------|
| 2021-09-25T00:00:00Z |
</details>

<br>

### List all the movies and tv shows in alphabetical order. 
```sql
SELECT 
  title
FROM "netflix_titles_info"
ORDER BY title ASC;
```
<details>
  <summary><b><i>Show result</i></b></summary>

| title                                               |
|-----------------------------------------------------|
| Bangkok Breaking                                    |
| Blood & Water                                       |
| Confessions of an Invisible Girl                    |
| Crime Stories: India Detectives                     |
| Dear White People                                   |
| Dick Johnson Is Dead                                |
| Europe's Most Dangerous Man: Otto Skorzeny in Spain |
| Falsa identidad                                     |
| Ganglands                                           |
| Intrusion                                           |
| Jaguar                                              |
| Jailbirds New Orleans                               |
| Je Suis Karl                                        |
| Kota Factory                                        |
| Midnight Mass                                       |
| My Little Pony: A New Generation                    |
| Sankofa                                             |
| The Great British Baking Show                       |
| The Starling                                        |
| Vendetta: Truth Lies and The Mafia                  |
</details>

<br>

### Who was the Director for the movie The Starling? 
```sql
SELECT 
  director
FROM "netflix_titles_info" titles
LEFT JOIN "netflix_people" people
ON titles.show_id = people.show_id
WHERE titles.title = 'The Starling';
```
<details>
  <summary><b><i>Show result</i></b></summary>

| director       |
|----------------|
| Theodore Melfi |
</details>

<br>

### What is the oldest movie in the database and what year was it made? 
```sql
SELECT 
  title, 
  release_year
FROM "netflix_titles_info"
WHERE type = 'Movie'
ORDER BY release_year ASC
LIMIT 1;
```
<details>
  <summary><b><i>Show result</i></b></summary>

| title   | release_year |
|---------|:------------:|
| Sankofa | 1993         |
</details>

<br>
