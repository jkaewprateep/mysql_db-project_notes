# mysql_db-project_notes
MySQL DB project notes - contribution for learning [META Advanced MySQL Topics](https://coursera.org/share/f475813ed222acfa20ff3840f5c8b358)

🧸💬 Will comeback and complete after eating a banana leaf 🌳🍌 🐑💬 ➰ แปลว่ามันหิวข้าวมาก

<p align="center" width="100%">
    <img width="34%" src="https://github.com/jkaewprateep/mysql_db-project_notes/blob/main/Database_engineerproject_instructor.png">
    <img width="34%" src="https://github.com/jkaewprateep/mysql_db-project_notes/blob/main/MySQL_advanced_topics_instructor.png">
    <img width="29%" src="https://github.com/jkaewprateep/mysql_db-project_notes/blob/main/08.jpg"> </br>
    <b> Database project | MySQL advanced | My favorite teacher 💃( 👩‍🏫 ) </b> </br>
    <b> Pictures from the Internet </b> </br>
</p>

## 🧸💬 CREATE table

👧💬 🎈 Simple by definition of information services and tabular storages for data information and aggregation process make it easy from installation, development, testing, deployment until maintenance and services </br>
🦤💬 ER-diagrams are useful at this stage when someone thinks it is work time amount on a simple chart diagram when they can start defining tables and procedures right-the-way, look into this side when all meta information is confirmed and process related are validated of data fields information. Simple database columns field mapping is easy and simple as eyes seeing but aggregated results do not always to be first-level observation, aggregation including time intervals, and update required information because sometimes it does not include data information in bale only but actions from users or results from confirmation process. </br>
💃( 👩‍🏫 )💬 Some examples of web-services response with database application when results from query interfaces response when it is ready or stages message communication, this kind of messages communication repeatedly as cycle and it reply with information instant when it ready but only complete filed flagged, aggregation of this kind of information required communications and data flow diagrams. </br>
🦭💬 Dashboard not updated‼️  🐑💬 ➰ It is updated with it ready you can settings for multiple stage responses for query value with where conditions. 🐯💬 Not my TCP/IP. </br>

```
🧸💬 Create table SQL statement syntax with required columns, default settings, value types, NULL value, and Primary Key.
CREATE TABLE ContractInfo(
	ContractID INT NOT NULL,
	StaffID INT NOT NULL,
	Salary DECIMAL (7,2) NOT NULL,
	Location VARCHAR (50) NOT NULL DEFAULT "Texas",
	StaffType VARCHAR (20) NOT NULL CHECK(StaffType = "Junior" OR StaffType = "Senior"),
	PRIMARY KEY (ContractID)
);

🧸💬 Add database table index to the table with foreigner reference. 
ALTER TABLE ContractInfo 
ADD CONSTRAINT FK_StaffID_ContractInfo
FOREIGN KEY (StaffID) REFERENCES Staff(StaffID);
```

🐑💬 ➰ Registration method, they are matric of values submitted to the event listener and there are multiple event listeners depending on their functions, architecture, communication methods, and user requirements when forwarding message services available with message server services and information for authentication servers and registration server as required at the first step of interactions beginning. </br>
👧💬 🎈 Reply of the message is separated into multiple stages of communication by the time response and step required by actions to perform when message communication message initial request, this kind of communication message works as where cause in the database with partial information response possible. </br>

<p align="center" width="100%">
    <img width="40%" src="https://github.com/jkaewprateep/mysql_db-project_notes/blob/main/DekDee_Client.png"> </br>
    <b> My simple client free for customer, embedded message for CTI communications </b> </br>
</p>

💃( 👩‍🏫 )💬 The trends of automation batch process with ETL processes such as Apache Spark, and data warehouse as micro-services deployment for instant deployment. Similarly to this allows fast deployment using Kubernetes or Docker applications with instant run time library deployment support. </br>
🐣💬 The login process by comparing username update status and not update status for time login and update value is specific in some database application 🥹💬 That is a secret hidden in the application not directly in the database when they query, first they will talk about it. </br> 
🦭💬 Linux OS capable commands, notifications, and actions for remote services activation and I do not need to create dedicated users to start applications for the remote services for application and database security. </br>
🦤💬 ```Deployment scripts```, ```installation```, and ```migration scripts``` for databases and applications are important. They are working with ```validation steps``` and this creates ```advantage of these SQL commands``` in our notes. </br>

<p align="center" width="100%">
    <img width="40%" src="https://github.com/jkaewprateep/mysql_db-project_notes/blob/main/application_withdatabase.png"> </br>
    <b> My simple client with database communication on web application engine support RedHat and Debian </b> </br>
</p>

## 🧸💬 ALTER table

🧸💬 ```ALTER table```, ```inform``` the database server of the table object and ```ready for the schema``` to apply for new settings or the complete process can be blocked of the next command generated to apply. </br>
🐐💬 ➰ There is ```update-alter``` action resulting in a new record differentiated when column names are different or updated but today update command and common command are included realted to schema activity if they are required. </br>


```
🧸💬 Ready table Staff and create a primary index on column StaffID with the name PK_StaffID.
ALTER TABLE Staff ADD CONSTRAINT PK_StaffID PRIMARY KEY (StaffID);

🧸💬  Ready table Staff and update PhoneNumber column, value type, and attribute.
ALTER TABLE Staff MODIFY PhoneNumber INT NOT NULL;

🧸💬  Ready table Staff and update PhoneNumber column, value type, and attribute.
ALTER TABLE Staff ADD Role VARCHAR(50) NOT NULL;

🧸💬  Ready table Staff and remove PhoneNumber column.
ALTER TABLE Staff DROP PhoneNumber;

🧸💬  Ready table FoodOrders and create one column named OrderDate with attributes.
ALTER TABLE FoodOrders ADD COLUMN OrderDate DATE NOT NULL;

🧸💬  Ready table FoodOrders and create one foreign key from column name CustomerID to table name Customers with column name CustomerID.
ALTER TABLE FoodOrders ADD FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID);

🧸💬  Ready table FoodOrders and remove column OrderDate.
ALTER TABLE FoodOrders DROP COLUMN OrderDate;

🧸💬  Ready table FoodOrders and update columns Order_status and DeliveryStatus with type VARCHAR(15).
ALTER TABLE FoodOrders CHANGE Order_status DeliveryStatus VARCHAR(15);

🧸💬  Ready table FoodOrders and rename to OrderDeliveryStatus.
ALTER TABLE FoodOrders RENAME OrderDeliveryStatus;
```

## 🧸💬 COLUMNS CONCATENATION AND DATE FORMAT AND CONDITIONS

🦭💬 What is ```internal database concatenation ⁉️``` </br>
🐐💬 ➰ In the past alter table was required for every activity and they are separated by user permission and database permission, alter ```does not immediately update``` of the target table or object instant but it requires application. Select and update are used for the validation process, someone can ```alter the table for concatenate value``` which is a single called internal concatenate and there are many of ways depending on your ```database security administrator```. 🐐💬 ➰ 🥊💥 Panus I did not see SQL Central email this year, may be he need to go to work lah hahaha~~! </br>   

```
🧸💬 Concatinate of columns Name, "-", Quantity, "-" and OrderStatus.
select CONCAT(LCASE(Name), "-", mg_orders.Quantity, "-", UCASE(OrderStatus)) from item, mg_orders where item.ItemID = mg_orders.ItemId;

🧸💬 Round up the Cost column Cost with the calculation value and set the new name as HandlingCost.
select ROUND(Cost * 5 / 100, 2) AS "HandlingCost" from mg_orders;

🧸💬 Apply Date format to column DeliveryDate with weekday format string indicator.
select DATE_FORMAT(DeliveryDate, '%W') from mg_orders;

🧸💬 Compare not null for column name DeliveryDate, if not found set it to "NOT DELIVERED".
select *, COALESCE( DeliveryDate, "NOT DELIVERED" ), COALESCE( DATE_ADD(DeliveryDate, INTERVAL 30 DAY), "NOT DELIVERED" ) AS "TargetDate" from mg_orders;

🧸💬 Return NULL by conditions, compare not null and set target value.
select *, NULLIF( DeliveryDate, "2022-05-25" ), COALESCE( DATE_ADD(DeliveryDate, INTERVAL 30 DAY), "NOT DELIVERED" ) AS "TargetDate" from mg_orders;
```

## 🧸💬 Stored procedure

🐑💬 ➰ What is the ```delays process call update ⁉️``` </br>
🐐💬 ➰ ```Congession of activities``` from many types of clients in operations may cause some ```insert/update processes``` to require delays time for reference numbers or selected columns. Create a procedure that can process by itself and return when it finishes without delays from request, no delays mean interval gaps from multiple updates because they can be ```handled by the database not by client request```. </br>
🐐💬 ➰ Delay process can cause ```debugging from negotiation messages communications```. </br>

```
🧸💬 Create a procedure or store procedure with input parameters and dataset result output as display.
CREATE PROCEDURE GetListOfOrdersInRange( MinimumValue INT, MaximumValue INT ) SELECT * FROM Orders WHERE Cost BETWEEN MinimumValue AND MaximumValue;

🧸💬 Call the created procedure.
CALL GetListOfOrdersInRange( 150, 600 );
```

## 🧸💬 Stored procedure with IF cause

🐣💬 What is ```IF CAUSE``` procedure statement ⁉️ </br>
🐐💬 ➰ When you are not aware of SQL statement syntax often found with ```THEN``` and ```tab indent```, not guaranteed return from condition means they can return the matching value ```condition met``` or return ```NULL```. Use case condition statement handle matching and often use ```THEN``` in the statement does not consume of the extra process. 🦤💬 Business object, they are using SQL statement syntax, internally integration services and report service they support of many application but knowledge transfer to new company. </br> 
🐣💬 There are use cases of ```guarantee return``` and ```non-guarantee return``` when the process is a priority and time response is a priority, often use ```return``` or ```break``` if available. </br>

```
🧸💬 Set delimiter syntax to // because of multiple client types support.
DELIMITER // 

🧸💬 Create a procedure name EvaluateProduct with input parameter and input parameter types.
CREATE Procedure GetDiscount(OrderIDInput INT)
     🧸💬 Begin by telling of the procedure statement block.
     BEGIN
         🧸💬 Declare variables.
         DECLARE cost_after_discount DECIMAL(7,2); 
         DECLARE current_cost DECIMAL(7,2); 
         DECLARE order_quantity INT;
         🧸💬 Select and save dataset results into target declared variables.
         SELECT Quantity INTO order_quantity FROM Orders WHERE OrderID = OrderIDInput; 
         SELECT Cost INTO current_cost FROM Orders WHERE OrderID = OrderIDInput;

	🧸💬 IF cause statement.
        IF order_quantity >= 20 THEN
          SET cost_after_discount = current_cost - (current_cost * 0.2);              
        ELSEIF order_quantity >= 10 THEN
          SET cost_after_discount = current_cost - (current_cost * 0.1); 
        ELSE SET cost_after_discount = current_cost;
        END IF;

    🧸💬 For display result set.
    SELECT cost_after_discount; 
🧸💬 End by telling of the procedure statement block.
END//

🧸💬 Set delimiter syntax to ;
DELIMITER ; 
```

## 🧸💬 Stored procedure with variable values return

👧💬 🎈 What is the ```external variables indicator ⁉️ ```. </br>
🐐💬 ➰ By intention some ```SQL developers``` create ```external variables``` or ```shared variables``` for access them later, this behavior allows some applications to ```query records``` or selection interactions for reports and matching of ```CTI user's registration``` but this method does not guarantee results please use CTI interfaces provided. </br>
👤💬 It is our plan, to lures you with high-performance values ... open request for full report guarantee with detail. 🐑💬 ➰ It is internal use but it is a value we had interface you can use more easily and have updates. </br>

```
🧸💬 Set delimiter syntax to // because of multiple client types support.
DELIMITER //

🧸💬 Create a procedure name EvaluateProduct with input parameter and input parameter types.
CREATE PROCEDURE EvaluateProduct( product_id VARCHAR(255), sold_items_2020 DECIMAL(7,2), sold_items_2021 DECIMAL(7,2), sold_items_2022 DECIMAL(7,2) )
	🧸💬 Begin by telling of the procedure statement block.
	BEGIN
		🧸💬 Declare variables.
		DECLARE temp_sold_items_2020 DECIMAL(7,2); 		
		DECLARE temp_sold_items_2021 DECIMAL(7,2); 	
		DECLARE temp_sold_items_2022 DECIMAL(7,2);
		🧸💬 Select and save dataset results into target declared variables.
		SELECT SUM(Quantity) INTO temp_sold_items_2020 FROM Orders WHERE ProductID IN ( product_id ) AND YEAR(Date) IN (  sold_items_2020 ) GROUP BY YEAR( Date );
		SELECT SUM(Quantity) INTO temp_sold_items_2021 FROM Orders WHERE ProductID IN ( product_id ) AND YEAR(Date) IN (  sold_items_2021 ) GROUP BY YEAR( Date );
		SELECT SUM(Quantity) INTO temp_sold_items_2022 FROM Orders WHERE ProductID IN ( product_id ) AND YEAR(Date) IN (  sold_items_2022 ) GROUP BY YEAR( Date );

		🧸💬 Set variables for output call by external process.
		SELECT @sold_items_2020 := temp_sold_items_2020;
		SELECT @sold_items_2021 := temp_sold_items_2021;
		SELECT @sold_items_2022 := temp_sold_items_2022;

		🧸💬 For display result set separated from external return variables.
		SELECT temp_sold_items_2020, temp_sold_items_2021, temp_sold_items_2022;

	🧸💬 End by telling of the procedure statement block.
	END//

🧸💬 Set delimiter syntax to ;
DELIMITER ; 
```

## 🧸💬 Stored procedure with variable values update with rowID

🐑💬 ➰ How do ```telecommunication applications work with databases```, I always attach datasets and results set table with an application that allows ```synchronizing update data records``` if required because I do not like to frequently update databases. </br>
👧💬 🎈 That is a good idea for application, database, and security but some requirements they are working on central database update for ```guarantee transactions communication solution```. Application services or communication message application is the first task and only requires query update of the database with different primary table keys. </br>
🐐💬 ➰ Even if the ```same procedure is called twice``` they are on ```different external variables``` if they return and you can use object references the same as table columns. ```👤💬⁉️ How do you know that ⁉️``` </br>

```
🧸💬 SET new delimiter syntax to //
DELIMITER // 

🧸💬 Create a procedure name EvaluateProduct with input parameter and input parameter types.
CREATE PROCEDURE UpdateBooking    ( booking_id INT, customer_id INT, booking_date DATE, table number INT )
	🧸💬 Begin by telling of the procedure statement block.
	BEGIN
		🧸💬 Declare variables.
		DECLARE CURRENT_BOOKINGID INT; 
        	DECLARE COUNT_BOOKINGID INT; 
		DECLARE MESSAGE VARCHAR(255);

		🧸💬 Start transaction process statement.
	        START TRANSACTION;
	
		🧸💬 Save target BookingsID to variable name CURRENT_BOOKINGID.
	        SET CURRENT_BOOKINGID = ( SELECT MAX( BookingsID ) + 1 AS "Number" FROM littlelemondb.bookings GROUP BY BookingsID ORDER BY BookingsID DESC LIMIT 1 );
	
		🧸💬 Save the target number of BookingsID found to the variable name COUNT_BOOKINGID.
	        SET COUNT_BOOKINGID = ( SELECT COUNT( BookingsID ) FROM littlelemondb.bookings WHERE BookingsID = ANY ( 
	
					SELECT BookingsID
	
						FROM littlelemondb.bookings
						WHERE TableNo = tableNumber
						AND BookingDate = booking_date
						) );
	
	        🧸💬 IF cause statement      
	        IF COUNT_BOOKINGID < 1 THEN 
			SET MESSAGE = " - booking is not found";
	
			🧸💬 Rollback transaction process statement.
			ROLLBACK;
	
		🧸💬 ELSE then updates the record with target values.
		ELSE UPDATE littlelemondb.bookings 
				SET BookingDate = booking_date, 
	            TableNo = tableNumber,
	            CustomerID = customer_id,
	            Customer_details_CustomerID = customer_id
	            
	            WHERE BookingsID = booking_id;
				COMMIT;
	            SET MESSAGE = " - new booking updated";
			END IF;
	
		🧸💬 For display result set.
		SELECT CONCAT("Table ", tableNumber, MESSAGE) AS "Booking status" ;

	🧸💬 End by telling of the procedure statement block.
	END	//

🧸💬 SET delimiter syntax to ;
DELIMITER ; 
```

## 🧸💬 INNER JOIN

🐑💬 ➰ Try to use ```INNER join``` because of the resultset when calling.  🦭💬 But you call ```outer join``` in ```LINQ``` than inner join </br>
🐑💬 ➰ I think I missed some lines here, I like to find some details out of the ```dot notation``` and ```object explorer``` that can help with application capacity. </br> 
🦭💬 I remember you use outer join for most of the query, lower for string comparisons, and string ```switch case``` for conditions. </br>
🐑💬 ➰ That is because ```it should work as it displays```, I like to hack testers when they test the program running smoothly but they review their test cases. </br>

```
🧸💬 Inner join tables Bookings and Customers
SELECT Customers.FullName, Bookings.BookingID FROM Customers, Bookings where Customers.CustomerID = Bookings.CustomerID and Bookings.BookingDate = "2021-11-11";
```

## 🧸💬 REPLACE

🦭💬 ```Not only update or insert``` but we ```hardly update```, data engineers have some work in here. </br>
🐑💬 ➰ That is because it does not ```validate some relationships``` but they need to perform ```instant of actions```, ```aggregation table``` and ```trigger``` need to be defined. </br>

```
🧸💬 Update or insert into table Courses, is there multiple modes?
REPLACE INTO Courses ( CourseName, Cost ) VALUES ("Kabasa", 20.00);
```

## 🧸💬 Temporary VIEW table

👧💬 🎈 ```Temporary table view``` is ```partitioned``` because they are working internally for intermitted results. </br>
🦭💬 What is ```partition hacking⁉️``` </br>
🐐💬 ➰ You ```cannot create a new view``` or change the view records selection conditions but you can ```create a new table with a similar structure```, in selection use ```full name specification```. ```👤💬 Booo~ ``` </br>

```
🧸💬 Create of temporary table view with parameters input and selection conditions.
CREATE VIEW BookingsView AS SELECT BookingID, BookingDate, NumberOfGuests FROM Bookings WHERE BookingDate < "2021-11-13" AND NumberOfGuests > 3;
```

## 🧸💬 CREATE FUNCTION

🐑💬 ➰ In security and application requirements, procedures or prepared statements need a return value for some application ```remote execution event```. Some security engineers track of input/output of this function because of ```validation results``` and ```similarity execution costs``` for determination. </br>
🦭💬 There are some reasons for monitoring and categorizing tasks as procedure or execution processes from ```similarity values return```, the priority of output changes, and ```application in communications```. Find one application that works often in response to the same message with the same behavior you can divide the system into clusters. </br>

```
🧸💬 Create a function with input parameters.
CREATE FUNCTION FindCost(order_id INT)

🧸💬 Specific return type for the creating function.
RETURNS DECIMAL (5,2)

🧸💬 To return value from this thread execution.
DETERMINISTIC

🧸💬 Return value.
RETURN (SELECT Cost FROM Orders WHERE OrderID = order_id);

- - -
🧸💬 Create a function with input parameters.
CREATE FUNCTION FindSoldQuantity (year_number INT)

🧸💬 Specific return type for the creating function.
RETURNS DECIMAL (7,2)

🧸💬 To return value from this thread execution.
DETERMINISTIC

🧸💬 Return value.
RETURN (select SUM(Orders.Quantity) from Products, Orders where Products.ProductID = Orders.ProductID AND Products.ProductID = "P3" AND YEAR(Orders.Date) IN ( year_number ) GROUP BY Products.ProductID);
```

## 🧸💬 CREATE TRIGGER

```
CREATE TRIGGER OrderQtyCheck  
  BEFORE INSERT ON Orders  
  FOR EACH ROW  
BEGIN 
  IF NEW.Quantity < 0 THEN  
    SET NEW.Quantity = 0; 
  END IF; 
END;
```

## 🧸💬 EXPLAIN and INDEXES
```
SELECT SUBSTRING( ReverseFullName, 1, 4 ) AS "FIRSTNAME" FROM Employees WHERE SUBSTRING( ReverseFullName, 1, 4 ) = "Tolo";

EXPLAIN SELECT SUBSTRING( ReverseFullName, 1, 4 ) AS "FIRSTNAME" FROM Employees WHERE SUBSTRING( ReverseFullName, 1, 4 ) = "Tolo";
```

## 🧸💬 JSON object

```
select ActivityID, Properties->'$.Order', Properties->'$.ClientID', Properties->'$.ProductID' from Activity WHERE Properties->'$.Order' = "True";

SELECT Activity.Properties ->>'$.ProductID' 
AS ProductID, Products.ProductName, Products.BuyPrice, Products.SellPrice 
FROM Products INNER JOIN Activity 
ON Products.ProductID = Activity.Properties ->>'$.ProductID' 
WHERE Activity.Properties ->>'$.Order' = "True";
```
