# LECTURE DAY 1
# Dimension Data Modeling 
## Dimensions
### Are attributes of a entity 
    - some of these dimensions may identify an entity
    - others just attributes
### Dimension come in two flavors
    - slowly changing
    - fixed
### Knowing your data consumer
    - Data analyst / Data scientists 
        -  Sould be very easy to query. nNot many complex data types.
    - Other data engineers 
        - Sould be compact and probably arder to query. Nested types are okay
    - ML models
        - depends on the model and how its trained
    - Customers
        - should be a very easy to interpret chart
### OLPT vs master data vs OLAP
    - OLPT (Online transactions processing)
        -  OPtimizes for low-latency
        (one user one entity)
    - OLAP (Online analytical Processing)
        - Optimizes for large volumen, group by queries, minimized JOINs
    - Master Data
        - Optimizes for completenses of entity definitions, dedupled.
### Mismatch needs= less business value.
    - Some biggest problems in data enginering occur when data is modeled for the wrong consumer!
    - be sore the customer are a valuable user and undestand all steps.
### OLPT and OLAP is a Continuum
    Production database snapshots => Master Data => OLAP Cubes => Metrics
### Cumulative table desing
     - core components
        - 2 dataframes (yesterday and today)
        - FULL OUTER JOIN the two data frames together
        - COALESCE values to keep everything around
        - Hang onto all history.
    - Usages
        - Growth analytical at Facebook (dim_all_users)
        - State transition tracking (we will cover this more analytics track, applying analytical patterns later)
 ### Comulative table desing (cont)
     - Strengths
        - Historical analysis without shuffle (A shuffle occurs when a distributed engine (e.g., Spark, Flink, Hive, Synapse, BigQuery) must move data across the network to satisfy an operation that requires data with the same key to be colocated.)
        - Easy "transition" analysis
    - Drawbacks
        - Can be backfilled sequenrially.
        - Handling PII data can be a mess since delete/inactive users get carried forward
### The compactness vs usability tradeoff
     - The most usable tables usually
        - Have no complex data 
        - Easily can be manipulated with WHERE and GROUP BY.
    - The most compact tables (no human readable)
        - Are compressed to be as small as possible and can't be queried directly until they're decoded.
    - The middle-ground tables.
        - use complex data types (e.g. ARRAY,MAP and STRUCT), making querying trickier but also compacting more.
    - When would you use eac type of table?
        - More compact
            - Online systems where latency and data volumes matter a lot. Consumers usually highly technical.
        - Middle-ground 
            - upstream staging/master data the majority of consumers are other data engineers
        - More usable 
            - When analytics is the main consumer and the majority of consumers are less technical.
### Struct vs Array vs Map

    - Struct
        - Key are rigidly defined compresion is good!
        - Values can be any type
    - Map
        - Keys are loosely defined, compresion is okay!
        - Values all have to be the same type
    - Array 
        - Ordinal
        - List of values that all have to be dame type.
### Termporal cardinality explosions of dimension
    - Whan you add a temporal aspect to your dimension and the cardinality increases by a least 1 order of magnitude
        - example:
            Airbnb has ~ 6 millions listings
                If we want to know the nightly pricing and available of each night for the next year 
                    that's 365*6 millions or about ~ 2 billions nights
                Should this data be:
                    Linting-level an array of nights?
                    listing night level with 2 billion rows?
                If you do the sorting, parquet will keep these two about same  size
### Badness of denormalized temporal dimensions
    - If you explode it out and need to join other dimension, Spark shuffle will ruin your compresion!
### Run lenght encoding compresion
    - Probably the most important compresion technique in big data right now. It's why parquet file format has become so sucessful.
    - Suffle can ruin this. (Be careful) Suffle happens in distributed enviroments whrn you do a JPIN and GROUP BY.
<img src="media/img_1.png" width="400">
</p>
After a join , Spark may mix up ordening of the rows and ruin your compression.


 
