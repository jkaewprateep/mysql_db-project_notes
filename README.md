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

👧💬 🎈 Simple by define of information services and tabular storages for data information and aggregation process make it easy from installation, development, testing, deployment until maintenance and services </br>.

```
CREATE TABLE ContractInfo(
	ContractID INT NOT NULL,
	StaffID INT NOT NULL,
	Salary DECIMAL (7,2) NOT NULL,
	Location VARCHAR (50) NOT NULL DEFAULT "Texas",
	StaffType VARCHAR (20) NOT NULL CHECK(StaffType = "Junior" OR StaffType = "Senior"),
	PRIMARY KEY (ContractID)
);

ALTER TABLE ContractInfo 
ADD CONSTRAINT FK_StaffID_ContractInfo
FOREIGN KEY (StaffID) REFERENCES Staff(StaffID);
```

## 🧸💬 ALTER table

```
ALTER TABLE Staff ADD CONSTRAINT PK_StaffID PRIMARY KEY (StaffID);

ALTER TABLE Staff MODIFY PhoneNumber INT NOT NULL;

ALTER TABLE Staff ADD Role VARCHAR(50) NOT NULL;

ALTER TABLE Staff DROP PhoneNumber;

ALTER TABLE FoodOrders ADD COLUMN OrderDate DATE NOT NULL;

ALTER TABLE FoodOrders ADD FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID);

ALTER TABLE FoodOrders DROP COLUMN OrderDate;

ALTER TABLE FoodOrders CHANGE Order_status DeliveryStatus VARCHAR(15);

ALTER TABLE FoodOrders RENAME OrderDeliveryStatus;
```

## 🧸💬 COLUMNS CONTAMINATION AND DATE FORMAT AND CONDITIONS

```
select CONCAT(LCASE(Name), "-", mg_orders.Quantity, "-", UCASE(OrderStatus)) from item, mg_orders where item.ItemID = mg_orders.ItemId;

select ROUND(Cost * 5 / 100, 2) AS "HandlingCost" from mg_orders;

select DATE_FORMAT(DeliveryDate, '%W') from mg_orders;

select *, COALESCE( DeliveryDate, "NOT DELIVERED" ), COALESCE( DATE_ADD(DeliveryDate, INTERVAL 30 DAY), "NOT DELIVERED" ) AS "TargetDate" from mg_orders;

select *, NULLIF( DeliveryDate, "2022-05-25" ), COALESCE( DATE_ADD(DeliveryDate, INTERVAL 30 DAY), "NOT DELIVERED" ) AS "TargetDate" from mg_orders;
```

## 🧸💬 Stored procedure

```
CREATE PROCEDURE GetListOfOrdersInRange( MinimumValue INT, MaximumValue INT ) SELECT * FROM Orders WHERE Cost BETWEEN MinimumValue AND MaximumValue;
CALL GetListOfOrdersInRange( 150, 600 );
```

## 🧸💬 Stored procedure with IF cause

```
DELIMITER // 

CREATE Procedure GetDiscount(OrderIDInput INT) 
     BEGIN 
         DECLARE cost_after_discount DECIMAL(7,2); 
         DECLARE current_cost DECIMAL(7,2); 
         DECLARE order_quantity INT; 
         SELECT Quantity INTO order_quantity FROM Orders WHERE OrderID = OrderIDInput; 
         SELECT Cost INTO current_cost FROM Orders WHERE OrderID = OrderIDInput; 
        IF order_quantity >= 20 THEN
          SET cost_after_discount = current_cost - (current_cost * 0.2);              
        ELSEIF order_quantity >= 10 THEN
          SET cost_after_discount = current_cost - (current_cost * 0.1); 
        ELSE SET cost_after_discount = current_cost;
        END IF;
    SELECT cost_after_discount; 
END//

DELIMITER ; 
```

## 🧸💬 Stored procedure with variable values return

```
DELIMITER //

CREATE PROCEDURE EvaluateProduct( product_id VARCHAR(255), sold_items_2020 DECIMAL(7,2), sold_items_2021 DECIMAL(7,2), sold_items_2022 DECIMAL(7,2) ) 
	BEGIN 
		DECLARE temp_sold_items_2020 DECIMAL(7,2); 		
		DECLARE temp_sold_items_2021 DECIMAL(7,2); 	
		DECLARE temp_sold_items_2022 DECIMAL(7,2); 	
		SELECT SUM(Quantity) INTO temp_sold_items_2020 FROM Orders WHERE ProductID IN ( product_id ) AND YEAR(Date) IN (  sold_items_2020 ) GROUP BY YEAR( Date );
		SELECT SUM(Quantity) INTO temp_sold_items_2021 FROM Orders WHERE ProductID IN ( product_id ) AND YEAR(Date) IN (  sold_items_2021 ) GROUP BY YEAR( Date );
		SELECT SUM(Quantity) INTO temp_sold_items_2022 FROM Orders WHERE ProductID IN ( product_id ) AND YEAR(Date) IN (  sold_items_2022 ) GROUP BY YEAR( Date );

		SELECT @sold_items_2020 := temp_sold_items_2020;
		SELECT @sold_items_2021 := temp_sold_items_2021;
		SELECT @sold_items_2022 := temp_sold_items_2022;
		
		SELECT temp_sold_items_2020, temp_sold_items_2021, temp_sold_items_2022;
	END//

DELIMITER ; 
```

## 🧸💬 Stored procedure with variable values update with rowID

```
DELIMITER // 

CREATE PROCEDURE UpdateBooking    ( booking_id INT, customer_id INT, booking_date DATE, tableNumber INT ) 
	BEGIN 
		DECLARE CURRENT_BOOKINGID INT; 
        DECLARE COUNT_BOOKINGID INT; 
		DECLARE MESSAGE VARCHAR(255);
        
        START TRANSACTION;
        
        SET CURRENT_BOOKINGID = ( SELECT MAX( BookingsID ) + 1 AS "Number" FROM littlelemondb.bookings GROUP BY BookingsID ORDER BY BookingsID DESC LIMIT 1 );
        
                SET COUNT_BOOKINGID = ( SELECT COUNT( BookingsID ) FROM littlelemondb.bookings WHERE BookingsID = ANY ( 

				SELECT BookingsID

					FROM littlelemondb.bookings
					WHERE TableNo = tableNumber
					AND BookingDate = booking_date
					) );

              
        IF COUNT_BOOKINGID < 1 THEN 
			SET MESSAGE = " - booking is not found";
			ROLLBACK;
        ELSE UPDATE littlelemondb.bookings 
			SET BookingDate = booking_date, 
            TableNo = tableNumber,
            CustomerID = customer_id,
            Customer_details_CustomerID = customer_id
            
            WHERE BookingsID = booking_id;
			COMMIT;
            SET MESSAGE = " - new booking updated";
		END IF;
        
		SELECT CONCAT("Table ", tableNumber, MESSAGE) AS "Booking status" ;
	END	//

DELIMITER ; 
```

## 🧸💬 INNER JOIN

```
SELECT Customers.FullName, Bookings.BookingID FROM Customers, Bookings where Customers.CustomerID = Bookings.CustomerID and Bookings.BookingDate = "2021-11-11";
```

## 🧸💬 REPLACE

```
REPLACE INTO Courses ( CourseName, Cost ) VALUES ("Kabasa", 20.00);
```

## 🧸💬 Temporary VIEW table

```
CREATE VIEW BookingsView AS SELECT BookingID, BookingDate, NumberOfGuests FROM Bookings WHERE BookingDate < "2021-11-13" AND NumberOfGuests > 3;
```

## 🧸💬 CREATE FUNCTION

```
CREATE FUNCTION FindCost(order_id INT) 
RETURNS DECIMAL (5,2) 
DETERMINISTIC 
RETURN (SELECT Cost FROM Orders WHERE OrderID = order_id);

CREATE FUNCTION FindSoldQuantity (year_number INT) 
RETURNS DECIMAL (7,2) 
DETERMINISTIC 
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
