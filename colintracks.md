## Load

```
LOAD CSV WITH HEADERS FROM "https://raw.githubusercontent.com/ThinkR-open/datasets/master/tracks.csv" AS csvLine
CREATE (t:artist { name: csvLine.artist, album: csvLine.album_name, track: csvLine.track, duration: toInteger(csvLine.duration), expl: toBoolean(csvLine.explicit), pop: csvLine.popularity});
```

### How many Thy Art is Murder songs ? 

```
MATCH (a:artist) WHERE a.name = "Thy Art Is Murder" RETURN COUNT(*);
```

Which one?

```
MATCH (a:artist) WHERE a.name = "Thy Art Is Murder" RETURN *;
```

### Average duration

```
MATCH (a:artist) RETURN AVG(a.duration);
```

### Names of Emperor songs
```
MATCH (a:artist {name: "Emperor"}) RETURN a.track;
```

### Max duration

```
MATCH (a:artist) RETURN MAX(a.duration);
```

