**WHAT IS CACHING?**

Caching is the <font color="orange">process of storing and accessing data from a cache.</font>
A cache is a <font color="orange">software or hardware component aimed at storing data so that future requests for the same data can be served faster.</font>
Caching was born out of the need to make responding to requests faster since accessing data from persistent data memory takes a considerable amount of time.
Caches are typically implemented using  <font color="orange">fast access hardware such as RAM and a software component. </font>This is because RAM is faster than disk-based hardware.
Caches make it possible to efficiently reuse previously retrieved or computed data.
When a new request arrives the requested data is searched for first in the cache. when it is found this is called cache hit. if it isn't that is cache miss. 

<font color="orange"></font>
Caching is also important because <font color="orange">it allows us to avoid making new requests or reprocessing data every time so that we can avoid overhead </font>e.g network overhead, network overhead, CPU usage *especially if requests are complex.* This can prolong the life our machines or servers. Plus reducing the overall number or requests reduces the overall amount of requests needed which may decrease the cost of infrastructure required.

Caching allows an application or website to reduce latency and provide high throughput(the number of network calls and request response cycles between the client and server within a stipulated amount of time). Caching intercepts all the requests heading towards the db and provides a response in a faster time.

When an application server requests data from the database it can be called the client and the db would be the server.
## 
## <font color="aqua">TYPES OF CACHING</font>

<font color="aqua">In-Memory Caching</font>
In this approach, cached data is stored directly in RAM, which is faster than the typical storing system.

the most common implementation of this type of caching is based on key-value databases. 

<font color="aqua">Database Caching</font>
Each DB typically comes with some level of caching which is used to avoid querying a database excessively.
<font color="orange">By caching the result of the last queries executed the database can provide the preciously cached data immediately this way for the period of time that the cached data is valid the DB doesn't have to process any queries.</font>
The most popular way of doing this is using a **hash table** to store key value pairs. 

<font color="aqua">Web Caching</font>
<font color="#89CFF0">Web-Client caching</font>
This is done on the client's side. 
The first time a browser loads a web page it stores the associated resources then the next time the same page is hit the browser can look in the cache and retrieve them in the user's machine. 

<font color="#89CFF0">Web Server Caching</font>
<font color="orange">Storing resources server side for re-use.</font>
This is useful when you have dynamically generated content that takes time to be generated.

<font color="#89CFF0">CDN Caching</font>
<font color="orange">Involves caching content like web pages and associated assets in proxy servers. </font>
When a request is made the proxy server  intercepts the request and checks to see if it has a  copy of the requested data if so it delivers it to the user and if not it forwards the request to the origin server. These proxy servers are placed in various locations globally and user requests are dynamically routed to the nearest one, this way you reduce network-latency 

Caching Dynamic Data
Dynamic data typically has a TTL. when it ends data is purged from the cache and the newly updated data is stored in it. (This is known as cache invalidation). Caching won't help if the data changes too often e.g the price of a stock, score of a cricket/baseball match.

Caching static data like web page assets, customer data that doesn't change like age, address, social id etc can be cached on the client(browser), CDN or server.

DO YOU NEED A CACHE?
![6038989893009408.jpeg](:/8f46853ce9654348aec79f06c357c2ea)

Typically you want to **cache frequently accessed data** instead of constantly polling the db for the same data.

Frequently requested data from the db with the help of several table joins can be cached **to avert the same joins query being run every time the same data is requested.** 
We can store user sessions in a cache. Key-value data stores are primarily used to implement caching in web applications.

## <font color="aqua">CACHING STRATEGIES</font>
<font color="#89CFF0">Cache-aside</font>
<font color="orange">Data is lazy-loaded into the cache so when a user makes a request the system first looks in the cache and it finds the data it returns it if not the application fetched data from the db and returns it to the user and then caches it for future requests.</font>

For data writes these are done directly to the DB. To avoid inconsistency between the DB and cache the data typically has a TTL after which the data in the cache is invalidated. 

This strategy is best for <font color="orange">read-heavy </font>workloads, the data doesn't get updated too frequently like customer data and can have a long TTL assigned to it.

<font color="#89CFF0">Read-through</font>
 <font color="orange">Similar to  cache aside except that here the cache automatically stays consistent with the db.</font>
The cache library takes the onus off maintaining consistency with the db. the app data in this strategy is also lazy-loaded in the cache only when the user requests its, the data model of the cache has to be consistent with the db since it is updated automatically by the library.

<font color="#89CFF0">Write-through</font>
 <font color="orange">Every write goes through the cache before updating the DB.</font>
This keeps consistency between the cache and db but adds latency to each write operation since the data also has to be written to the cache as well.
This strategy works well for use cases where we need strict data consistency between the cache and DB. It is generally used with other strategies to achieve optimized performance.


<font color="#89CFF0">Write-back </font>
 <font color="orange">Data is directly written on the cache instead of the DB and the cache after some time/a delay writes data to the DB.</font>
 This reduces the number of DB writes especially if the writes happen frequently like in a game. 

The risk with this is that if the cache fails before the DB Is updated you could lose all the data you have saved there. typically you would combine this with other strategies.

It's great though for managing deployment costs because write operations are fewer.
