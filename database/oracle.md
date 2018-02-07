1. Truncate all data in all tables:   

        select 'truncate table ' || table_name || ';' from user_tables
        and then copy paste the result and run them

2. Delete all tables: 

        SELECT 'DROP TABLE "' || TABLE_NAME || '" CASCADE CONSTRAINTS;' FROM user_tables;
        and then copy paste the result and run them

3. Copy rows and paste in the same table, but skip the PK: 

        1.
        BEGIN
 
          FOR r IN (SELECT * FROM hosts WHERE hostID > 1) 
          LOOP
            r.hostID := null;  -- For some reason, it will automatically change the null to the meaningful PK
            r.hostName  := r.hostID;
            INSERT INTO hosts VALUES r;
          END LOOP;

        END;
        
        
        2.
        CREATE TABLE Temp_Table AS SELECT * FROM MyTable where Column2 = 'Value2';
        UPDATE Temp_Table SET r.Column2 := 'NewValue2', r.Column3 := 'NewValue3';
        INSERT INTO MyTable SELECT * FROM Temp_Table;
        DROP TABLE Temp_Table;
        
        3. 
        INSERT INTO MyTable
          SELECT PK_Seq.nextval, 'NewValue2', 'NewValue3', Column4, Column5
            FROM MyTable WHERE Column2 = 'Value2'
        
4. Don't forget to commit after each query run!!!

5. There is no way to add empty string, oracle will internally change that to null; and you can only do that with columns which allow null. For columns which don't allow null, you can only query them by **IS NOT NULL**. 
