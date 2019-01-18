TRUNCATE TABLE  

      You may want to do this when you hit the limit of primary key INT limit. You may encounter foreign key constraint issue. To resolve that, you need to
      1. drop constraint https://docs.microsoft.com/en-us/sql/relational-databases/tables/delete-foreign-key-relationships?view=sql-server-2017
      2. truncate the table
      3. create the constraint back https://docs.microsoft.com/en-us/sql/relational-databases/tables/create-foreign-key-relationships?view=sql-server-2017
