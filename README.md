# rabbitMQ_demo
How to using RabbitMQ (producer consumer with Spring boot and MVC)

Important Points :
--> To purge any message : Go to rabbitMQ bin --> purge_queue {queue name}

Exchange : It routes the message to the appropriate queue {Apply some conditions based on which we decide Queue} --> Types :  
1. Direct, 2. Fanout, 3. Topic, 4. Headers

Queue : where we pass the message and consumer will utilize the specific queue

1. Direct Exchange :: it matches the key which is present in Producer and Queue

2. Fanout Exchange :: (public -subscriber kind of), there is no concept of key matching and all, it is kind of pulbic exchange, all the queue that are attached to the Fanoutout exchange will get the message

3. Topic Exchange :: it will not match the two key exactly but it will match the portion of the key

* means one word
# one and more than one word

Public the message to topic exhange --> key message ="tv.mobile.ac"   

1. Queue key ="*.mobile.*,    [Matched]
2. Queue key ="*.tv.*,     [Not Matched]
 3. Queue key ="#.ac   [Matched]
If any message that has mobile word in the middle and have a word before and after it will go to mobile queue


4. Header Exchange :: In this exchange rather than using routing key we use Header. Header is key value pair, to consume a queue we have to match message header with queue header

any match : OR condition
all match :  AND condition 

example : 

Header = {"item1 = mobile" , "item2 = television}

Queues : 

1. Mobile --> Header = {"x-match = any" , "item1=mobile" , "item2=mob" }                 [Matched bcoz of item 1]
2. TV --> Header = {"x-match = any" , "item1 = tv" , "item2=television" }                   [Matched bcoz of item 2]
3. AC -->  Header = {"x-match = all" , "itme1=mobile" , "item2=ac" }                         [Not Matched] 

NOTE : CONSUMER part only works with Queue, it does not have any interaction with Exchange




