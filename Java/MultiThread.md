1. If the method is synchronized, then it equals to synchronized(this);  

2. If synchronized method is in a static method of a class, then it equals to synchronized(T.class), and we can not use synchronized(this);  
