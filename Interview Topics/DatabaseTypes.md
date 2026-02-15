# ✅ **Database Categories with 2–3 Products & Uses**

***

## **1. Relational Databases (RDBMS)**

Relational databases organize data in tables with rows & columns and enforce ACID guarantees.  
**Products**

*   **MySQL** — Popular open‑source RDBMS used for web apps, transactional systems. [\[databasetown.com\]](https://databasetown.com/examples-of-relational-database/)
*   **PostgreSQL** — Advanced open‑source ORDBMS known for extensibility and strong standards compliance. [\[databasetown.com\]](https://databasetown.com/examples-of-relational-database/)
*   **Microsoft SQL Server** — Enterprise RDBMS for business applications and analytics. [\[databasetown.com\]](https://databasetown.com/examples-of-relational-database/)

**Uses**: Transaction processing, structured data storage, financial systems, CRUD apps.

***

## **2. Key-Value Stores**

Simple key→value lookups with extremely high throughput.  
**Products**

*   **Redis** — In-memory key–value store supporting rich data structures. Used for caching, sessions, real-time analytics. [\[redis.io\]](https://redis.io/nosql/key-value-databases/)
*   **Amazon DynamoDB** — Fully managed, highly scalable key–value and document store. Ideal for serverless, high-traffic workloads. [\[theskilledcoder.com\]](https://theskilledcoder.com/posts/system-design/key-value-stores)
*   **Memcached** — Lightweight, in‑memory caching system. [\[geeksforgeeks.org\]](https://www.geeksforgeeks.org/system-design/memcached-vs-redis/)

**Uses**: Caching, sessions, rate limiting, leaderboards, quick lookups.

***

## **3. Document Databases**

Store JSON/BSON documents with flexible schemas.  
**Products**

*   **MongoDB** — Widely used document store with flexible schema and strong developer ecosystem. [\[milvus.io\]](https://milvus.io/ai-quick-reference/what-are-some-examples-of-popular-document-databases)
*   **Couchbase** — Document + key-value hybrid designed for real‑time applications. [\[milvus.io\]](https://milvus.io/ai-quick-reference/what-are-some-examples-of-popular-document-databases)
*   **Firebase Firestore** — Cloud-hosted document database for real-time apps. [\[milvus.io\]](https://milvus.io/ai-quick-reference/what-are-some-examples-of-popular-document-databases)

**Uses**: Content management, e‑commerce catalogs, user profiles, mobile apps.

***

## **4. Time-Series Databases**

Optimized for time‑stamped data and high ingestion rates.  
**Products**

*   **InfluxDB** — Purpose-built time-series DB for metrics, IoT, logs. [\[influxdata.com\]](https://www.influxdata.com/comparison/influxdb-vs-timescaledb/)
*   **TimescaleDB** — PostgreSQL extension optimized for time-series workloads. [\[influxdata.com\]](https://www.influxdata.com/comparison/influxdb-vs-timescaledb/)
*   **Prometheus** — Time-series DB for monitoring and observability. [\[calmops.com\]](https://calmops.com/database/timeseries-databases/)

**Uses**: Monitoring, observability, IoT sensor streams, financial tick data.

***

## **5. Graph Databases**

Store data as nodes and edges to represent relationships.  
**Products**

*   **Neo4j** — Native graph DB used for recommendation engines, fraud detection. [\[index.dev\]](https://www.index.dev/skill-vs-skill/database-janusgraph-vs-neo4j-vs-dgraph)
*   **JanusGraph** — Distributed open-source graph DB for very large graphs. [\[sourceforge.net\]](https://sourceforge.net/software/compare/JanusGraph-vs-Neo4j/)
*   **Dgraph** — High‑performance distributed graph database. [\[index.dev\]](https://www.index.dev/skill-vs-skill/database-janusgraph-vs-neo4j-vs-dgraph)

**Uses**: Social networks, fraud detection, knowledge graphs, identity graphs.

***

## **6. Columnar Databases**

Store data by columns for analytical workloads.  
**Products**

*   **Amazon Redshift** — AWS cloud data warehouse using columnar storage. [\[estuary.dev\]](https://estuary.dev/blog/columnar-database/)
*   **Google BigQuery** — Serverless columnar analytics engine. [\[estuary.dev\]](https://estuary.dev/blog/columnar-database/)
*   **ClickHouse** — Open-source, extremely fast column-store for real‑time analytics. [\[estuary.dev\]](https://estuary.dev/blog/columnar-database/)

**Uses**: BI dashboards, OLAP queries, large-scale analytics, log analysis.

***

## **7. In‑Memory Databases**

Keep data in RAM for ultra‑fast access.  
**Products**

*   **Redis** — In‑memory DB supporting persistence & rich data structures. [\[geeksforgeeks.org\]](https://www.geeksforgeeks.org/system-design/memcached-vs-redis/)
*   **Memcached** — Simple, high-performance in-memory cache. [\[geeksforgeeks.org\]](https://www.geeksforgeeks.org/system-design/memcached-vs-redis/)
*   **VoltDB** — In‑memory, ACID-compliant OLTP database. [\[codestudy.net\]](https://www.codestudy.net/blog/difference-between-in-memory-cache-and-in-memory-database/)

**Uses**: Real-time analytics, caching, low‑latency processing, session stores.

***

## **8. Search Databases (Full‑Text Search Engines)**

Optimized for text search, log analytics, and observability.  
**Products**

*   **Elasticsearch** — Distributed search engine widely used in the ELK stack. [\[coralogix.com\]](https://coralogix.com/guides/elasticsearch/elasticsearch-vs-opensearch-key-differences/)
*   **OpenSearch** — AWS‑led open-source fork of Elasticsearch. [\[coralogix.com\]](https://coralogix.com/guides/elasticsearch/elasticsearch-vs-opensearch-key-differences/)
*   **Apache Solr** — Enterprise search platform built on Lucene. *(Solr not explicitly in search results, so omitted for citation consistency)*

**Uses**: Search bars, log analytics, APM/observability, security analytics.

***

## **9. Vector Databases**

Store high‑dimensional embeddings for semantic search & AI.  
**Products**

*   **Pinecone** — Fully managed vector DB for semantic search & RAG systems. [\[tensorblue.com\]](https://tensorblue.com/blog/vector-database-comparison-pinecone-weaviate-qdrant-milvus-2025)
*   **Weaviate** — Open‑source vector DB with built‑in embedding modules. [\[tensorblue.com\]](https://tensorblue.com/blog/vector-database-comparison-pinecone-weaviate-qdrant-milvus-2025)
*   **Milvus** — Open‑source, scalable enterprise vector store. [\[tensorblue.com\]](https://tensorblue.com/blog/vector-database-comparison-pinecone-weaviate-qdrant-milvus-2025)

**Uses**: AI search, recommendation, RAG for LLMs, similarity search (text/image/audio/video).

***

## **10. NewSQL Databases**

Combine SQL consistency with horizontal scalability.  
**Products**

*   **Google Cloud Spanner** — Globally consistent, horizontally scalable SQL database. [\[expertbeacon.com\]](https://expertbeacon.com/google-cloud-spanner-the-future-of-newsql-databases/)
*   **CockroachDB** — Distributed SQL database inspired by Spanner. [\[lukeiscoder.com\]](https://lukeiscoder.com/2025/12/16/designing-distributed-sql-database-google-spanner-yugabyte-cockroachdb/)
*   **YugabyteDB** — Distributed SQL database with strong PostgreSQL compatibility. [\[db-engines.com\]](https://db-engines.com/en/system/CockroachDB%3BGoogle%20Cloud%20Spanner%3BYugabyteDB)

**Uses**: Global-scale transactional systems, financial ledgers, multi-region apps.

***
