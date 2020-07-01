# Exercice d'SQL

**1) Affichez toutes les villes**  
```sql

Select name from city;
-- 4079
```

**2) Affichez toutes les villes françaises**  

```sql
Select name from city where countryCode='FRA';
-- 4079
```
**3) Affichez les pays dont la date d'indépendance est inférieur à l'an 1900 et n'est pas null**  
```sql
select * from country where IndepYear < 1900 AND NOT NULL;
-- 43
```

**4) Affichez le nombre de pays dans le monde**  
```sql
select count(*) from country;
-- 239
```
**5) Affichez le pays avec la plus petite superficie**  
<<<<<<< HEAD
```sql
SELECT * FROM country WHERE SurfaceArea = (SELECT MIN(SurfaceArea) FROM country);

select Name from world.country ORDER BY SurfaceArea ASC LIMIT 1;
-- 0.4 - vatican
```
**6) Affichez le nombre moyen d'habitants par ville**  
```sql
SELECT AVG(Population) FROM country;
-- 350468
``` 

=======
**6) Affichez le nombre moyen d'habitants pour toute ville confondue**  
>>>>>>> 497e154176200cb704ffed92849ec59b1f83e5f3
**7) Affichez le nom et la densité des pays (population/surface) rangées par ordre décroissant de densité**  

```sql
SELECT Name, (population/surfaceArea) AS density FROM country ORDER BY density DESC;
```


**8) Insérer une nouvelle ville avec :**  

- ID : 4080
- Name : Oompa Loompa
- CountryCode : BRA 
- District : Amazonas
- Population : 78000

```sql
INSERT INTO city(Name, CountryCode, District, Population)
VALUES(NULL, "Oompa Loompa", "BRA", "Amazonas", 78000)
```
**9) Supprimer la ville de Campinas ainsi que toutes les données liées**  

```sql
DELETE FROM city WHERE name = 'Campinas'
```

**10) Affichez toute les villes dont la langue officiel est l'anglais. Sur ces résultats devront apparaître les colonnes:**  

- Name (en tant que nom de la ville)
- CountryCode (en tant que code pays)
- CountryName (en tant que nom de ce pays)
- Population
- Percentage (en tant que le pourcentage de personne parlant ce language)

<<<<<<< HEAD
```sql
SELECT city.NAME, country.Name as 'CountryName', country.Code, countrylanguage.Percentage, city.Population FROM country, countrylanguage, city WHERE country.Code = countrylanguage.CountryCode AND city.CountryCode = country.Code AND countrylanguage.isOfficial = "T" And countrylanguage.Language = 'English' 
```

ou encore 

```sql
SELECT city.NAME, country.Name as 'CountryName', country.Code, countrylanguage.Percentage, city.Population 
FROM country
INNER JOIN countrylanguage on (country.Code = countrylanguage.CountryCode)
INNER JOIN city ON (city.CountryCode = country.Code)
WHERE countrylanguage.isOfficial = "T"
And countrylanguage.Language = 'English'
```

**11) Affichez la différence entre la somme des populations listée dans les villes par rapport à la population annoncée dans le pays**
  
```sql
Select Country.code, Country.population as 'Country Pop', Cities.population as 'City Pop',  Country.population - Cities.population as 'Difference Pop'
FROM
(SELECT code, sum(city.population) as population FROM country, city where city.countryCode = country.code group by code) Cities
RIGHT JOIN Country on ( Country.code = Difference.code)
```
=======
**11) Affichez la différence entre la somme des populations listée dans les villes par rapport à la population annoncée dans le pays**  
>>>>>>> 497e154176200cb704ffed92849ec59b1f83e5f3
