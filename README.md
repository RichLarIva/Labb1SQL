# Labb 1

# MySQL

Skärmdump som visar database explorer i IntelliJ med skapad person-tabell med data:

![MySQL i database explorer](bilder/bild2.png)

NOT: Ni ska även ha skapat en user som bara har access till databasen my_database, ingen bild krävs

# MongoDB

Skärmdump av databas på MongoDB Atlas med skapad movie-collection med data:

![MongoDBAtlas](bilder/bild3.png)

# SQL

Skärmdump som visar att ni klarat av första två sidorna på sqlbolt.com:s interaktiva tutorial

![SQL-bolt](bilder/bild4.png)

# Frågor som ni ska svara på (G-nivå)

Besvara frågorna med egna ord. Ge gärna exempel.

## Databaser och verktyg

1. Vad är en databas, och vad kan den användas till?
    ```
    en databas används för att lagra och organisera information.
   Som ett exempel använder banker databaser för att lagra konton, användare och liknande.
    ```
2. Vad används språket SQL till?
   ```
   SQL används för att kommunicera med relationsdatabaser. 
   Genom SQL kan man lägga till information, uppdatera information, ta bort information och hämta information.
   ```

## Tabeller och relationer

3. Vad är en tabell, en rad och en kolumn?
4. Vad är en primärnyckel, och varför behövs den?
5. Vad är en främmande nyckel?
6. Varför är det bra att lagra kunduppgifter och köp i olika tabeller?

## NoSQL

7. Vad menas med NoSQL, och hur kan information organiseras i en sådan databas?
8. Ge ett exempel på när en NoSQL-databas kan vara lämplig och förklara varför.

## SQL – hämta data från tabellen person

Skriv en SQL-fråga som svar på varje uppgift.

9. Hämta alla kolumner för alla personer i tabellen.

```sql
   SELECT *
   FROM people;
```

10. Hämta endast förnamn och efternamn för alla personer.

```mysql
   SELECT firstname, lastname
   FROM people;
```

11. Hämta förnamn, efternamn och inkomst för personer med en inkomst över 30 000.

```mysql
   SELECT firstname, lastname, income
   FROM people
   WHERE income > 30000;
```

12. Hämta alla personer födda före den 1 januari 1990.

```mysql
    SELECT *
    FROM people
    WHERE birthdate < '1990-01-01';
```

13. Hämta förnamn, efternamn och inkomst, sorterat efter inkomst från högst till lägst.

```mysql
    SELECT firstname, lastname, income
    FROM people
    ORDER BY income DESC;    
```

14. Räkna hur många personer som finns i tabellen.

```mysql
    SELECT COUNT(*)
    FROM PEOPLE;    
```

# VG-nivå

Dessa frågor ska besvaras med ett längre svar, minst en halv A4-sida:

1. En banköverföring avbryts efter att pengarna dragits från det första kontot.
   Vad kan konsekvensen bli, och hur kan en transaktion hjälpa?

2. Välj ett enkelt system, antingen en webbutik eller en chatt.
   Resonera om när en relationsdatabas respektive en NoSQL-databas
   kan vara lämplig. Motivera med hur informationen ska lagras och användas.


