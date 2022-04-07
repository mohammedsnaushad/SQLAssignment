# SQLAssignment

Create database Cmpny;

use Cmpny;

Create table Customer (Id Int Primary key,Fname nvarchar(40),Lname nvarchar(40),City nvarchar(40),Country nvarchar(40),phone nvarchar(20));

create index IndexCustomerName on Customer(Fname);

Create table Ordertbl(orderId int Primary key,OrderDate time,OrderNumber nvarchar(10),CustomerId int foreign key references [Customer](Id),TotalAmount decimal(12,2));

create index IndexOrderCustomerId on ordertbl(CustomerId);

Create index IndexOrderDate on Ordertbl(OrderDate);

Create table product(productId Int primary key ,ProductName nvarchar(50),
UnitPrice decimal(12,2),package nvarchar (30),IsDiscontinued bit);

create index IndexproductSupplierId on Product(productId);

create index IndexproductName on product(productName);

Create table OrderItem(OrderitemId Int primary key,orderId int foreign key references Ordertbl(orderId),productId int foreign key references product(productId),UnitPrice decimal(12,2),Quantity int);

create index IndexOrderItemOrderId on OrderItem(OrderId);

create index IndexOrderItemProductId on OrderItem(ProductId);

Insert into Customer (Id,Fname,Lname,city,country,phone) values(111,'Abhi','jayan','Thrissur','India',7045128945),
(112,'Nirmal','Mohan','Cochin','India',8012459786),
(113,'Jishnu','Chethan','Banglore','India',9874561235),
(114,'shafi','Shahabaz','Chennai','India',8527419636),
(115,'Asif','Ali','Pune','India',7418529635);

Insert into Customer (Id,Fname,Lname,city,country,phone) values (116,'Mohammed','razeen','paris','france',55584562),
(117,'Jubaise','sha','Alain','Muscat',9874561);

Select * from Customer

Insert into Ordertbl(orderId,OrderDate,OrderNumber,CustomerId,TotalAmount) values (501,01-01-2022,101,111,115.00),
(502,02-01-2022,101,112,150.00),
(503,03-01-2022,101,113,200.00);


Insert into product (productId,ProductName,UnitPrice,package,IsDiscontinued)
Values(1,'Noodles',20.00,'For Children',0),
(2,' Chocolates',50.00,'wrapping paper',0),
(3,'packed soup',30.00,'plastic cup',0);


Insert into orderitem(orderitemId,OrderId,productId,UnitPrice,Quantity)
Values(001,501,1,20.00,5),
(002,502,2,50.00,2),
(003,503,3,30.00,4);

Select * from Customer;
--Display whose name starts with A or I
Select Country from Customer where Lname like 'A%' or lname like 'I%';

--Display whose name third letter is 'I'
select Fname,Lname from customer where Lname like '__I%';

--alter the firstname of customer and order table by adding not null
alter table Customer alter column Fname nvarchar(40) NOT NULL;

--alter customer  ordertable by adding not null DateTime
alter table Ordertbl alter column orderDate DtaeTime NOT NULL;
