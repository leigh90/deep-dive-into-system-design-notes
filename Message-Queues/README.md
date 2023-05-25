A message queue routes messages from source to destination or sender to the receive in the FIFO order. First message in is the the first one out.

Message queues also support priority based message delivery. Where messages have a prioriy assigned to them and the queue processes the messages based on this. These are called priority queues. 

Add/Facilitate asynchronous behaviour. - Asychronous behaviour allows the modules to communicate in the background without hindering on-going tasks. For example during sign up a sitw will redirect you to the homepage before email confirmation is complete while you are routed to the home page the server sends the email. This task of sending the email is assigned to a message queue. 

Facilitate cross-module communication. In a heterogenous environment you can temporarily store messages till they are processed and consumed. for example in sending email you dont need both receiver and sender to be online at the same time. AN email is sent and the message is stored temporarily in the email sever till the receiver comes online and reads.

Message queues are used to implement notifications systems similar to Facebook notifications. 

You can use message queues to run batch jobs like say in the stock market app that cached trades and then updated the db at regular intervals. 

You can provide rules while routing messages through a queue. For instance priority, Message queues have many features includemessage acknowledgements, retrying failed messages, etc 

MESSAGE QUEUE MODELS 

Publish-Subscribe Model
One or more producers broadcast messages to multiple consumers. For ecample a newspaper service where users subscribe and the news is delivered to them daily.




![5842943451594752.jpeg](:/edcc953cecec422a8e76abcc1e9726c4)


Message queues here use exchanges that push the messages to the queues that push the message queues based on the exchange type and set rules. 

Different kinds of exchanges exist direct, topic, headers, fanout. 

Fanout - pushes the messages to the queue and consumers receive the broadcast. The relationship between the exchange and the queue is called a fanout.

This model is responsible for delivering real-time news, updates, notifications and social apps to the end-users. The end-users  follow certain pages and are updated on the content regularly.

Point to Point Model

Typically one producer to one consumer. You can have multiple producers and consumers but a message can on be recieved by one consumer. It is not a broadcast.


![6547336517910528.jpeg](:/a92ec410cd4149f69bf4846b43edd974)


Message protocols

AMQP - Advanced Message Queue Protocol 
STOMP - Simple/Streaming Text Oriented Message Protocols. 

HOW NOTIFICATION SYSTEMS WORK WITH MESSAGE QUEUES

Pull-Based Approach 
Soo say you have a social media, and you want to show a user new posts from their connections. WIthout a message queue what you do is have poll a user's connections and then check for posts from each of them. If there are new posts we pull them and display them.  We can also send the user notifications about new posts, and track these notifications using a boolean notification counter in the user table and adding and AJAX poll query from the client for new notifications.

When the db finds new posts it changes the counter to true and when the counter is true in responding to the Ajaz poll request, the application sends a notification to the user that you have recent posts made by connections



![6667990026158080.jpeg](:/e030886c49414694b26d5458f407c816)


Theres 2 downsides to this appraoch
1. Its an expensive operation to poll the db so often it consumes lots of bandwidth and places a heavy load on the db
2. The post displayed wont be in real time since you have to poll the db.

Push-based Approach

When you use a message queue,  you have a distributed transcation. So say a user creates a post. One transcaction updated the db and anothet sends the post to a message queue. on receiveing the message the queue asynchronously and immediately pushes the post to the user;s connections that are online. This way they dont need to poll the queue for new posts.

You can also set a TTL for the queue to last until all the offline users have seen the post. You can also use a separate key-value store to store the user details that you need to be able to push notifications. this way you dont need to poll the DB for the user's connections etc


![6581126971785216.jpeg](:/d456cfd90811487eb3dab159085800b1)

You need to think about distributed transactions. Say the database push is successful but the queue push fails you can either let it be and write a query to poll the db for new updates or you can roll back the entire transaction. 


Post creation is an event that a user triggers in the application. Similar events are liking a post, photo, video, watching a live-stream and so on.

Handling Concurrent Requests with Message Queues
when millions of users around the world update and entity concurrently  we can queue all the update requests using a high throughput message queue. Then process them sequentially in a FIFO queue. 



