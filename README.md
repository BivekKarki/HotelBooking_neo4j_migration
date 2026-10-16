# PRT563 Assessment 4 - Hotel Booking & Guest Services in Neo4j

Sydney Group 12

Bivek Karki (s395860)

Subodh Budhathoki (s394191)

Pramisha Shrestha (s399137)

Soman Ranabhat (s388032)

This has the scripts and data for migrating our Assessment 2 hotel database from a
relational model into Neo4j.

## What's in here

| File | What it's for |
|---|---|
| `import.txt` | Task 2 - constraints, indexes, loading the nodes and relationships, plus the checks we ran at the end |
| `queries.txt` | Task 3 - the four query use cases |
| `analytics.txt` | Tasks 4 and 5 - the GDS centrality and similarity scripts |
| the 12 `.csv` files | the data, exported out of our Assessment 2 SQLite database |

## How to run it

You need Neo4j 5.x with the Graph Data Science plugin installed. You do not
need APOC - we deliberately rewrote one of the queries so it would run on a
plain install.

1. Copy all 12 `.csv` files into the import folder of your database.
   
2. Run `import.txt` section by section from the top. Section 0 wipes the
   database first, so skip it if you don't want that.
3. Section 6 at the end prints the counts. You should get **1,397 nodes and
   3,773 relationships**. If not, re-run whichever section is short.
4. Then `queries.txt` for Task 3, and `analytics.txt` for Tasks 4 and 5.

## A note on the data

The data is sample data, not real client data. We generated it at a larger scale
than we used in Assessment 2 (60 guests, 250 bookings, 540 service requests)
because with the smaller dataset the centrality and similarity algorithms
didn't produce results that told us anything useful - too many nodes scored
the same. The schema, constraints and business rules are all unchanged from
Assessment 2. This is explained in Section 1.1 of the report.
