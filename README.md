# PRT563 Assessment 4 - Hotel Booking & Guest Services in Neo4j

Sydney Group 12
Bivek Karki (s395860), Subodh Budhathoki (s394191),
Pramisha Shrestha (s399137), Soman Ranabhat (s388032)

This is the repository that goes with our Assessment 4 report. It has the
scripts and data for migrating our Assessment 2 hotel database from a
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
   In Neo4j Desktop that's the `...` menu next to the database > Open folder
   > Import. The files need to sit directly in that folder, not in a
   subfolder inside it, otherwise `file:///` won't find them.
2. Run `import.txt` section by section from the top. Section 0 wipes the
   database first, so skip it if you don't want that.
3. Section 6 at the end prints the counts. You should get **1,397 nodes and
   3,773 relationships**. If not, re-run whichever section is short.
4. Then `queries.txt` for Task 3, and `analytics.txt` for Tasks 4 and 5.

Before running `analytics.txt`, check GDS is actually there with
`RETURN gds.version();`. The scripts use the `gds.graph.project` syntax.

## Expected results

The counts and query results we got are written into the comments in each
file so they can be checked against what the scripts produce.

| Check | What we got |
|---|---|
| Nodes / relationships | 1,397 / 3,773 |
| `serviceDelivery` projection | 907 nodes, 4,912 relationships |
| `guestServices` projection | 72 nodes, 307 relationships |
| Use case 1 - available premium rooms | 7 rows |
| Use case 2 - outstanding invoices | 80 invoices, $73,295.96 owing |
| Use case 3 - staff scorecard | 13 of 15 staff |
| Use case 4 - recommendations for guest 51 | Breakfast Buffet first, 14 peers |

The `serviceDelivery` projection is UNDIRECTED, which is why the relationship
count comes back as 4,912 rather than 2,456 - Neo4j stores each one in both
directions.

## A note on the data

The data is made up, not real client data. We generated it at a larger scale
than we used in Assessment 2 (60 guests, 250 bookings, 540 service requests)
because with the smaller dataset the centrality and similarity algorithms
didn't produce results that told us anything useful - too many nodes scored
the same. The schema, constraints and business rules are all unchanged from
Assessment 2. This is explained in Section 1.1 of the report.
