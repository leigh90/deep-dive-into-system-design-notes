Data stream processing has become important with the rise of the amount of data we collect especially now with IOT devices that generate and transmit data at an unprecedented rate. They also rely on data to operate as well as communicate with other devices.

We need to colloct and analyse this data to make better business decisions as well as analyse app performance based on up-time.

better business decision allow us to create more customer-centric products and increase customer loyalty.

### <font color="aqua">DATA INGESTION</font>
Data ingestion is the process of collecting data streaming in from different sources and preparing it to be processed by the system.

### <font color="aqua">Layers of data processing setup</font>
- Data Collection
- Data 	query 
- Data processing
- Data visualization
- Data storage
- Data security



![5250130053693440.jpeg](:/a72de9ddd9a1418d9661fd591836a26f)

<font color="orange">Data Standardization</font>

Most of the data we collect is in a non-homogenous unstructured format so it needs to be processed to be uniform and fit for processing. this data standardization is done in the data collection and preparation layer.

the data is then processed based on the business requirements and is classified into different flows and routed to different destinations.

then analytics is run on the data, using different analytical models such as statistical analytics, text analytics etc

Once analytics is run we visualise the data to be presented to stakeholders on a tool like kibana

Then the data is moved to secure storage 

There's 2 ways to ingest data
- Real time 
- In batches
Real-time ingestion is used by systems that read medical data like heartbeat and blood pressure monitors via wearable IOT sensors.
It's also preferred for systems that handle financial data like stock markets, events etc.

For systems that read trends over time we can ingest data in batches for example a system that shows popularity of a sport in a given region over certain time.

<font color="aqua">Challenges of Data Ingestion</font>
1. It's a slow process. Often you're ingesting data from multiple sources each likely in it's own format, syntax, attached metadata. You need to be able to transform it into a standard format like JSON that can be understood by your system.
2. It can be tedious. It takes alot of computational resources and time. Flowing data can be stages at several stages in the pipeline, processed and then moved ahead. You also have to authenticate and verify it at each stage to meet the org's security standards. This can take weeks or even months.
3. It is a resource intensive process hence can be quite expensive from the computational resources to the engineering resources.
4. Moving around data is tricky and opens you up to the risk of breach.

An important thing to keep in mind is that real time analytics is not all that accurate or holistic since the analytics run on a limited amount of data. On the other hand batch processing tends to be more accurate really coz you have more to work with and more time to analyse it.


<font color="aqua">Data Ingestion Use Cases</font>
 
 <font color="aqua">Data Pipelines</font>
Data pipelines <font color="orange">facilitate the efficient flow of data from one point to another and enable developers to apply filters on the data streaming-in real time </font> 

They work on a set of rules predefined by the engineering teams and are routed accordingly without manual interventions through the entire flow from extraction, combination, validation and convergence.



 <font color="#89CFF0">Features of Data Pipelines</font>
 - Ensure smooth flow of data 
 - Enable business to apply filters and business logic
 - Avert bottlenecks and redundancy in the flow
 - Facilitate parallel processing of data
 - Protect data from being corrupted

Traditionally we used ETL systems to manage all the data's movement but the thing is it doesn't allow for real time streaming. 
<font color="aqua">ECTRACT, TRANSFORM, LOAD (ETL)</font>

<font color="orange">Extract</font> - Fetch data from the source(s)
<font color="orange">Transform</font> -  Standardize the heterogeneous data into a standardized format.
<font color="orange">Load</font> - Moving the data to a warehouse or other storage location.
ETL is done in batches. 

<font color="aqua">Distributed Data Processing</font>
<font color="orange">Distributed data processing means diverging large amounts of data to several nodes running in a  cluster for parallel processing. </font>
This is opposed to a centralized system the tasks are queued to be processed one by one.
The nodes are run in parallel and work in conjunction and coordinated by a node-coordinator.
Since the nodes are distributed and run in parallel this allows the system to be scalable and highly available. 


![5116764474048512.jpeg](:/8bb73334e03e48b5a253dd6a6b0af26b)

A good example of a node-coordinator that is widely used in Apache Zookeeper.

<font color="aqua">Distributed data processing technologies</font>
- Map reduce - Apache Hadoop 
- Apache Spark 
- Apache storm  - processing real-time streaming data.
- Apache Kafka - typically used for notification systems, managing streams of data, monitoring website activity and metrics, messaging and log aggregation. 

<font color="aqua">Lambda Architecture</font>
Lambda architecture uses batch and real-time streaming data processing to reduce the latency of batch processing.


![4614345407332352.jpeg](:/f8df09a51c9e400184f13ff74f46c38f)


#### <font color="aqua">Layers of the Lambda architecture</font>
- Batch layer - deals witth the results of the batch processed data 
- Speed layer - gets data from the real time stream processing 
- Serving layer - combines the results obtained from both layers.

#### <font color="aqua">Layers of the Lambda architecture</font>
All the data flows through a single streaming pipeline flowing the data of both real-time and batch processing through a streaming pipeline reducing the complexity of managing separate layers for processing data. 

Kappa only has two layers: Speed for stream processing and Serving which is the final layer. 
Kappa is preferred if the batch and the streaming analytics results are fairly identical and lambda is preffered if not. 


<font color="orange"></font>