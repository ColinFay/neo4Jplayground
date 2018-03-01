Colin Tracks
================

``` neo4j
LOAD CSV WITH HEADERS FROM "https://raw.githubusercontent.com/ThinkR-open/datasets/master/tracks.csv" AS csvLine CREATE (t:artist { name: csvLine.artist, album: csvLine.album_name, track: csvLine.track, duration: toInteger(csvLine.duration), expl: toBoolean(csvLine.explicit), pop: csvLine.popularity});
```

    ## 0 rows available after 818 ms, consumed after another 0 ms
    ## Added 2367 nodes, Set 14202 properties, Added 2367 labels

### How many Thy Art is Murder songs ?

``` neo4j
MATCH (a:artist) WHERE a.name = "Thy Art Is Murder" RETURN COUNT(*);
```

    ## +----------+
    ## | COUNT(*) |
    ## +----------+
    ## | 120      |
    ## +----------+
    ## 
    ## 1 row available after 80 ms, consumed after another 0 ms

Which
one?

``` neo4j
MATCH (a:artist) WHERE a.name = "Thy Art Is Murder" RETURN a.track AS nom;
```

    ## +-----------------------------+
    ## | nom                         |
    ## +-----------------------------+
    ## | "Reign Of Darkness"         |
    ## | "Slaves Beyond Death"       |
    ## | "Puppet Master"             |
    ## | "The Son Of Misery"         |
    ## | "Fire In The Sky"           |
    ## | "Into Chaos We Climb"       |
    ## | "The Final Curtain"         |
    ## | "Shadow Of Eternal Sin"     |
    ## | "Vile Creation"             |
    ## | "Du Hast"                   |
    ## | "They Will Know Another"    |
    ## | "Immolation"                |
    ## | "Dead Sun"                  |
    ## | "Gates Of Misery"           |
    ## | "Absolute Genocide"         |
    ## | "The Purest Strain Of Hate" |
    ## | "Infinite Forms"            |
    ## | "Defective Breed"           |
    ## | "Doomed From Birth"         |
    ## | "Dear Desolation"           |
    ## | "Death Dealer"              |
    ## | "Man Is the Enemy"          |
    ## | "The Skin Of The Serpent"   |
    ## | "No Absolution"             |
    ## | "Reign Of Darkness"         |
    ## | "Slaves Beyond Death"       |
    ## | "Puppet Master"             |
    ## | "The Son Of Misery"         |
    ## | "Fire In The Sky"           |
    ## | "Into Chaos We Climb"       |
    ## | "The Final Curtain"         |
    ## | "Shadow Of Eternal Sin"     |
    ## | "Vile Creation"             |
    ## | "Du Hast"                   |
    ## | "They Will Know Another"    |
    ## | "Immolation"                |
    ## | "Dead Sun"                  |
    ## | "Gates Of Misery"           |
    ## | "Absolute Genocide"         |
    ## | "The Purest Strain Of Hate" |
    ## | "Infinite Forms"            |
    ## | "Defective Breed"           |
    ## | "Doomed From Birth"         |
    ## | "Dear Desolation"           |
    ## | "Death Dealer"              |
    ## | "Man Is the Enemy"          |
    ## | "The Skin Of The Serpent"   |
    ## | "No Absolution"             |
    ## | "Reign Of Darkness"         |
    ## | "Slaves Beyond Death"       |
    ## | "Puppet Master"             |
    ## | "The Son Of Misery"         |
    ## | "Fire In The Sky"           |
    ## | "Into Chaos We Climb"       |
    ## | "The Final Curtain"         |
    ## | "Shadow Of Eternal Sin"     |
    ## | "Vile Creation"             |
    ## | "Du Hast"                   |
    ## | "They Will Know Another"    |
    ## | "Immolation"                |
    ## | "Dead Sun"                  |
    ## | "Gates Of Misery"           |
    ## | "Absolute Genocide"         |
    ## | "The Purest Strain Of Hate" |
    ## | "Infinite Forms"            |
    ## | "Defective Breed"           |
    ## | "Doomed From Birth"         |
    ## | "Dear Desolation"           |
    ## | "Death Dealer"              |
    ## | "Man Is the Enemy"          |
    ## | "The Skin Of The Serpent"   |
    ## | "No Absolution"             |
    ## | "Reign Of Darkness"         |
    ## | "Slaves Beyond Death"       |
    ## | "Puppet Master"             |
    ## | "The Son Of Misery"         |
    ## | "Fire In The Sky"           |
    ## | "Into Chaos We Climb"       |
    ## | "The Final Curtain"         |
    ## | "Shadow Of Eternal Sin"     |
    ## | "Vile Creation"             |
    ## | "Du Hast"                   |
    ## | "They Will Know Another"    |
    ## | "Immolation"                |
    ## | "Dead Sun"                  |
    ## | "Gates Of Misery"           |
    ## | "Absolute Genocide"         |
    ## | "The Purest Strain Of Hate" |
    ## | "Infinite Forms"            |
    ## | "Defective Breed"           |
    ## | "Doomed From Birth"         |
    ## | "Dear Desolation"           |
    ## | "Death Dealer"              |
    ## | "Man Is the Enemy"          |
    ## | "The Skin Of The Serpent"   |
    ## | "No Absolution"             |
    ## | "Reign Of Darkness"         |
    ## | "Slaves Beyond Death"       |
    ## | "Puppet Master"             |
    ## | "The Son Of Misery"         |
    ## | "Fire In The Sky"           |
    ## | "Into Chaos We Climb"       |
    ## | "The Final Curtain"         |
    ## | "Shadow Of Eternal Sin"     |
    ## | "Vile Creation"             |
    ## | "Du Hast"                   |
    ## | "They Will Know Another"    |
    ## | "Immolation"                |
    ## | "Dead Sun"                  |
    ## | "Gates Of Misery"           |
    ## | "Absolute Genocide"         |
    ## | "The Purest Strain Of Hate" |
    ## | "Infinite Forms"            |
    ## | "Defective Breed"           |
    ## | "Doomed From Birth"         |
    ## | "Dear Desolation"           |
    ## | "Death Dealer"              |
    ## | "Man Is the Enemy"          |
    ## | "The Skin Of The Serpent"   |
    ## | "No Absolution"             |
    ## +-----------------------------+
    ## 
    ## 120 rows available after 1 ms, consumed after another 27 ms

### Average duration

``` neo4j
MATCH (a:artist) RETURN AVG(a.duration);
```

    ## +--------------------+
    ## | AVG(a.duration)    |
    ## +--------------------+
    ## | 248153.25433037596 |
    ## +--------------------+
    ## 
    ## 1 row available after 328 ms, consumed after another 0 ms

### Names of Emperor songs

``` neo4j
MATCH (a:artist {name: "Emperor"}) RETURN a.track AS emperor_tracks;
```

    ## +----------------------------------+
    ## | emperor_tracks                   |
    ## +----------------------------------+
    ## | "I Am the Black Wizards"         |
    ## | "The Loss & Curse of Reverence"  |
    ## | "The Burning Shadows of Silence" |
    ## | "I Am the Black Wizards"         |
    ## | "The Loss & Curse of Reverence"  |
    ## | "The Burning Shadows of Silence" |
    ## | "I Am the Black Wizards"         |
    ## | "The Loss & Curse of Reverence"  |
    ## | "The Burning Shadows of Silence" |
    ## | "I Am the Black Wizards"         |
    ## | "The Loss & Curse of Reverence"  |
    ## | "The Burning Shadows of Silence" |
    ## | "I Am the Black Wizards"         |
    ## | "The Loss & Curse of Reverence"  |
    ## | "The Burning Shadows of Silence" |
    ## +----------------------------------+
    ## 
    ## 15 rows available after 1 ms, consumed after another 20 ms

### Max duration

``` neo4j
MATCH (a:artist) RETURN MAX(a.duration);
```

    ## +-----------------+
    ## | MAX(a.duration) |
    ## +-----------------+
    ## | 1264266         |
    ## +-----------------+
    ## 
    ## 1 row available after 51 ms, consumed after another 0 ms
