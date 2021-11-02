+++
title = "caseFunFinder"
author = "Cameron Farmer"
date = "2021-10-31T13:31:56-04:00"
workingDirectory = "~/root/myPortfolio/schoolWork/caseFunFinder.md"
weight = 0 
draft = false
toc = true
description = "CaseFunFinder is the final project my group and I made for our Introduction to Databases course. It is a simple web-based application connected to a database of attractions near Case Western Reserve University. Users can then execute a number of complicated queries on the database through its simple front-end. Check it out for yourself!"
+++

## Intro

Intro to Databases was one of my favorite classes during my Senior year of undergrad. During the course I learnt so much about the theory behind database structures and organization which instilled in me an appreciation how our information is stored. Databases pose their own unique problems and require elegant (and often mathematically provable) solutions. This made the class extremely exciting to me and I had a lot of fun working on the final project. 

My group and I decided to make CaseFunFinder -- a simple application that interfaced with a database of geographical attractions around our school (Case Western Reserve University). We started our project with a design phase during which we came up with a structure for organizing the type of information we wanted to store. Once we had decided on the arrangement of our data, we used SQL to create and populate our database's tables. Then, we connected the database to a very basic React site we were running on localhost in order to demo our project. 

## Demo

> Here is the demo of our database! (Thanks Randall <3)
{{< youtube osVOPDL2Vms >}}

## Design

The purpose of our database was to store information relevant to locations around our university and the greater Cleveland area. This posed a unique problem for us and necessitated that we come up with a clever way to organize our data. After considering a variety of solutions, we decided the most elegant way to structure our data was to categorize the locations we wanted to capture. We deliberated and elected to categorize all of our attractions into one of four groups: parks, museums/historical landmarks, theaters/performing art centers, and restaurants. 

By categorizing all of our location data, we were able to create an **is-a** relationship within our database. That is, we created a table for each category, as well as a table with every single attraction across all categories called **Attractions**. That table contained general information attractions such as its name, address, opening time, and so on.  This enabled us to store more information specific to each category within their own respective tables -- for instance, each restaurant has a field for whether or not it has vegetarian options!

Each attraction also has a field called its **fun id**, which acts as its unique identifier. The **fun id** is used as a primary key and is necessary to utilize the aforementioned is-a relationship. 

{{< figure src="/img/caseFunFinder/erDiagram.png" caption="ER Diagram for our database" >}}

Our database did not stop at just attractions, however. Since it was meant to be used as part of a larger application we included a table for user information. The user table was used to store information such as the user's name, and login information as well as a **user id** which acted as a unique identifier for each user. This allowed us to expand the capability of our database when we realized we could make a relationship between users and events! This lead us to the creation of the **Is tracking** and **Is favorite** relationship tables which contain entries composed of two primary keys: **user id** and **fun id**.  

We really liked this idea of relationships between entities in different tables, we decided to take it a step further. We created an entirely new type of entity called an **Event**! Events always take place at locations, so we used the structure we already had for **attractions** and created a new relationship called **Hosts**. Events have information such as start time and date, whether its child friendly, etc. as well as fields for event's name AND the attraction acting as its venue. 

## The Code

We created this database using MySQL and MySQLWorkbench. Once we had decided on our structure, it was a simple matter of creating our tables and inserting into them. Here is how we created our attractions table: 

{{< code language="sql" title="Creation of attraction table" id="1" expand="Show" collapse="Hide" isCollapsed="false">}}
CREATE TABLE `attractions` (
  `fun_id` int NOT NULL,
  `attraction_name` varchar(50) NOT NULL,
  `attraction_type` varchar(30) DEFAULT NULL,
  `street_address` varchar(100) DEFAULT NULL,
  `city` varchar(30) DEFAULT NULL,
  `zip_code` int DEFAULT NULL,
  `opening_hour` int DEFAULT NULL,
  `closing_hour` int DEFAULT NULL,
  `rating` decimal(2,1) DEFAULT NULL,
  `mask_required` varchar(1) DEFAULT NULL,
  PRIMARY KEY (`fun_id`,`attraction_name`)
) 
{{< /code >}}

Here is how we made tables that were part of an **is-a** relationship with attractions. Notice the **REFERENCES** field:

{{< code language="sql" title="Creation of restaurants table" id="1" expand="Show" collapse="Hide" isCollapsed="false">}}
CREATE TABLE `restaurants` (
  `fun_id` int NOT NULL,
  `rname` varchar(50) NOT NULL,
  `owner` varchar(50) DEFAULT NULL,
  `capacity_limit` varchar(10) DEFAULT NULL,
  `vegetarian_options` varchar(1) DEFAULT NULL,
  `vegan_options` varchar(1) DEFAULT NULL,
  PRIMARY KEY (`fun_id`,`rname`),
  KEY `fun_id_idx` (`fun_id`,`rname`),
  CONSTRAINT `fun_id, rname` FOREIGN KEY (`fun_id`, `rname`) REFERENCES `attractions` (`fun_id`, `attraction_name`) ON DELETE CASCADE ON UPDATE CASCADE
) 
{{< /code >}}

And finally, here is how we made relationships between tables. Notice how the only fields for any given entity are the primary keys of the tables it is relating: 

{{< code language="sql" title="Creation of is_tracking table" id="1" expand="Show" collapse="Hide" isCollapsed="false">}}
CREATE TABLE `is_tracking` (
  `cwru_id` varchar(30) NOT NULL,
  `fun_id` int NOT NULL,
  `attraction_name` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`cwru_id`,`fun_id`),
  KEY `cwru_id_idx` (`cwru_id`),
  KEY `attraction_fun_id, attraction_name_idx` (`fun_id`,`attraction_name`),
  CONSTRAINT `attraction_fun_id, attraction_name` FOREIGN KEY (`fun_id`, `attraction_name`) REFERENCES `attractions` (`fun_id`, `attraction_name`) ON DELETE RESTRICT ON UPDATE RESTRICT,
  CONSTRAINT `cwru_id` FOREIGN KEY (`cwru_id`) REFERENCES `users` (`cwru_id`) ON DELETE RESTRICT ON UPDATE RESTRICT
)
{{< /code >}}

The relationship tables posed a lot of problems due to the number of constraints they required. It took us a while to finally figure out how to create the table properly with all of the necessary checks in place. Furthermore, the entities in this table had to reference fields in other tables, which lead to a couple of bugs due to typos. 

## Personal Accomplishments

I really enjoyed the design phase of this project. I contributed greatly to the **is-a** relationship structure of our projects, and suggested the categorizing of attractions. Once we reached development, we all worked together to get it working, but I am particularly proud of some of the more complex queries I came up with for our demo. 

For instance, check out this query: 

> *"For each zip code, the user wants to find the attraction names and fun ids of attractions that host the maximum number of events; they then want the zip code, fun id, and attraction name of each such attraction listed."*

{{< code language="sql" title="Query for above request" id="1" expand="Show" collapse="Hide" isCollapsed="false">}}
WITH 	event_count(zip_code, host_fun_id, attraction_name, ct)
		(SELECT 	A2.zip_code, H2.host_fun_id, A2.attraction_name, COUNT(DISTINCT  H2.event_being_hosted_fun_id)
        FROM 		attractions A2, Hosts H2
		WHERE 	A2.fun_id = H2.host_fun_id
		GROUP BY 	A2.zip_code, H2.host_fun_id, A2.attraction_name),
SELECT 	A1.zip_code, A1.fun_id, A1.attraction_name
FROM 	attractions A1, event_count E
WHERE 	A1.fun_id = E.host_fun_id
AND 		E.ct = (SELECT MAX	(E2.ct)
	        		FROM 		event-count E2
	       		    WHERE 	A1.zip_code = E2.zip_code)
{{< /code >}}

## Lessons Learned

I am extremely appreciative of this class due to the value of learning how to write queries in SQL. I think our professor did an excellent job in training us to use all of SQL's weird little features, and demanded that we compose complex queries for homework and tests very often. This made me very comfortable using SQL and MySQLWorkbench and has left me very confident in my ability to query a database. 

Furthermore, I also learned how to do a form of set mathematics that apply to databases in order to compose queries that are mathematically provably complete! I thought this was really cool since it was a direct connection between math and computer science I had never considered. 