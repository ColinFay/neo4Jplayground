## 90's norwegian black metal bands as a Neo4J graph

```
CREATE
// bands
(burzum:Band {name: 'Burzum', formed: 1991}),
(carpathianforest:Band {name: 'Carpathian Forest', formed: 1990}),
(darkthrone:Band {name: 'Darkthrone', formed: 1986}),
(emperor:Band {name: 'Emperor', formed: 1986}),
(enslaved:Band {name: 'Enslaved', formed: 1991}),
(gorgoroth:Band {name: 'Gorgoroth', formed: 1992}),
(hades:Band {name: 'Hades', formed: 1992}),
(immortal:Band {name: 'Immortal', formed: 1991}),
(mayhem:Band {name: 'Mayhem', formed: 1984}),
(satyricon:Band {name: 'Satyricon', formed: 1984}),
(taake:Band {name: 'Taake', formed: 1993}),
// City
(bergen:City {name: 'Bergen'}),
(oslo:City {name: 'Oslo'}),
(sandnes:City {name: 'Sandnes'}),
(rogaland:City {name: 'Rogaland'}),
// Records
(deathcrush:record {name: 'Deathcrush', release: 1987}),
(freezingmoon:record {name: 'Freezing Moon', release: 1987}),
(carnage:record {name: 'Carnage', release: 1990}),
(liveinleipzig:record {name: 'Live in Leipzig', release: 1990}),
(demoi:record {name: 'Demo I', release: 1991}),
(ablaze:record {name: 'A Blaze in the Northern Sky', release: 1991}),
(immortal_rec:record {name: 'Immortal', release: 1991}),
(demoii:record {name: 'Demo I', release: 1991}),
(nema:record {name: 'Nema', release: 1991}),
(burzum_rec:record {name: 'Burzum', release: 1992}),
(detsom:record {name: 'Det som engang var', release: 1992}),
(diabolical:record {name: 'Diabolical Fullmoon Mysticism', release: 1992}),
(wrath:record {name: 'Wrath of the Tyrant', release: 1992}),
(all_evil:record {name: 'All Evil', release: 1992}),
(yggdrasill:record {name: 'Yggdrasill', release: 1992}),
(funeral_moon:record {name: 'Under a Funeral Moon', release: 1992}),
(aske:record {name: 'Aske', release: 1992}),
(bloodlust:record {name: 'Bloodlust & Perversion', release: 1992}),
(hvis:record {name: 'Hvis lyset tar oss', release: 1992}),
(demys:record {name: 'De Mysteriis Dom Sathanas', release: 1992}),
(hordanes:record {name: 'Hordanes Land', release: 1992}),
(emperor_rec:record {name: 'Emperor', release: 1992}),
(as_the_shadow:record {name: 'As the Shadows Rise', release: 1992}),
(filosofem:record {name: 'Filosofem', release: 1993}),
(theforest:record {name: 'The Forest Is My Throne', release: 1993}),
(viking:record {name: 'Vikingligr Veldi', release: 1993}),
(journey:record {name: 'Journey Through the Cold', release: 1993}),
(moors:record {name: 'Moors of Svarttjern', release: 1993}),
(asorcery:record {name: 'A Sorcery Written in Blood', release: 1993}),
(inthenightside:record {name: 'In the Nightside Eclipse', release: 1993}),
(darkmed:record {name: 'Dark Medieval Times', release: 1993}),
(pureho:record {name: 'Pure Holocaust', release: 1993}),
(trans:record {name: 'Transilvanian Hunger', release: 1993}),
// links
// IS_FROM
(burzum)-[:IS_FROM]->(bergen),
(carpathianforest)-[:IS_FROM]->(rogaland),
(emperor)-[:IS_FROM]->(sandnes),
(enslaved)-[:IS_FROM]->(rogaland),
(gorgoroth)-[:IS_FROM]->(bergen),
(hades)-[:IS_FROM]->(bergen),
(immortal)-[:IS_FROM]->(bergen),
(mayhem)-[:IS_FROM]->(oslo),
(satyricon)-[:IS_FROM]->(oslo),
(taake)-[:IS_FROM]->(bergen), 
// WAS_RECORDED
(deathcrush)-[:WAS_RECORDED]->(mayhem),
(freezingmoon)-[:WAS_RECORDED]->(mayhem),
(carnage)-[:WAS_RECORDED]->(mayhem),
(liveinleipzig)-[:WAS_RECORDED]->(mayhem),
(demys)-[:WAS_RECORDED]->(mayhem),
(demoi)-[:WAS_RECORDED]->(burzum),
(demoii)-[:WAS_RECORDED]->(burzum),
(burzum_rec)-[:WAS_RECORDED]->(burzum),
(detsom)-[:WAS_RECORDED]->(burzum),
(aske)-[:WAS_RECORDED]->(burzum),
(hvis)-[:WAS_RECORDED]->(burzum),
(filosofem)-[:WAS_RECORDED]->(burzum),
(ablaze)-[:WAS_RECORDED]->(darkthrone),
(funeral_moon)-[:WAS_RECORDED]->(darkthrone),
(trans)-[:WAS_RECORDED]->(darkthrone),
(immortal_rec)-[:WAS_RECORDED]->(immortal),
(diabolical)-[:WAS_RECORDED]->(immortal),
(pureho)-[:WAS_RECORDED]->(immortal),
(nema)-[:WAS_RECORDED]->(enslaved),
(yggdrasill)-[:WAS_RECORDED]->(enslaved),
(hordanes)-[:WAS_RECORDED]->(enslaved),
(viking)-[:WAS_RECORDED]->(enslaved),
(wrath)-[:WAS_RECORDED]->(emperor),
(all_evil)-[:WAS_RECORDED]->(satyricon),
(theforest)-[:WAS_RECORDED]->(satyricon),
(darkmed)-[:WAS_RECORDED]->(satyricon),
(bloodlust)-[:WAS_RECORDED]->(carpathianforest),
(journey)-[:WAS_RECORDED]->(carpathianforest),
(moors)-[:WAS_RECORDED]->(carpathianforest),
(emperor_rec)-[:WAS_RECORDED]->(emperor),
(as_the_shadow)-[:WAS_RECORDED]->(emperor),
(inthenightside)-[:WAS_RECORDED]->(emperor),
(asorcery)-[:WAS_RECORDED]->(gorgoroth);
```

## Return 

### formed in 1990 

`MATCH (b:Band) WHERE b.formed = 1990 RETURN *;` 

or

`MATCH (b:Band {formed: 1990}) RETURN *;` 

### formed before 1995

`MATCH (b:Band) WHERE b.formed < 1995 RETURN *;`

### From Oslo

`MATCH (r:Band) -[f:IS_FROM] -> (c:City {name:"Oslo"}) RETURN *;`

### Demo albums 

`MATCH (r:record) WHERE r.name CONTAINS "Demo" RETURN *;`

### Emperor albums

`MATCH (r:record) -[:WAS_RECORDED] -> (b:Band) where b.name = "Emperor" RETURN *;`

## Count stuffs

### Recorded in 1993

`MATCH (r:record) WHERE r.release = 1993 RETURN COUNT(*);`

### Bands from Bergen

`MATCH (r:Band) -[f:IS_FROM] -> (c:City {name:"Bergen"}) RETURN COUNT(*);`

