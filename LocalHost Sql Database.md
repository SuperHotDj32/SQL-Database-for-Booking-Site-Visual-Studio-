# SQL-Database-for-Booking-Site-Visual-Studio-
This project is (For Educational purposes) το build a Sql Database for Booking Site! It's very simple with tables, child tables,Foreign keys &amp; Alter table about cascade! It's not completed just to know!
Flights:

Number Of Flights:
ID
address
phone
Information


Starting Points & Destinations:
AFM
Country
Town
Airport
Island
Collaborator Company's

Date & Time
ID
Timezone
Time Departure
Time Withdrawal
Date Departure
Date Withdrawal

Price:
ID
Voucher - Coupons
Phone
Affiliated Company's Agreement

Customer Service Center:
AFM
Phone 
Email
Address
Owner Details
Fax

Staff:
AFM
amka
ama
ari8mos tautothtas
ari8mos diavathriou
date of birth
Name
Surname
Phone 
Viografiko
Adress
Stratiotikes Ypoxrewseis
Contract


Advertise:
ID
Contract
Collaborator Company's

Tickets:
ID 
Price
Collaborator Company's
E-Tickets
Stops
Delayed Flight's

Seats:
ID
Economical
Faster
Premium


Accounting Department:
AFM
Eksoda
Esoda
Phone
Email
Address
Salary
Owner Details
Refunds

Site:
URL
Email
Phone
Address
Payment 
Informations
E-Tickets
Users

Trabookit


Flights:
Number_Of_Flights
Starting_Points_Destinations
Date_Time
Price

Hotel:
Hotel_ID
Hotels_Name
Location
Types_Of_Room
Price

Customers:
Customer_ID
Customer_Details
Contact_Information
Payment_Information

Rental_Cars:
Cars_ID
Rental_Car_Brands
Location
Types_Of_Car
Price

Activities:
ID
Names_Of_Activities
Location
Description
Price

Reservations:
Date_Of_Reservations
Flights
Hotels
Rental_Cars
Activities

Airlines:
Airline_Names
Contact_Information

Airports:
Airport_Names
Location

Reviews:
Review_For_Hotels
Review_For_Rental_Cars
Review_For_Activities
Review_For_Airlines

Payments:
Customer_Payments
Date_Payments
Payment_Methods

Customer_Service_Center:
AFM
Address
Phone
Email
Owners_Name
Fax

Site:
URL
Email
Phone
Address
Payment 
Informations
E_Tickets
Users

Staff:
AFM
amka
ama
ari8mos tautothtas
ari8mos diavathriou
date of birth
Name
Surname
Phone 
Viografiko
Adress
Stratiotikes Ypoxrewseis
Contract









/
Flights == Hotel == Reservations == Site == Airports == Airlines == Payments == Customer_Service_Center
Hotel == Customers == Rental_Cars == Activities == Reservations == Reviews == Payments == Customer_Service_Center
Customers == Customer_Service_Center == Hotel == Activities == Reservations == Airlines == Airports == Reviews == Payments == Site
Rental_Cars == Customers == Hotel == Reservations == Payments == Reviews == Customer_Service_Center == Site
Activities == Customers == Site == Customer_Service_Center == Hotel == Reviews == Payments 
Reservations == Payments == Hotel == Customers == Rental_Cars == Airports == Payments == Customer_Service_Center
Airlines == Airports == Flights == Flights == Reservations == Reviews == Payments == Customer_Service_Center == Site == Customers
Airports == Airlines == Flights == Payments == Customer_Service_Center == Site == Customers
Reviews == Customer_Service_Center == Airlines == Activities == Rental_Cars == Customers == Hotel == Flights
Payments == Flights == Hotel == Rental_Cars
Customer_Service_Center == Site == Staff == Reservations == Airports == Payments == Reviews == Airlines ==  Rental_Cars 
Site == Staff == Customer_Service_Center == Payments == Reviews == Airports == Airlines == Reservations == Activities == Rental_Cars == Customers == Hotel == Flights 
Staff == Site == Customer_Service_Center == Customers
/





Trabookit Sample Without Cascade & Foreign:



CREATE TABLE Flights (
      Number_Of_Flights int AUTO_INCREMENT PRIMARY key,
      Starting_Points_Destinations varchar(255) not null,
      Date_Time date not null,
      Price int not null
);
CREATE TABLE Hotel (
      Hotel_ID int AUTO_INCREMENT PRIMARY key,
      Hotels_Name varchar(255) not null,
      Location varchar(255) not null,
      Types_Of_Room varchar(50) not null,
      Price int not null
);
CREATE TABLE Customers (
      Customer_ID int AUTO_INCREMENT PRIMARY key,
      Customer_Details text not null,
      Contact_Information text not null,
      Payment_Information text not null
);
CREATE TABLE Rental_Cars (
      Cars_ID int AUTO_INCREMENT PRIMARY key,
      Rental_Car_Brands varchar(50) not null,
      Location varchar(50) not null,
      Types_Of_Car varchar(100) not null,
      Price int not null
);
CREATE TABLE Activities (
      ID int AUTO_INCREMENT PRIMARY key,
      Names_Of_Activities varchar(255) not null,
      Location varchar(50) not null,
      Description text not null,
      Price int not null
);
CREATE TABLE Reservations (
      Reservation_ID int AUTO_INCREMENT PRIMARY key,
      Flights varchar(255) not null,
      Hotels varchar(255) not null,
      Rental_Cars varchar(255) not null,
      Activities varchar(255) not null
);
CREATE TABLE Airlines (
      Airlines_ID int AUTO_INCREMENT PRIMARY key,
      Airline_Name varchar(255) not null,
      Contact_Information text not null
);
CREATE TABLE Airports (
      Airports_ID int AUTO_INCREMENT PRIMARY key,
      Airport_Names varchar(255) not null,
      Location varchar(255) not null
);
CREATE TABLE Reviews (
      Reviews_ID int AUTO_INCREMENT PRIMARY key,
      Review_For_Hotels text not null,
      Review_For_Rental_Cars text not null,
      Review_For_Activities text not null,
      Review_For_Airlines text not null
);
CREATE TABLE Payments (
      Payments_ID int AUTO_INCREMENT PRIMARY key,
      Customer_Payments float not null,
      Date_Payments varchar(50) not null,
      Payment_Methods varchar(50) not null
);
CREATE TABLE Customer_Service_Center (
      AFM int AUTO_INCREMENT PRIMARY key,
      Address varchar(50) not null,
      Phone int(10) not null,
      Email varchar(20) not null,
      Owners_Name varchar(255) not null,
      Fax int(10) not null
);
Create TABLE Site(
      URL int(50) AUTO_INCREMENT PRIMARY key,
      Email varchar(50) not null,
      Phone int(10) not null,
      Address varchar(255) not null,
      Payment varchar(50) not null,
      Informations text not null,
      E_Tickets varchar(255) not null,
      Users varchar(255) not null
);





















Trabookit Sample Foreign:






CREATE TABLE Flights (
      Flights_ID int AUTO_INCREMENT PRIMARY key,
      Number_Of_Flights int not null,
      Starting_Points_Destinations varchar(255) not null,
      Date_Time date not null,
      Price int not null,
      FOREIGN KEY (Flights_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Site(URL),
      FOREIGN KEY (Flights_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Customer_Service_Center(AFM)   
);
CREATE TABLE Hotel (
      Hotel_ID int AUTO_INCREMENT PRIMARY key,
      Hotels_Name varchar(255) not null,
      Location varchar(255) not null,
      Types_Of_Room varchar(50) not null,
      Price int not null,
      FOREIGN KEY (Hotel_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Activities(ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Customer_Service_Center(AFM)  
);
CREATE TABLE Customers (
      Customer_ID int AUTO_INCREMENT PRIMARY key,
      Customer_Details text not null,
      Contact_Information text not null,
      Payment_Information text not null,
      FOREIGN KEY (Customer_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Customer_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Activities(ID),
      FOREIGN KEY (Customer_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Site(URL)
);
CREATE TABLE Rental_Cars (
      Cars_ID int AUTO_INCREMENT PRIMARY key,
      Rental_Car_Brands varchar(50) not null,
      Location varchar(50) not null,
      Types_Of_Car varchar(100) not null,
      Price int not null,
      FOREIGN KEY (Cars_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Cars_ID) REFERENCES Site(URL)
);
CREATE TABLE Activities (
      ID int AUTO_INCREMENT PRIMARY key,
      Names_Of_Activities varchar(255) not null,
      Location varchar(50) not null,
      Description text not null,
      Price int not null,
      FOREIGN KEY (ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (ID) REFERENCES Site(URL),
      FOREIGN KEY (ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (ID) REFERENCES Payments(Payments_ID)
);
CREATE TABLE Reservations (
      Reservation_ID int AUTO_INCREMENT PRIMARY key,
      Flights varchar(255) not null,
      Hotels varchar(255) not null,
      Rental_Cars varchar(255) not null,
      Activities varchar(255) not null,
      FOREIGN KEY (Reservation_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Customer_Service_Center(AFM)
);
CREATE TABLE Airlines (
      Airlines_ID int AUTO_INCREMENT PRIMARY key,
      Airline_Name varchar(255) not null,
      Contact_Information text not null,
      FOREIGN KEY (Airlines_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Flights(Flights_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Airlines_ID) REFERENCES Site(URL),
      FOREIGN KEY (Airlines_ID) REFERENCES Customers(Customer_ID)
);
CREATE TABLE Airports (
      Airports_ID int AUTO_INCREMENT PRIMARY key,
      Airport_Names varchar(255) not null,
      Location varchar(255) not null,
      FOREIGN KEY (Airports_ID) REFERENCES Airports(Airlines_ID),
      FOREIGN KEY (Airports_ID) REFERENCES Flights(Flights_ID),
      FOREIGN KEY (Airports_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Airports_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Airports_ID) REFERENCES Site(URL),
      FOREIGN KEY (Airports_ID) REFERENCES Customers(Customer_ID)
);
CREATE TABLE Reviews (
      Reviews_ID int AUTO_INCREMENT PRIMARY key,
      Review_For_Hotels text not null,
      Review_For_Rental_Cars text not null,
      Review_For_Activities text not null,
      Review_For_Airlines text not null,
      FOREIGN KEY (Reviews_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Reviews_ID) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Activities(ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Flights(Flights_ID)
);
CREATE TABLE Payments (
      Payments_ID int AUTO_INCREMENT PRIMARY key,
      Customer_Payments float not null,
      Date_Payments varchar(50) not null,
      Payment_Methods varchar(50) not null,
      FOREIGN KEY (Payments_ID) REFERENCES Flights(Flights_ID),
      FOREIGN KEY (Payments_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Payments_ID) REFERENCES Rental_Cars(Cars_ID)
);
CREATE TABLE Customer_Service_Center (
      AFM int AUTO_INCREMENT PRIMARY key,
      Address varchar(50) not null,
      Phone int(10) not null,
      Email varchar(20) not null,
      Owners_Name varchar(255) not null,
      Fax int(10) not null,
      FOREIGN KEY (AFM) REFERENCES Site(URL),
      FOREIGN KEY (AFM) REFERENCES Staff(AFM),
      FOREIGN KEY (AFM) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (AFM) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (AFM) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (AFM) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (AFM) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (AFM) REFERENCES Rental_Cars(Cars_ID)
);
Create TABLE Site(
      URL int(50) AUTO_INCREMENT PRIMARY key,
      Email varchar(50) not null,
      Phone int(10) not null,
      Address varchar(255) not null,
      Payment varchar(50) not null,
      Informations text not null,
      E_Tickets varchar(255) not null,
      Users varchar(255) not null,
      FOREIGN KEY (URL) REFERENCES Staff(AFM),
      FOREIGN KEY (URL) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (URL) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (URL) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (URL) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (URL) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (URL) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (URL) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (URL) REFERENCES Activities(ID),
      FOREIGN KEY (URL) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (URL) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (URL) REFERENCES Flights(Flights_ID)
);
Create TABLE Staff(
      AFM int(10) AUTO_INCREMENT PRIMARY key,
      AMKA int(9) not null,
      AMA int(10) not null,
      ID_Number varchar(8) not null,
      Passport_Number varchar(9) not null,
      Date_Of_Birth varchar(50) not null,
      Name varchar(255) not null,
      Surname varchar(255) not null,
      Phone int(10) not null,
      Viografiko text not null,
      Adress varchar(255) not null,
      Stratiotikes_Ypoxrewseis boolean,
      Contract text not null,
      FOREIGN KEY (AFM) REFERENCES Site(URL),
      FOREIGN KEY (AFM) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (AFM) REFERENCES Customers(Customer_ID)
);



























Trabookit Sample Cascade & Foreign:







CREATE TABLE Flights (
      Flights_ID int AUTO_INCREMENT PRIMARY key,
      Number_Of_Flights int not null,
      Starting_Points_Destinations varchar(255) not null,
      Date_Time date not null,
      Price int not null,
      FOREIGN KEY (Flights_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Site(URL),
      FOREIGN KEY (Flights_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Flights_ID) REFERENCES Customer_Service_Center(AFM)   
);
CREATE TABLE Hotel (
      Hotel_ID int AUTO_INCREMENT PRIMARY key,
      Hotels_Name varchar(255) not null,
      Location varchar(255) not null,
      Types_Of_Room varchar(50) not null,
      Price int not null,
      FOREIGN KEY (Hotel_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Activities(ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Hotel_ID) REFERENCES Customer_Service_Center(AFM)  
);
CREATE TABLE Customers (
      Customer_ID int AUTO_INCREMENT PRIMARY key,
      Customer_Details text not null,
      Contact_Information text not null,
      Payment_Information text not null,
      FOREIGN KEY (Customer_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Customer_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Activities(ID),
      FOREIGN KEY (Customer_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Customer_ID) REFERENCES Site(URL)
);
CREATE TABLE Rental_Cars (
      Cars_ID int AUTO_INCREMENT PRIMARY key,
      Rental_Car_Brands varchar(50) not null,
      Location varchar(50) not null,
      Types_Of_Car varchar(100) not null,
      Price int not null,
      FOREIGN KEY (Cars_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (Cars_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Cars_ID) REFERENCES Site(URL)
);
CREATE TABLE Activities (
      ID int AUTO_INCREMENT PRIMARY key,
      Names_Of_Activities varchar(255) not null,
      Location varchar(50) not null,
      Description text not null,
      Price int not null,
      FOREIGN KEY (ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (ID) REFERENCES Site(URL),
      FOREIGN KEY (ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (ID) REFERENCES Payments(Payments_ID)
);
CREATE TABLE Reservations (
      Reservation_ID int AUTO_INCREMENT PRIMARY key,
      Flights varchar(255) not null,
      Hotels varchar(255) not null,
      Rental_Cars varchar(255) not null,
      Activities varchar(255) not null,
      FOREIGN KEY (Reservation_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Reservation_ID) REFERENCES Customer_Service_Center(AFM)
);
CREATE TABLE Airlines (
      Airlines_ID int AUTO_INCREMENT PRIMARY key,
      Airline_Name varchar(255) not null,
      Contact_Information text not null,
      FOREIGN KEY (Airlines_ID) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Flights(Flights_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Airlines_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Airlines_ID) REFERENCES Site(URL),
      FOREIGN KEY (Airlines_ID) REFERENCES Customers(Customer_ID)
);
CREATE TABLE Airports (
      Airports_ID int AUTO_INCREMENT PRIMARY key,
      Airport_Names varchar(255) not null,
      Location varchar(255) not null,
      FOREIGN KEY (Airports_ID) REFERENCES Airports(Airlines_ID),
      FOREIGN KEY (Airports_ID) REFERENCES Flights(Flights_ID),
      FOREIGN KEY (Airports_ID) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (Airports_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Airports_ID) REFERENCES Site(URL),
      FOREIGN KEY (Airports_ID) REFERENCES Customers(Customer_ID)
);
CREATE TABLE Reviews (
      Reviews_ID int AUTO_INCREMENT PRIMARY key,
      Review_For_Hotels text not null,
      Review_For_Rental_Cars text not null,
      Review_For_Activities text not null,
      Review_For_Airlines text not null,
      FOREIGN KEY (Reviews_ID) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (Reviews_ID) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Activities(ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Reviews_ID) REFERENCES Flights(Flights_ID)
);
CREATE TABLE Payments (
      Payments_ID int AUTO_INCREMENT PRIMARY key,
      Customer_Payments float not null,
      Date_Payments varchar(50) not null,
      Payment_Methods varchar(50) not null,
      FOREIGN KEY (Payments_ID) REFERENCES Flights(Flights_ID),
      FOREIGN KEY (Payments_ID) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (Payments_ID) REFERENCES Rental_Cars(Cars_ID)
);
CREATE TABLE Customer_Service_Center (
      AFM int AUTO_INCREMENT PRIMARY key,
      Address varchar(50) not null,
      Phone int(10) not null,
      Email varchar(20) not null,
      Owners_Name varchar(255) not null,
      Fax int(10) not null,
      FOREIGN KEY (AFM) REFERENCES Site(URL),
      FOREIGN KEY (AFM) REFERENCES Staff(AFM),
      FOREIGN KEY (AFM) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (AFM) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (AFM) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (AFM) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (AFM) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (AFM) REFERENCES Rental_Cars(Cars_ID)
);
Create TABLE Site(
      URL int(50) AUTO_INCREMENT PRIMARY key,
      Email varchar(50) not null,
      Phone int(10) not null,
      Address varchar(255) not null,
      Payment varchar(50) not null,
      Informations text not null,
      E_Tickets varchar(255) not null,
      Users varchar(255) not null,
      FOREIGN KEY (URL) REFERENCES Staff(AFM),
      FOREIGN KEY (URL) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (URL) REFERENCES Payments(Payments_ID),
      FOREIGN KEY (URL) REFERENCES Airports(Airports_ID),
      FOREIGN KEY (URL) REFERENCES Reservations(Reservation_ID),
      FOREIGN KEY (URL) REFERENCES Reviews(Reviews_ID),
      FOREIGN KEY (URL) REFERENCES Airlines(Airlines_ID),
      FOREIGN KEY (URL) REFERENCES Rental_Cars(Cars_ID),
      FOREIGN KEY (URL) REFERENCES Activities(ID),
      FOREIGN KEY (URL) REFERENCES Customers(Customer_ID),
      FOREIGN KEY (URL) REFERENCES Hotel(Hotel_ID),
      FOREIGN KEY (URL) REFERENCES Flights(Flights_ID)
);
Create TABLE Staff(
      AFM int(10) AUTO_INCREMENT PRIMARY key,
      AMKA int(9) not null,
      AMA int(10) not null,
      ID_Number varchar(8) not null,
      Passport_Number varchar(9) not null,
      Date_Of_Birth varchar(50) not null,
      Name varchar(255) not null,
      Surname varchar(255) not null,
      Phone int(10) not null,
      Viografiko text not null,
      Adress varchar(255) not null,
      Stratiotikes_Ypoxrewseis boolean,
      Contract text not null,
      FOREIGN KEY (AFM) REFERENCES Site(URL),
      FOREIGN KEY (AFM) REFERENCES Customer_Service_Center(AFM),
      FOREIGN KEY (AFM) REFERENCES Customers(Customer_ID)
);






ALTER TABLE Flights ADD FOREIGN KEY (Flights_ID) REFERENCES Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Flights ADD FOREIGN KEY (Flights_ID) REFERENCES Reservations(Reservation_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Flights ADD FOREIGN KEY (Flights_ID) REFERENCES Site(URL) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Flights ADD FOREIGN KEY (Flights_ID) REFERENCES Airports(Airports_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Flights ADD FOREIGN KEY (Flights_ID) REFERENCES Airlines(Airlines_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Flights ADD FOREIGN KEY (Flights_ID) REFERENCES Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Flights ADD FOREIGN KEY (Flights_ID) REFERENCES Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Hotel ADD FOREIGN KEY (Hotel_ID) REFERENCES Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Hotel ADD FOREIGN KEY (Hotel_ID) REFERENCES Rental_Cars(Cars_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Hotel ADD FOREIGN KEY (Hotel_ID) REFERENCES Activities(ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Hotel ADD FOREIGN KEY (Hotel_ID) REFERENCES Reservations(Reservation_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Hotel ADD FOREIGN KEY (Hotel_ID) REFERENCES Reviews(Reviews_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Hotel ADD FOREIGN KEY (Hotel_ID) REFERENCES Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Hotel ADD FOREIGN KEY (Hotel_ID) REFERENCES Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Customers ADD FOREIGN KEY (Customer_ID) REFERENCES Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customers ADD FOREIGN KEY (Customer_ID) REFERENCES Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customers ADD FOREIGN KEY (Customer_ID) REFERENCES Reservations(Reservation_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customers ADD FOREIGN KEY (Customer_ID) REFERENCES Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customers ADD FOREIGN KEY (Customer_ID) REFERENCES Reviews(Reviews_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customers ADD FOREIGN KEY (Customer_ID) REFERENCES Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customers ADD FOREIGN KEY (Customer_ID) REFERENCES Site(URL) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Activities ADD FOREIGN KEY (ID) REFERENCES Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Activities ADD FOREIGN KEY (ID) REFERENCES Site(URL) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Activities ADD FOREIGN KEY (ID) REFERENCES Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Activities ADD FOREIGN KEY (ID) REFERENCES Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Activities ADD FOREIGN KEY (ID) REFERENCES Reviews(Reviews_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Activities ADD FOREIGN KEY (ID) REFERENCES Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Reservations ADD FOREIGN KEY (Reservation_ID) REFERENCES Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reservations ADD FOREIGN KEY (Reservation_ID) REFERENCES Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reservations ADD FOREIGN KEY (Reservation_ID) REFERENCES Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reservations ADD FOREIGN KEY (Reservation_ID) REFERENCES Rental_Cars(Cars_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reservations ADD FOREIGN KEY (Reservation_ID) REFERENCES Airports(Airports_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reservations ADD FOREIGN KEY (Reservation_ID) REFERENCES Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reservations ADD FOREIGN KEY (Reservation_ID) REFERENCES Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES Airports(Airports_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES Flights(Flights_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES Reservations(Reservation_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES Reviews(Reviews_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES Site(URL) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airlines ADD FOREIGN KEY (Airlines_ID) REFERENCES  Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Airports ADD FOREIGN KEY (Airports_ID) REFERENCES  Airports(Airlines_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airports ADD FOREIGN KEY (Airports_ID) REFERENCES  Flights(Flights_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airports ADD FOREIGN KEY (Airports_ID) REFERENCES  Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airports ADD FOREIGN KEY (Airports_ID) REFERENCES  Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airports ADD FOREIGN KEY (Airports_ID) REFERENCES  Site(URL) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Airports ADD FOREIGN KEY (Airports_ID) REFERENCES  Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Reviews ADD FOREIGN KEY (Reviews_ID) REFERENCES  Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reviews ADD FOREIGN KEY (Reviews_ID) REFERENCES  Airlines(Airlines_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reviews ADD FOREIGN KEY (Reviews_ID) REFERENCES  Activities(ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reviews ADD FOREIGN KEY (Reviews_ID) REFERENCES  Rental_Cars(Cars_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reviews ADD FOREIGN KEY (Reviews_ID) REFERENCES  Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reviews ADD FOREIGN KEY (Reviews_ID) REFERENCES  Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Reviews ADD FOREIGN KEY (Reviews_ID) REFERENCES  Flights(Flights_ID) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Payments ADD FOREIGN KEY (Payments_ID) REFERENCES  Flights(Flights_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Payments ADD FOREIGN KEY (Payments_ID) REFERENCES  Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Payments ADD FOREIGN KEY (Payments_ID) REFERENCES  Rental_Cars(Cars_ID) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Site(URL) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Staff(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Reservations(Reservation_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Airports(Airports_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Reviews(Reviews_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Airlines(Airlines_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Customer_Service_Center ADD FOREIGN KEY (AFM) REFERENCES  Rental_Cars(Cars_ID) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Staff(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Payments(Payments_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Airports(Airports_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Reservations(Reservation_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Reviews(Reviews_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Airlines(Airlines_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Rental_Cars(Cars_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Activities(ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Hotel(Hotel_ID) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Site ADD FOREIGN KEY (URL) REFERENCES  Flights(Flights_ID) ON DELETE CASCADE ON UPDATE CASCADE;

ALTER TABLE Staff ADD FOREIGN KEY (AFM) REFERENCES  Site(URL) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Staff ADD FOREIGN KEY (AFM) REFERENCES  Customer_Service_Center(AFM) ON DELETE CASCADE ON UPDATE CASCADE;
ALTER TABLE Staff ADD FOREIGN KEY (AFM) REFERENCES  Customers(Customer_ID) ON DELETE CASCADE ON UPDATE CASCADE;
