### Four isolation levels
Isolation Level 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Dirty read 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
Non-repeatable read 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
Phantom read  

READ_UNCOMMITTED
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
allowed
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
allowed
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
allowed  
READ_COMMITTED
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
prevented
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
allowed
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
allowed  
REPEATABLE_READ
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
prevented
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
prevented
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
allowed  
SERIALIZABLE
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
prevented
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
prevented
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
prevented  

#### Dirty read  
A dirty read happens when a transaction is allowed to read uncommitted changes of some other running transaction. 
This happens because there is no locking preventing it. 
In the picture above, you can see that the second transaction uses an inconsistent value as of the first transaction had rollbacked.

#### Non-repeatable read  
A non-repeatable read manifests when consecutive reads yield different results due to a concurring transaction that has just updated the record we’re reading. 
This is undesirable since we end up using stale data. 
This is prevented by holding a shared lock (read lock) on the read record for the whole duration of the current transaction.

#### Phantom read  
A phantom read happens when a second transaction inserts a row that matches a previous select criteria of the first transaction. 
We, therefore, end up using stale data, which might affect our business operation. 
This is prevented using range locks or predicate locking.

#### A database engine should provide  
* Locking facilities that preserve transaction isolation.  
* Logging facilities that ensure transaction durability. 
Even if the server hardware, operating system, or the instance of the Database Engine itself fails, the instance uses the transaction logs upon restart to automatically roll back any uncompleted transactions to the point of the system failure.  
* Transaction management features that enforce transaction atomicity and consistency. 
After a transaction has started, it must be successfully completed, or the instance of the Database Engine undoes all of the data modifications made since the transaction started.
#### good website  
https://vladmihalcea.com/2014/01/05/a-beginners-guide-to-acid-and-database-transactions/
https://technet.microsoft.com/en-us/library/ms190612(v=sql.105).aspx
