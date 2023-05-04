# Trip-Planner

A Trip planner management system would play a significant role in 
planning the perfect trip. The main purpose is to help tourism 
companies to pre-plan the trip of their customers according to their 
system access all the details such as tourist places, travelling mode, 
accommodation etc. this helps the customer to reduce the unnecessary 
wastage of time and money. So, proposed system maintains centralized 
repository to make necessary travel arrangements and to retrieve 
information easily.
The system is implemented in MySQL Workbench and 
Normalization and Dependencies are also handled perfectly.

# ENTITY RELATIONSHIP DIAGRAM
An entity relationship model describes interrelated things of interest in 
a specific domain of knowledge. The ER Diagram of Trip planner 
Management System is shown below.

![image](https://user-images.githubusercontent.com/91787844/186564111-af99e359-6c4e-4e08-96c4-755f64f38a80.png)

# RELATIONAL SCHEMA
A relational database schema helps to understand and organize the 
structure of a database. It is helpful when we design a new database or 
existing database is modified to incorporate new functionality.

![image](https://user-images.githubusercontent.com/91787844/186564330-3e0f33f1-e79e-4240-bbe6-b3663a6ce332.png)


#TABLES DESCRIPTION
This is the list of all the tables which we created in our database.


![image](https://user-images.githubusercontent.com/91787844/236265793-299da857-56b7-4a84-979e-3ca147e1c75d.png)
![image](https://user-images.githubusercontent.com/91787844/236265823-022f06e4-cb6f-4550-b211-1d6599dac8a5.png)

 #Travelling mode
• Trains: This entity is useful for travelling the long distances to 
one city to another city it contains the train ids, train’s name, 
source etc. this entity further divided into four entities using 
normalization.

• Buses: This entity is alternate for trains it contains the bus ids, 
bus’s name, type of buses etc. this entity further divided into four 
entities using normalization.

• Cabs: This entity is useful for travelling the short distance it 
contains the cabs ids, cab type, cost etc. this entity further divided 
into four entities using normalization.

• Accommodation
• Hotels: This entity is useful for staying of customers it contains 
the hotel id, hotel’s name, type etc. this entity further divided into 
three entities using normalization.

# Tourist places
• City: This entity contains list of cities of tourist places it contains 
the only city’s name.

• Locality: This entity contains list of area of place in respective 
city it contains the locality’s id, name etc.

• Places: This entity contains list of tourist place in respective area 
it contains address, name, description etc.

• Restaurants: This entity contains list of restaurants in respective 
area it contains address, name, type etc.
