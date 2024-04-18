# mysql_db-project_notes
MySQL DB project notes - contribution for learning

🧸💬 Will comeback and complete after eating a banana leaf 🐑💬 ➰ แปลว่ามันหิวข้าวมาก

## 🧸💬 CREATE table

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

