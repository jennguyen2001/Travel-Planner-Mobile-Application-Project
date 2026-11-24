Planning plays an important role in traveling. It not only contributes to a trip’s success and satisfaction but also to travelers’ safety and financial efficiency. However, many travelers may overlook the planning process because they perceive it as complicated and time-consuming. Travel planning involves many aspects, such as destinations, flights, transportation, tourism activities, and budgeting. As a result, planners need to use various tools and platforms to gather information. The objective of this project is to build an iOS mobile application that helps travelers organize trip information and manage activities more conveniently. The scope of the application focuses on planning features, including creating individual or group trips, managering members of trips, adding activities and tracking estimated expenses.
Table1: Trip
Trip_ID
(PK)	Traveler_ID
(PK)	Traveler_name	Traveler_contact	Start_date	End_date	City	Country
T01	P01	Anna	316111111	2026-01-01	2026-01-14	Tokyo	Japan
T01	P02	John	316112111	2026-01-01	2026-01-14	Tokyo	Japan
T01	P03	Mark	316111112	2026-01-01	2026-01-14	Tokyo	Japan
T02	P01	Anna	316111111	2026-01-02	2026-02-02	Chicago	US
T02	P04	Jun	316111312	2026-01-02	2026-02-02	Chicago	US
T03	P05	April	316131312	2026-03-02	2026-03-14	Seoul	Korea
T04	P04	Jun	316111312	2026-04-02	2026-04-8	Tokyo	Japan

Table1 is used to manage information of each trips, such as trip members, dates and location. This supports the application's search function. Users can search for their trips, and the application retrieves relevant information from the database.
Table 2: Expense
Expense_ID (PK)	Trip_ID (FK)	Traveler_ID (FK)	Expense_category		Amount
E01	T01	P01	Hotel	100
E02	T01	P01	Food	50
E03	T01	P02	Taxi	100
E04	T01	P03	Food	50

Table 2 is used to manage all expenses for each trip. This supports the bill-splitting function. Users input each expense amount and specify who paid. The application saves their inputs to the database to calculate the amount each trip member owes to others.




Table3: Activity 
Table 3 is used to manage activities associated with trips and activities in the system in general. This supports the search and recommendation functions. Users can input an activity, and the application retrieves data from the database to find activities in the same city and category and then recommend those with the highest ratings. Users can add the suggested activities to their trips.
Activity_ID
(PK)	Trip_ID (FK)	Activity_name	Activity_category	Activity_city	Activity_country	Rating_count	Average_Rating
A01	T01	Tokyo Tower	Sightseeing	Tokyo	Japan	3.8	112
A02	T01	Sensoji Temple	Historical	Tokyo	Japan	4.7	50
A03	T02	Millennium Park	Entertainment	Chicago	US	4.7	100
A04	T03	Gyeongbokgung Palace	Historical	Seoul	Korea	4.5	80
A05	T03	Namsan Tower	Sightseeing	Seoul	Korea	4	92
A06	T04	Tokyo Tower	Sightseeing	Tokyo	Japan	3.8	112

Example 1: Query listing all the activities in Seoul for recommendation function
{\pi }_{\text{Activity\_name}}\left({\sigma }_{\text{city}=\prime Seoul\prime }\left(\text{Activity}\right)\right)
Example 2: Query supporting feature calculating expenses of the trip
{\pi }_{\text{Expense\_ID,\ Amount}}\left({\sigma }_{\text{Trip\_ID}=\prime T02\prime }\left(Expense\right)\right)
Example 3: Query listing all the activity names of trip T02
{\pi }_{Activity\_name}\left(Activity\bowtie {\sigma }_{Trip\_ID=\prime T02\prime }\left(Trip\_Activity\right)\right)
Example 4: Query listing all expenses Traveler P01 paid in Trip T01
{\pi }_{\text{Expense\_ID,\ Amount}}\left({\sigma }_{\text{Trip\_ID=\ '\ T01'}\ \ \wedge \ Traveler\_ID\ =\ 'P01'}\left(Expense\right)\right)
Example 5: Query finding all the activities located in the same city and having the same category as Activity A03
{\sigma }_{\text{Activitiy\_ID}\neq \prime A03\prime }\ (\text{Activity}\bowtie {\pi }_{\text{Activity\_category,\ Activity\_city}}\left({\sigma }_{\text{Activity\_ID\ =\ 'A03'}}\left(\text{Activity}\right)\right)
I plan to use AI to support the development of the application’s back-end and database connection. Some prompts I plan to use include, for examples :
	Explain how to connect a Flask application to an SQLite database.
	Explain how to perform CRUD operations using Flask and SQLite.
	Explain how to implement a search function that filters records based on multiple attributes.

<img width="468" height="649" alt="image" src="https://github.com/user-attachments/assets/9daf6684-9c6e-47f0-b276-270d38631fdb" />
