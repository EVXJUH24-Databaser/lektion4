---
author: Lektion 4
date: MMMM dd, YYYY
paging: "%d / %d"
---

# Teams lektion 4

## Agenda

1. Frågor och repetition
2. Genomgång av övningar (36 - 43)
3. Introduktion till relationer
4. Introduktion till joins
5. Övning med handledning
6. Quiz frågor

---

# Fråga

Om man väljer att börja om på projektet måste man fortfarande ha med så det går att spara till fil eller räcker det med databas?

# Svar

Det räcker med databas. Ni måste inte spara till fil.

---

# Fråga

När man använder `SERIAL` och en `INSERT INTO` inte fungerar (pga villkor tex), kan du bekräfta att den SERIAL som SKULLE ha använts förbrukas?
EX: i din video om realtionsdatabas så skriver du kommentar #1 följd av en ogiltig INSERT INTO. Sen kommenterar du mera utan anmärkning.
när man tittar i tabellen senare ser man att kommentaren #2 inte kommer med.

# Svar

Om en INSERT INTO går fel, med `SERIAL`, så kommer ett nummer skippas.

- INSERT -> 1
- INSERT -> 2
- INSERT (fail, 3 skippas)
- INSERT -> 4

---

# Hur sparas listor av saker i SQL-databaser?

En kolumn kan endast spara ett värde och inte flera som en array. Istället hanteras listor av saker med "relationer".

En relation bildas när en rad i en tabell har en länk till en annan rad, oftast i en annan tabell.

---

# Exempel relation: Människor <-> Husdjur

```md
humans:

| name   | age |
| ------ | --- |
| Bob    | 30  |
| Rachel | 27  |

pets:

| name    | owner  |
| ------- | ------ |
| Charlie | Bob    |
| Oskar   | Bob    |
| Nevad   | Rachel |
```

---

# Primary keys och foreign keys

En relation är en länk mellan två rader. För att skapa en länk så används primary keys och foreign keys.

**Primary key**: en identifierande kolumn. Den är självstående och är typiskt sätt en `SERIAL` eller `UUID`.

**Foreign key**: en refererande kolumn. Refererar till en primary key.

För att referera till en primary key har foreign keys alltid samma värde som en primary key. En primary key kan dock vara helt unik, och utan foreign key.

I exemplet med människor och husdjur så är `humans:name` en primary key och `pets:owner` en foreign key. Detta är dock något som skaparen av tabellerna har bestämt.

---

# Typer av relationer

## One-to-One

En rad refererar till exakt en rad. Förekommer sällan.

## One-to-Many och Many-to-One

En rad refererar till flera (0-n) rader. One-to-Many och Many-to-One är samma sak från olika perspektiv.

Exempel: människor <-> husdjur, användare <-> kommentarer

## Many-to-Many

Flera rader refererar till flera rader. Om One-to-Many går åt båda hållen så är det Many-to-Many. Skapas med "junction" tabeller.

Exempel: användare <-> git repos, spelare <-> spel

---

# Quiz frågor

- Vad är en connection string?
- Varför skall man inte lägga in query-argument genom string concatenation?
- Namnge 3 constraints
- Är `SERIAL` en constraint?
- Det finns "primary" keys och ??? keys?
- Vad är det för skillnad på en primary key och en foreign key?
- Om man vill spara en lista med saker i PostgreSQL, vad gör man?
- Alla har en pappa, och endast en pappa. Vad är det för typ av relation i SQL sammanhang?
- Vad är det för skillnad på Many-to-One och One-to-Many relationer?
- Är GitHub repos + users en form av Many-to-Many relation?
- Hur implementeras Many-to-Many relationer med tabeller?
