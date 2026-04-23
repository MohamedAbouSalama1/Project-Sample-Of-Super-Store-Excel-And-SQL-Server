Select * From Super_Store;

EXEC sp_rename 'dbo.Super_Store.[Order Date]', 'Order_Date', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Order ID]', 'Order_Id', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Row ID]', 'Row_Id', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Ship Date]', 'Ship_Date', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Ship Mode]', 'Ship_Mode', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Customer ID]', 'Customer_ID', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Customer Name]', 'Customer_Name', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Product ID]', 'Product_ID', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Sub-Category]', 'Sub_Category', 'COLUMN';
EXEC sp_rename 'dbo.Super_Store.[Product Name]', 'Product_Name', 'COLUMN';

Select City,Sub_Category 
From Super_Store;

Select Product_Name , Country
From Super_Store;

Select Max(Sales) AS Max_Sales,Category
From Super_Store
Group By Category;

Select Min(Profit) As Min_Sales,City 
From Super_Store
Group By City;

Select Min(Profit) As Min_Sales,City 
From Super_Store
Group By City;


Select Avg (Profit) As Avg_Profit From Super_Store;

Select*from Super_Store Where Profit > 200;                                                                                                 

Select Product_Name , SUBSTRING(Product_Name,1,4)As Short_Name_Of_Product From Super_Store;

Select Product_Name , len(Product_Name)As Len_Name_Of_Product From Super_Store;

Select Count (*) AS Number_Of_Product From Super_Store;

Select Product_Name,Max(Quantity) As Max_Quantity, Count (*) AS Number_Of_Product 
From Super_Store
Group By Product_Name
Having Count (*)>1 And Max(Quantity)>1;

Create View Max_Min_Profit As 

Select Max(Profit) As Max_Profit, Min(Profit) As Min_Perofit 

From Super_Store;


Create View Measure_Quantity As 

Select Product_Name,Quantity,

Case 
      When Quantity>20

      Then 'Good Store'
      
     When Quantity>50

      Then 'Very Good Store'

    Else 'Excellent'


   End As Measure

   From Super_Store;


  Create View Time_Of_Wait AS

Select Ship_Date, Datediff (Year,Ship_Date,GetDate())As How_Many_Year_Peerson_Wait
  From Super_Store

  Group By Ship_Date
  ;