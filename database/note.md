### Basic information

* **Identity column**  
a column (also known as a field) in a database table that is made up of values generated by the database. 
This is much like an AutoNumber field in Microsoft Access or a sequence in Oracle.  

* **The order of returned result**  
It is never guaranteed that the returned result by do select is ordered unless we add ORDER BY, no matter it is ORACLE or SQL SERVER.

* **How to copy a row and insert that to the same table**  

      INSERT INTO [dbo].[systemevents]  
             ([AdministratorID]  
             ,[TargetType]  
             ,[TargetID]  
             ,[TargetName]  
             ,[Time]  
             ,[Number]  
             ,[DescriptionResourceKey]  
             ,[DescriptionToFormat]  
             ,[Debug]  
             ,[OBJECTXML]  
             ,[AUDITXML]  
             ,[ManagerNodeID]  
             ,[AUDITXMLCOMPRESSED]  
             ,[TagSetID]  
             ,[Origin]  
             ,[DescriptionResourceNamespace])    

      select [AdministratorID]
                 ,[TargetType]
                 ,[TargetID]
                 ,[TargetName]
                 ,[Time]
                 ,[Number]
                 ,[DescriptionResourceKey]
                 ,[DescriptionToFormat]
                 ,[Debug]
                 ,[OBJECTXML]
                 ,[AUDITXML]
                 ,[ManagerNodeID]
                 ,[AUDITXMLCOMPRESSED]
                 ,[TagSetID]
                 ,[Origin]
                 ,[DescriptionResourceNamespace]
      from systemevents
      where SystemEventID = 9395

      GO 10000
      
Basically it will copy the systemevent 9395 and insert that row for 10000 times


* **find by time**  

      SELECT * from alert2s where alerttypeid = 28 and timeraised <=  TO_DATE('21/07/16', 'DD/MM/YY');
      
      
* **disable foreign key constraints**
      
      ALTER TABLE Purchasing.PurchaseOrderHeader  
      NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
      
* **Reseed if you delete and want to reuse the primary key**

      DBCC CHECKIDENT ('HOSTGROUPS', RESEED, 211); 
      -- Could be any number, as long as it's the last one
      
      
* **ORACLE use NULL LAST by default when sorting, while SQL SERVER use NULL FIRST by default for sorting**

* **If we want to copy a row to the same table but want to change some columns, what we can do is: **

      select * into temptable from TABLENAME where ID = 1
      alter table temptable drop column columnA
      update temptable set columnB = NULL
      insert into TABLENAME select * from temptable

