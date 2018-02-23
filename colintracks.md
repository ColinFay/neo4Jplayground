## Load

```
LOAD CSV WITH HEADERS FROM "https://raw.githubusercontent.com/ThinkR-open/datasets/master/tracks.csv" AS csvLine
CREATE (t:artist { name: csvLine.artist, album: csvLine.album_name, track: csvLine.track, duration: toInteger(csvLine.duration), expl: toBoolean(csvLine.explicit), pop: csvLine.popularity});
```

### How many Thy Art is Murder songs ? 

```
MATCH (a:artist) WHERE a.name = "Thy Art Is Murder" RETURN COUNT(*);
+----------+
| COUNT(*) |
+----------+
| 24       |
+----------+

1 row available after 64 ms, consumed after another 0 ms
```

Which one?

```
MATCH (a:artist) WHERE a.name = "Thy Art Is Murder" RETURN a.track AS nom;
+-----------------------------+
| nom                         |
+-----------------------------+
| "Reign Of Darkness"         |
| "Slaves Beyond Death"       |
| "Puppet Master"             |
| "The Son Of Misery"         |
| "Fire In The Sky"           |
| "Into Chaos We Climb"       |
| "The Final Curtain"         |
| "Shadow Of Eternal Sin"     |
| "Vile Creation"             |
| "Du Hast"                   |
| "They Will Know Another"    |
| "Immolation"                |
| "Dead Sun"                  |
| "Gates Of Misery"           |
| "Absolute Genocide"         |
| "The Purest Strain Of Hate" |
| "Infinite Forms"            |
| "Defective Breed"           |
| "Doomed From Birth"         |
| "Dear Desolation"           |
| "Death Dealer"              |
| "Man Is the Enemy"          |
| "The Skin Of The Serpent"   |
| "No Absolution"             |
+-----------------------------+

24 rows available after 17 ms, consumed after another 10 ms
```

### Average duration

```
MATCH (a:artist) RETURN AVG(a.duration);
+-------------------+
| AVG(a.duration)   |
+-------------------+
| 248153.2543303759 |
+-------------------+

1 row available after 64 ms, consumed after another 0 ms
```

### Names of Emperor songs
```
MATCH (a:artist {name: "Emperor"}) RETURN a.track AS emperor_tracks;
+----------------------------------+
| emperor_tracks                   |
+----------------------------------+
| "I Am the Black Wizards"         |
| "The Loss & Curse of Reverence"  |
| "The Burning Shadows of Silence" |
+----------------------------------+

3 rows available after 15 ms, consumed after another 13 ms
```

### Max duration

```
MATCH (a:artist) RETURN MAX(a.duration);
+-----------------+
| MAX(a.duration) |
+-----------------+
| 1264266         |
+-----------------+

1 row available after 31 ms, consumed after another 0 ms
```


