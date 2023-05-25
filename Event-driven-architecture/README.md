23/01/2023 12:48
Blocking - <font color="orange">This is when the flow of execution is paused while waiting for a process to complete.</font>
You could have a function that calls like 10 others within it but they other 9 are blocked because you are waiting on a response from function 1.
Non-blocking <font color="orange">When the flow doesnt wait for the external function called to return a response it just continues to execute the following lines of code.
</font>
Keep this could be inconsistent since the function youre waiting on could error out but you still continue.
This approach facilitates IO intensive operations IO intensive operations include the disk and other hardware based operations, communications, network operations

<font color="aqua">What is an event? </font>
We typically have two kinds of processes. Either CPU Intensive and IO intensive. IO means events. An event can be anything from a tweet to a click of a button to a http request, an ingested message, a change in the value of a variable etc

in web2.0 realu-time apps have a lot of events like the request-response cycles between the client and server, an online game, a messaging app etc

Too many event happening is called a stream of events.

Non-blocking architecture is also known as reactive or event driven architecture. 
Frameworks like NodeJ, frameworks like in the Java ecosystem like Play, Akka are non-blocking by nature and are built for modern hig IO apps

They can handle a big number of concurrent connections with minimal resource consumption. 

Reactive architecture means reacting to events occuring regularly, the code is written to monitor the stream and react to the events. 
Event-driven architecture is all about processing asynchronous data streams. The application becomes inherently asynchronous.

NodeJS is a single-threaded non-blocking framework written to handle more IO-intensive tasks. It has an event loop architecture.

<font color="aqua">WEBHOOKS</font>

What is a webhook?

<font color="orange">It's effectively a way of saying I'l call you when I have something new for you, you do your thing, I'll let you know. </font>

Typically requesters used to poll a server for updates say a sports website outside apps would poll the site regularly for new info. This however puts a load on the server. So instead of the apps checking the server for new stuff the server sends them stuff when there is something to send. 

<font color="aqua">How do webhooks work?</font>
Consumers register a HTTP endpoint with the producer with a unique API key. When new information is available the server fires a HTTP event to all the registered endpoints notifying them of the latest update. (Its like call me on this number when something happens)

![4954686534713344.jpeg](:/e02115c683d844f99671efc4ab3483dc)

Browser notifications are one example of Webhooks. Instead of visiting the websites every now and then for new info, they notify us when they publish new content.

<font color="orange">Side note</font>
Typically several modules work in conjuction they often share RAM and the DB

<font color="orange">Shared nothing architecture</font> is where several modules do not share anything in terms of resources like RAM and the DB. The goal is to eliminate single points of failure by having each module use its own RAM and hard disk so if one system goes down the others remain online and unaffected. This helps with scalability and performance

<font color="orange">Hexagonal Architecture/ Ports and Adapter Pattern </font>
Here you have the main business logic insulated at the core and have an outer layer where you have a port and an adapter. 
The ports act like and interface and all the input to the app goes through it, 

Exrternal entitties do not have direct access to the business logic.It lies isolated at the center and all the IO input output is at the edges of the structure.
 Adapters convert the data obtained from the ports to be processed by the business logic.
 

Ports form the outer layer of the architecture. They act as an interface, an API to all the external requests. They prevent any external request to have any sort of direct interaction with an application resource.
 P.s the hexagonal shape has nothing to do with the pattern it's just another example of the non intuitive nature of tech jargon
 
 Also note this approach is an evolved layered architecture, in terms of simiplicity.
 
<font color="orange">Peer-to-Peer Architecture </font>
A P2P network is one in which computers also known as nodes can communicate with each other without a central server. The absence of a central server rules out the possibility of a single point of failure.

All the computers in a network have equal rights. A node can be a seeder and a leecher at the same time.

A seeder is a node that hosts the information on its system and provides the bandwidth to download the information while a leecher downloads the information from the network.

Think torrenting downloads


![5252606806982656.jpeg](:/14fea430a723482c8491bfacff3f1b8f)


<font color="orange">Downsides of a centralised system</font>
1. Security
2. Prone to attacks by natural disasters, bankruptcy 
3. You're at the mercy of the owner of the central server.
4. 
<font color="orange">Why use a decentralised system</font>

1. Nobody has control over your data, and nobody has the power to delete it because all the participating nodes in a P2P network have equal rights. During a zombie apocalypse, when the huge corporation servers are dead or on fire, we can still communicate with each other via a peer-to-peer connection.

2. Peer to peer file sharing. like bit torrent, is cheap, fast esp for large files.

In P2P information is exchanged over TCPI IP just like it does over HTTP. P2P design has an overlay network over the TCP IP which enables the users to connect directly. All the nodes are indexed and discoverable 
<font color="aqua">Types of P2P networks</font>
1. Unstructured Network

Nodes/peers keep connecting with each other randomly. There is no structure or rule simply connect and grow the network.

Nodes are not indexed, to search the data we scan each and every node in the network. The search is 0(n) in complexity, where n is the number of nodes in the network. So if you're searching for a file, and its only available on one node you have to search all the the nodes which could be billions

This can be very slooow.

2. Structured Network

For a a structured network we have nodes that are properly indexed. This makes it easier to search for specific data.

It implements a distributed hash table to index the nodes. This index is just like a book index where we check to find a piece of information in the book rather than searching through every page.

3. Hybrid Model.

This is a combination of P2P and Client-to-Sever.
You set up a centralized server and then use a p2p network for availability since to take it down you would need to take down all the nodes in the network. The p2p app can scale to the moon without putting a load on any one node. The app scales with more and more peopl using the app.


<font color="aqua">Decentralised Social Networks</font>

decentralized social networks have servers spread out across the globe hosted by individuals like you and me. Nobody has autonomous control over the network.

Scalability is directly proportional to the the number of users joining and active on the network.

the data is encrypted for everyone, including the network’s technical team.
The data, just like a blockchain ledger, is replicated across the nodes. So, even if a few nodes go down, our data is not lost.
These social networks are written on protocols and software that are open source so that the community can keep improving the code and keep building awesome features.

<font color="aqua"></font>

