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

   En databas används för att lagra och organisera information.
   Som ett exempel använder banker databaser för att lagra konton, användare och liknande.

---

2. Vad används språket SQL till?

   SQL används för att kommunicera med relationsdatabaser.
   Genom SQL kan man lägga till information, uppdatera
   information, ta bort information och hämta information.

## Tabeller och relationer

3. Vad är en tabell, en rad och en kolumn?

   En tabell används för att organisera information i en databas.

   En rad representerar en enskild post till exempel en
   Person med sitt förnamn, efternamn och ålder.

   En kolumn representerar en specifik egenskap hos
   informationen, till exempel förnamn.
   Varje rad har ett värde för den kolumnen.

---

4. Vad är en primärnyckel, och varför behövs den?

   En primärnyckel är ett unikt värde som används för att indentifera varje rad i en tabell.
   Den används även för indexering, vilket gör det snabbare att söka efter information i databasen.
   En primär nyckel säkerställer också att varje rad har ett unikt värde och inte kan ha NULL

---

5. Vad är en främmande nyckel?

   En främmande nyckel är en kolumn som används för att koppla ihop två tabeller. Den referar till en primärnyckel i en
   annan tabell, vilket gör så att det kan relatera information mellan tabeller.
   Ett exempel är att en person ska kunna ha flera email kopplade till sig.

---

6. Varför är det bra att lagra kunduppgifter och köp i olika tabeller?

   Det är bra eftersom att man slipper lagra samma information flera gånger. Istället kan man koppla ihop tabellerna med
   hjälp av kundens ID. Detta gör databasen mer organiserad och enklare att hantera i långsiktigt.

## NoSQL

7. Vad menas med NoSQL, och hur kan information organiseras i en sådan databas?

NoSQL innebär att man använder en databas som inte bygger på traditionella relationella tabeller. Informationen kan
exempelvis organiseras som dokument, nyckel-värde-par eller grafer.
   
---

8. Ge ett exempel på när en NoSQL-databas kan vara lämplig och förklara varför.

En NoSQL databas kan vara lämplig för en chattaplikation eftersom meddelanden kan innehålla olika typer av information
till exempel text, bilder och tidsstämplar. Det gör det enklare att lagra informationen med olika strukturer.

## SQL – hämta data från tabellen person

Skriv en SQL-fråga som svar på varje uppgift.

9. Hämta alla kolumner för alla personer i tabellen.

```sql
   SELECT *
   FROM people;
```

10. Hämta endast förnamn och efternamn för alla personer.

```mysql
   SELECT first_name, last_name
   FROM people;
```

11. Hämta förnamn, efternamn och inkomst för personer med en inkomst över 30 000.

```mysql
   SELECT first_name, last_name, income
   FROM people
   WHERE income > 30000;
```

12. Hämta alla personer födda före den 1 januari 1990.

```mysql
    SELECT *
    FROM people
    WHERE birth_date < '1990-01-01';
```

13. Hämta förnamn, efternamn och inkomst, sorterat efter inkomst från högst till lägst.

```mysql
    SELECT first_name, last_name, income
    FROM people
    ORDER BY income DESC;    
```

14. Räkna hur många personer som finns i tabellen.

```mysql
    SELECT COUNT(*)
    FROM people;    
```

# VG-nivå

Dessa frågor ska besvaras med ett längre svar, minst en halv A4-sida:

1. En banköverföring avbryts efter att pengarna dragits från det första kontot.
   Vad kan konsekvensen bli, och hur kan en transaktion hjälpa?

Om en banköverföring nu skulle avbrytas efter att pengarna har dragifts från det första kontot kan det då uppstå
problem. Exempelvis kan pengarna försvinna från den som skickar pengar konto medan att den som tar emot får inga pengar.
Detta kan leda till att saldot på båda kontonen blir felaktiga och att banken skulle då behöva undersöka vad som har
hänt för att rätta till problemet.

För att förhindra den här typen av problem använder man transaktioner i databaser. En transaktion innebär helt enkelt
att flera operationer behandlas som en enda operation. Det innebär då att antingen genomförs alla operationer eller så
avbryts hela transaktionen.

I en banköverföring skulle detta exempelvis innebära att banken först drar pengar från sändarens konto och sedan lägger
till samma summa på mottagarens konto. Om något går fel under denna process kommer ändringarna återställas.

Några viktiga SQL-kommandon som används just för detta är ```COMMIT``` och ```ROLLBACK```. ```COMMIT``` används för att
spara ändringarna när alla operationer har lyckats. ```ROLLBACK``` som namnet säger används då istället för att ångra
ändringarna och gå tillbaka i fall något går fel.

Ett exempel på hur en banköverföring kan se ut i SQL:

```mysql
START TRANSACTION;

UPDATE accounts
SET balance = balance - 500
WHERE id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE id = 2;

COMMIT;
```

Om något går fel innan transaktionen har genomförts kan man som sagt använda sig av ```ROLLBACK``` istället för
```COMMIT``` I just denna kod exempel.

Transaktioner är därför väldigt viktiga i system där information måste vara korrekt, exempelvis banker och
betalningssystem. Utan de skulle det finnas ännu större risk att information blir felakigkt om något avbryts under
processen.

2. Välj ett enkelt system, antingen en webbutik eller en chatt.
   Resonera om när en relationsdatabas respektive en NoSQL-databas
   kan vara lämplig. Motivera med hur informationen ska lagras och användas.

Mitt exmpel kommer just vara en webbutik. I en webbutik kommer man behöva lagra flera olika typer av information, som
exempel kunder, produkter, beställningar och betalningar. Informationen behöver även kunna kopplas ihop så att man
exemepelvis kan se vilka produkter en viss kund har köpt.

En relationsdatabas, just detta exempel MySQL (Då vi använder det i just denna kurs), skulle passa bra för en webbutik
eftersom informationen har tydliga relationer till varandra. Man kan ha flera seperate tabeller för kunder, produkter,
och beställningar. Varje kund kan ha flera beställningar och varje beställning kan inneha flera produkter.

Och genom att använda sig av primärnyckalr och främmande nycklar kan man då koppla ihop tabellerna. Det gör det enklare
att hämta den nödvändiga informationen, exempelvis vilka beställningar som tillhör en viss kund. En annan fördel då med
relationsdatabaser är att man kan använda sig som tidigare nämnt transaktioner för att säkerställa att informationen
blir korrekt. Det är särskilt viktigt vid betalningar och beställningar eftersom man vill inte att informationen blir
felaktigt.

I en NoSQL-database, MongoDB som exempel (Once again är för det är det vi använder i denna kurs), skulle självklart
också kunna användas i en webbutik. Då istället för traditonella tabeller kan man lagra informationen i dokument med ett
JSON liknande format. Ett produktdokument skulle kunna då innehålla produktens namn, pris, beskrivning och olika
egenskaper.

Fördelen med NoSQL är då att infomrationenn kan vara mer flexibel och inte måste ha en viss struktur (Vilket är varför i
en chatt applikation kan vara ganska bra, eftersom en chatt kan innehålla bilder med annat.) Olika produkter behöver
exempelvis inte ha samma egenskaper. En dator kan ha information om CPU och RAM-minne, dock en tröja istället kan ha
storlek och färg. Med MongoDB kan då dessa egenskaper lagras direkt i respektive produktdokument utan att man behöver ha
samma kolumner för alla produkter.

Själv så tycker jag en relationsdatabass passar bäst i själva grunden i en webbutik eftersom kunder, beställningar och
betalningar har tydliga relationer till varandra och informationen behöver då vara korrekt. Däremot skulle NoSQL kunna
vara bra alternativ för exempelvis en produktkatalog eller en stor webbutik som säljer massor av grejor där olika
produkter kan ha väldigt olika egenskaper.