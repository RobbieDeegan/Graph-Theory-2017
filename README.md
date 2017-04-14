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

[Neo4j](https://neo4j.com) is a graph database management system developed by Neo Technology. It is one of the most popular graph database management systems used today and is used by companys including Cisco, Walmart, eBay, HP, LinkedIn and many more. Walmart uses Neo4j to optimise customer expierence with real time recomendations and eBay uses it for eCommerce Delivery Service Routing. 