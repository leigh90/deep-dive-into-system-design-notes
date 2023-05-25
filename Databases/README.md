## **KEY-VALUE DATABASES**

Definition: Use a simple key-value pairing method to store and quickly fetch the data with minimum latency.

**Features of a Key-Value database**
Because they ensure *minimum latency* that is constant time O(1) time(the data can be fetched in constant time) these kinds of DBs are used for *caching* application data. There is no query language required to fetch the data.

The key serves as a unique identifier and has a value associated with it. The value could be as simple as a string or as complex as an object graph.

Popular key-value databases include Redis, Hazelcast, Riak, Voldemort, Memcached.

Typical uses of a key-value db:

- caching
- persisting user state
- persisting user sessions
- managing real-time data
- implementing queues
- creating leaderboard in online games and web apps
- implementing a pub-sub system

Sample use cases
Microsoft uses Redis to handle the traffic spike on its platforms
Google Cloud uses Memcached to implement caching on their cloud platform.

## **TIME SERIES DATABASES**

Time Series Data is data containing data points associated with the occurrence of events with respect to time. These data points are tracked, monitored and aggregated based on specific business logic

This kind of data is ingested from *IOT devices*, *self-driving vehicles*, *industry sensors*, *social networks*, *stock market financial data* etc

**Definition:** these kinds of databases are optimized for tracking and persisting data that is continually read and written in the system over a period of time.

This kind of data allows us to track the behavior of a system over time and thus analyse patterns, anomalies that emerge.

Time-series data is used to run analytics which is used to make future business decisions and continually optimize products.

regular dbs are not optimized to handle time-series data. esp with IOT these databases are getting more popular.

Popular time-series dbs include *Influx DB*, *Prometheus*

Typical Use Cases for a time-series database include fetching data from IOT devices, managing data for running monitoring and analytics, writing an autonomous trading platform etc

Sample use cases

- IBM uses Influx DB to run analytics for real-time cognitive fraud detection.
- Spiio uses Influx DB to remotely monitor vertical lining green walls and plant installations.

## **WIDE-COLUMN DATABASES**

NO-SQL Database
Also known as column-oriented databases
Primarily used to handle massive amounts of data usually called Big Data.
Wide column databases are perfect for analytical use cases since they have a high performance and a scalable architecture. **They are built to manage big data while ensuring scalability, performance and high availability.**

wide-column dbs can store data in a record with a dynamic number of columns. A record can hold billions of columns.

Popular wide-column databases include Cassandra, HBase, Google BigTable, ScyllaDB etc

Sample use cases

- Netflix uses Cassandra in the analytics infrastructure.
- Adobe and other big guns use HBase for processing large amounts of data.