# Spotify Analytics 
Dataset: [Kaggle](https://www.kaggle.com/equinxx/spotify-top-50-songs-in-2021?select=spotify_top50_2021.csv)

<br>

## Analytics
Analyzes data from a Spotify dataset, focusing on artist popularity, song duration, energy levels, and emotional valence.

<br>

### Who are the top 10 artists based on popularity?
```sql
SELECT
    artist_name,
    AVG(popularity) popularity
FROM BIT_DB.Spotifydata
GROUP BY artist_name
ORDER BY popularity DESC
LIMIT 10;
```

<br>

### What are the top 25 longest songs in the dataset? (calculate duration from ms to seconds)
```sql
SELECT
    artist_name,
    track_name,
    (duration_ms / 1000) duration_seconds
FROM BIT_DB.Spotifydata
ORDER BY duration_seconds DESC
LIMIT 25;
```

<br>

### What songs give the most calming energy?
```sql
SELECT
    artist_name,
    track_name
FROM BIT_DB.Spotifydata
WHERE energy < 0.5
ORDER BY energy ASC;
```

<br>

### What are the max and minimum valence?
(scored between 0-10, valence measures whether a song will make a person feel happy (high) or sad (low))
```sql
SELECT
    artist_name,
    track_name,
    ROUND((valence * 10), 2) valence
FROM BIT_DB.Spotifydata
WHERE valence = (SELECT MAX(valence) FROM BIT_DB.Spotifydata)
OR valence = (SELECT MIN(valence) FROM BIT_DB.Spotifydata);
```

<br>
