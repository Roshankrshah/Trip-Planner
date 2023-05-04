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


# TABLES DESCRIPTION
This is the list of all the tables which we created in our database.


![image](https://user-images.githubusercontent.com/91787844/236265793-299da857-56b7-4a84-979e-3ca147e1c75d.png)
![image](https://user-images.githubusercontent.com/91787844/236265823-022f06e4-cb6f-4550-b211-1d6599dac8a5.png)

 ## Travelling mode
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

## Accommodation
• Hotels: This entity is useful for staying of customers it contains 
the hotel id, hotel’s name, type etc. this entity further divided into 
three entities using normalization.

## Tourist places
• City: This entity contains list of cities of tourist places it contains 
the only city’s name.

• Locality: This entity contains list of area of place in respective 
city it contains the locality’s id, name etc.

• Places: This entity contains list of tourist place in respective area 
it contains address, name, description etc.

• Restaurants: This entity contains list of restaurants in respective 
area it contains address, name, type etc.

# DEPENDENCIES AND NORMALIZATION
## Train 

![image](https://user-images.githubusercontent.com/91787844/236267157-e4b1bbec-57da-4fbc-972b-0aea86af134c.png)

Find Candidate Key

•	Attribute not present any sides: None

•	Attribute present Only on left side: name, Dep_time, fare, status, seats, hours.

•	Attribute present Only on right side: id, classId, source, destination, date.

•	Attribute present both sides: None

CK- (id, classId, source, destination, date)+ = R

Now decomposed the table into four table for BCNF normalization.


### Train

In this table there is one functional dependency 

{train_id --> train_name} and the normal form is BCNF.


#### TrainDepartureTime

  •	FDs: {train_id, source} ---> departure_time 
  
  •	Normal Form: BCNF 
  
  •	Foreign Key:
  
    o	train_id from table Train as train_id
    
    o	city_name from table City as source
    
#### TrainReservation

  •	FDs:
  
    o	{train_id, ClassId, source, destination, Date} ---> fare 
    
    o	{train_id, ClassId, source, destination, Date} ---> train_status 
    
    o	{train_id, ClassId, source, destination, Date} ---> no_of_seats 
    
  •	Normal Form: BCNF
  
  •	Foreign Key:
  
    o	{train_id, source} from table TrainDepartureTime as {train_id, source}
    
    o	city_name from table City as destination 
    
#### TrainJourneyHours

  •	FDs:
  
    o	{train_id, source, destination} ---> journey_hours 
    
  •	Normal Form: BCNF
  
  •	Foreign Key:
  
    o	{train_id, source} from table TrainDepartureTime as {train_id, source}
    
    o	city_name from table City as destination
    

###	CAB
####	CabType

 •	Normal Form: BCNF
 
####	CabService

  •	FDs:
  
    o	cab_service_id ---> provider_name
    
    o	cab_service_id ---> contact_no
    
    o	cab_service_id ---> rating
    
  •	Normal Form: BCNF
  
####	CabServiceInACity

  •	Normal Form: BCNF
  
  •	Foreign Key:
  
    o	cab_service_id from table CabService as cab_service_id
    
    o	city_name from table City as city_name 
    
####	Cabs
  
 •	FDs: 
 
    o	{cab_service_id, city_name, cab_type} ---> cost_per_day
    
    o	{cab_service_id, city_name, cab_type} ---> total_available_cabs
    
•	Normal Form: BCNF

•	Foreign Key:

    o	{cab_service_id, city_name} from table CabServiceInACity as {cab_service_id, city_name}
    
    o	cab_type from table CabType as cab_type 
    
###	BUS
#### Bus

 •	FDs:
 
     o	bus_id ---> provider_name
   
     o	bus_id ---> is_ac
   
     o	bus_id ---> rating
   
 •	Normal Form: BCNF
 
####	BusDepartureTime

 •	FDs:
 
     o	{bus_id, source, departure_date} ---> time_of_departure
   
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
     o	bus_id from table Bus as bus_id
   
     o	city_name from table City as source
   
 •	BusJourneyHours
 
 •	FDs:
 
     o	{bus_id, source, destination, departure_date} ---> journey_hours
 
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
     o	{bus_id, source, departure_date} from table BusDepartureTime as bus_id,source, departure_date}
   
     o	city_name from table City as destination 
   
#### BusReservation

 •	FDs:
 
     o	bus_id, source, destination, departure_date, seat_type} ---> cost
   
     o	{bus_id, source, destination, departure_date, seat_type} ---> total_available_seats 
   
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
     o	{bus_id, source, departure_date} from table BusDepartureTime as {bus_id, source, departure_date}
   
     o	city_name from table City as destination
   
### City
#### City

 •	Normal Form: BCNF
 
 •	NearByCites
 
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
     o	city_name from table City as current _city
   
     o	city_name from table City as nearby_city 
   
### Locality
#### Locality

 •	FDs:
 
     o	locality_id ---> locality_name
   
     o	locality_id ---> city_name
   
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
     o	city_name from table City as city_name 
   
### Place to visit
#### PlacesToVisit 

 •	FDs:
 
     o	{place_name, locality_id} ---> place_type
   
     o	{place_name, locality_id} ---> description_of_the_place
   
     o	{place_name, locality_id} ---> rating
   
     o	{place_name, locality_id} ---> street_address
   
     o	{place_name, locality_id} ---> avg_cost_person
   
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
     o	locality_id from table Locality as locality_id
   
### Hotels
####	Hotels 

 •	FDs:
 
   o	{hotel_name, locality_id} ---> rating
   
   o	{hotel_name, locality_id} ---> street_address
   
   o	{hotel_name, locality_id} ---> is_room_service
   
   o	{hotel_name, locality_id} ---> contact_no
   
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
   o	locality_id from table Locality as locality_id 
   

#### HotelReservation

 •	FDs:
 
   o	{hotel_name, locality_id, date_of_availability, RoomType} ---> total_available_rooms
   
   o	{hotel_name, locality_id, date_of_availability, RoomType} ---> cost
   
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
   o	{hotel_name, locality_id} from table Hotels as {hotel_name, locality_id}
   
   o	room_type from table TypeOfRoom as room_type  
   
#### TypeOfRoom

 •	FDs:
 
   o	room_type ---> max_accomodation
   
 •	Normal Form: BCNF
 
### Restaurants
####	Restaurants

 •	FDs:
 
   o	{restaurant_name, locality_id} ---> restaurant_type
   
   o	{restaurant_name, locality_id} ---> rating
   
   o	{restaurant_name, locality_id} ---> street_address
   
   o	{restaurant_name, locality_id} ---> AvgRate/Person  
   
 •	Normal Form: BCNF
 
 •	Foreign Key:
 
   o	locality_id from table Locality as locality_id
   

# QUERIES:

These are some Realistic Queries for the System with their following SQL commands and relational algebra.
## Query 1: List all the cities which have more than 3 historical places to visit.

### Relational Algebra:

  a ← Locality ⨝<locality_id=PlacesToVisit.locality_id> PlacesToVisit
  
  b ← 𝞂<type = ‘Historical’>(a)
  
  c ← city_nameG count(city_name) (b) HAVING<ਹ<count> >=3>
 
  d ← 𝛑<city_name>(c)
 
MySQL Command:
 
 ![image](https://user-images.githubusercontent.com/91787844/236275991-286d9c4e-526a-446a-9e6e-b3c30cf9e4b5.png)
 
OUTPUT
 
 ![image](https://user-images.githubusercontent.com/91787844/236276040-24bca0a7-56ae-485f-a4d8-36b15f43dd15.png)
 
## QUERY 2:  NON-AC buses between Delhi and Mumbai on date 16th
April, 2021. 
 
### Relational Algebra
 
 a ← Bus ⨝<Bus.bus_id=BusReservation.bus_id> BusReservation
 
 b ← 𝞂<source = ‘Delhi and destination = ‘Mumbai’ and is_ac = false and date =’2021-4-16’>(a)
 
 c ← 𝛑<bus_id, bus_service_provider>(c)
 
MySQL Command
 
 ![image](https://user-images.githubusercontent.com/91787844/236276414-3ec12e87-9f4e-4cf6-92dc-21a742768c52.png)
 
OUTPUT
 
 ![image](https://user-images.githubusercontent.com/91787844/236276491-9bb6f04a-d751-4b2d-834b-1ff16d0014f3.png)
 
## QUERY 3: Restaurants near the cheapest hotel in Delhi.
 
### Relational Algebra
 
 a ← hotels ⨝<hotel.locality_id=locality.locality_id> locality
 
 b ← 𝞂<city_name = “Delhi”>(a)
 
 c ← 𝛑<min(cost)>(b)
 
 d ← 𝞂<cost in c and city_name = “Delhi”>(b)
 
 e ← d ⨝<d.locality_id=Restaurants.locality_id>Restaurants
 
 f ← 𝛑<city_name>(e)
 

MySQL Command 
 ![image](https://user-images.githubusercontent.com/91787844/236276713-ff3af607-d54f-40dc-ac0f-bacf40c8419e.png)
 
 OUTPUT
 
 ![image](https://user-images.githubusercontent.com/91787844/236276783-1f65575b-d212-4826-accb-3f44ea3c90a6.png)
 
## QUERY 4: Find restaurants which are nearby to the highest rated place to visit in Delhi.
 
### Relational Algebra
 
 a ← PlacesToVisit ⨝<PlacesToVisit.locality_id=Locality.locality_id>Locality
 
 b ← 𝞂<city_name = “Delhi”>(a)
 
 c ← 𝛑<max(rating)>(b)
 
 d ← 𝞂<cost in c and city_name = “Delhi”>(b)
 
 e ← d ⨝<d.locality_id=Restaurants.locality_id> Restaurants
 
 MySQL Command
 
 ![image](https://user-images.githubusercontent.com/91787844/236277045-4f037805-a7e7-4da6-ab7e-73cb06ba87a0.png)
 
 OUTPUT
 ![image](https://user-images.githubusercontent.com/91787844/236277137-6c3cea75-77e3-42f2-9fd6-e270fac7ffc5.png)
 
## QUERY 5: Find those hotels in Delhi, which have those rooms available that can accommodate more than 1 person.
 
### Relational algebra
 
 a ← HotelReservation ⨝<HotelReservation.room_type = TypeOfRoom.room_type>TypeOfRoom
 
 b ← a ⨝<a.locality_id = Locality.locality_id> Locality
 
 c ← 𝞂<city_name = “Delhi” and max_accomodation > 1 and total_available_rooms > 1>(b)
 
 d ← 𝛑<distinct hote_name, room_type>(c)
 
MySQL Command 
 
 ![image](https://user-images.githubusercontent.com/91787844/236277448-9be6c780-b6a6-4243-bd21-489c67466221.png)

 OUTPUT
 
 ![image](https://user-images.githubusercontent.com/91787844/236277500-8a60eee6-b2e1-4df7-a4db-c83995b16fc2.png)
 
## QUERY 6: All those cab service providers who can provide a ‘SUV’ cab in Vadodara.
 
### Relational algebra
 
 a ← Cabs ⨝<Cabs.cab_service_id=CabService.cab_service_id> CabService
 
 b ← 𝞂<cab_type = “SUV” and city_name = “Vadodara”>(a)
 
 c ← 𝛑<cab_service_id, provider_name>(b)

MySQL Command
 ![image](https://user-images.githubusercontent.com/91787844/236277679-9878d9d5-8c87-4f7a-bced-b2a44ebf4ced.png)
 
 OUTPUT
 ![image](https://user-images.githubusercontent.com/91787844/236277751-28500246-688f-4348-abe6-dac43b6a82c5.png)



 


 







    
