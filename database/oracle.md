1. Truncate all data in all tables:   

        select 'truncate table ' || table_name || ';' from user_tables
        and then copy paste the result and run them

2. Delete all tables: 

        SELECT 'DROP TABLE "' || TABLE_NAME || '" CASCADE CONSTRAINTS;' FROM user_tables;
        and then copy paste the result and run them
