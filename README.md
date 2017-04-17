# Graph Theory 2017 - Timetabling System
### Robert Deegan - G00320583
### Project Specification
>You are required to design and prototype a Neo4j database for use in a timetabling system for a third level institute like GMIT. The database should store information about student groups, classrooms, lecturers, and work hours – just like the currently used timetabling system at GMIT.

The use of timetabling systems are in affect in the vast majority or businesses and learning institutions from schools to universitys all over the world. They're what makes a company or college work. Without them there would be mass confusion. The same can be said for a poorly made or designed timetabling system can be as counter productive as no system at all, especially in a learning institution where theres as many variables as students, lecturer or teachers aswell as room to take them. For these reason it is essential to have a well layed out and designed timetable for a system to run smoothly and as efficiently as possible.

**So what does the ideal timetable have to achieve?**

The timetable must be easy to follow and well layed out so that all people using it can understand it and use it without confusion. Take the [GMIT](https://www.gmit.ie) timetabling system as an example. The GMIT system uses blocks on a x,y axis graph with the times of the classes on the top axis and the days of the week running down the left hand side. In my opinion the layout is easy to understand with each block holding information of the room, module, lecturer details and course details. I've never had any difficulty in using this system after three years in the college. It can be confusing at first as some of the blocks displayed on the timetable can vary in size sometimes making it difficult to see what time the block is on at. 

The system must also work well in use and cause minimal proplems. These proplems invlove lecturers not being sheduled for more than one lecture, multiple classes being assigned to one room and that the class is free to attend that block. The fact that the college has so many students and modules means this is easier said than done and in the first weeks of a semester can reveal proplems in the system and can be troublesome.

The system must also be adaptable to change and for it to be straight forward for it to change to the requirements of the class in question. Again easier said than done as there may be a room available but it is too small or not suitable for the class to use it or the class may not be available at that timeslot. All of this must be clear in the system to avoid double booked rooms or rooms not being suitable for the needs of the class
 
**What do we need for the timetable system?**

We'll need all the different variables that are involed in the running of each class on the timetable in order for it to run properly. For each class we need a room, a lecturer, the time for the class to run, the course involed, the module that is being taught and the group being taught. All of these variables must be included for the class to run as missing one will lead to proplems like a missing lecturer or no room to hold the lecture.

We also need a way of holding all of this data and information in an organised manner that can link every thing back to each other. When everything is linked a user can see all that data involved and see that the room there looking for cannot be booked as it is booked by class x and lecturer y so it is unavailable. In my opinion a good way to store all this is by using a [Graph Database.](https://en.wikipedia.org/wiki/Graph_database) A graph database uses relationships between entities to link different pieces of data together that can later be recieved together at the same time with one opertaion or query. The entites and represented as [nodes](https://en.wikipedia.org/wiki/Node_(computer_science)) and the relationship between these nodes are represented as [edges.](https://en.wikipedia.org/wiki/Glossary_of_graph_theory_terms#edge) A series of nodes and edges all linked together would act of the requirements of the timetabling system.

**Neo4j**

[Neo4j](https://neo4j.com) is a graph database management system developed by Neo Technology written in java. It is one of the most popular graph database management systems used today and is used by companys including Cisco, Walmart, eBay, HP, LinkedIn and many more. Walmart uses Neo4j to optimise customer expierence with real time recomendations and eBay uses it for eCommerce Delivery Service Routing. 

Each node and edge can hold multiple attributes and can be labled to narrow down searchs for a faster system. Neo4j uses the [Cypher Query Language](https://en.wikipedia.org/wiki/Cypher_Query_Language) to search through the database and carry out querys. The simple but powerful language can search through the largest and most complicated databases when the right querys are used using MATCH and WHERE clauses similar to SQL.

Neo4j has a very well layed out interface once installed and displays graph databases with the nodes represented by coloured cirlces and the relationships or edges can be labled for easy an easy to follow connection between the nodes. The database can be very well layed out if designed properly and the built it command line for cypher querys works very well. When the right querys are used, only the relevent information is displayed very quickly. The nodes can also be dragged around to suit your preference. 


**My Approach to the problem**

It took me a good while to come up with an approach to this problem. Mostly because I had to find something that was on par if not better than the current system implemented in the college. My first couple of drafts where not overly succesful as they where too complex and confusing even for myself and at the time I didn't understand 100% what was required but the these drafts eventually sent me down this path.

One night I decided to appraoch the problem in the order of the importance (in my opinion) of the variables involved in running a lecture. I felt that I the root node or one of the higher level nodes could not be satisfied, that the whole tree could not work. I decided to start with the room at the root node and work down from there. I felt at the time that the room was the most important as without it there would be no place to hold the lecture. Moving down from there I would add relationships from the room to the times that lectures run at from 9am - 6pm. From there a lecturer, group and module can be added to those times.

The rooms, lecturers, moudles, times and courses would be represented by nodes with each nodes being linked to each other when appropiate using relationships such as TAUGHT_BY, AT, ATTENDING etc. Cypher queries can then be used to fing the data and relationships you need.

**Implementaion**

I had to get all the room numbers used as lecture rooms in GMIT. I went to the GMIT timetabling page and navigated to the rooms section where all the rooms are listed. As shown to us by our lecturer Ian McLoughlin, I opened the page source of the page and copied all the room numbers from the source code. After an hour of staring at the information wondering how to use it, I used a few tricks in visual code to cut down all the HTML code to just get the raw data I needed. I then used a combonation of Miscrosoft Word and Excel to create Cypher queries for each room to be inserted in the database as a node. The information and queries can be seen in the CSV file above called [GMITRooms.csv.](https://github.com/RobbieDeegan/Graph-Theory-2017/blob/master/GMITRooms.csv) After a bit of trail and error and a lot of help from the vertical selection tool in Word, I tailored the data into the queries I needed and copied it all into Neo4j. It worked perfectly and the rooms where added. I only used the rooms on the GMIT Dublin Road campus to save some space for my prototype and as some of the room names in the Letterfrack and CCAM campuses didn't line up with the ones I've used in the databases.

I added each room with this query for each room.
>CREATE	(room1:Room{ name:'PF02'})
There was around 150 of these 

I used **room1** in order to add all the rooms in one query, theres no significance to the name.

I then went on to add some lecturers, modules and the course to the database.
>CREATE (n:Person { name: 'Ian McLoughlin', title: 'Lecturer' })
>CREATE (n:Module { name: 'Graph Theory'})
>CREATE (n:Course { name: 'BSc in Computing in Software Development Year 3'})


