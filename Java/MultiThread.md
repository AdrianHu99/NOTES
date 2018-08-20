1. If the method is synchronized, then it equals to synchronized(this);  

2. If synchronized method is in a static method of a class, then it equals to synchronized(T.class), and we can not use synchronized(this);  

3. If some exception are thrown during the thread is running, to avoid that, use try catch and do rollback.  

4. volatile - when this variable changes, java will notify other threads that read this variable, that the variable in their memory expires, please read the most recent value from this variable.

5. volatile vs. synchronize  

    volatile only makes sure of visibility  
    synchronize makes sure of visibility and atomicity  
    volatile has much better performance than synchronization
    
    
6. AtomicXXX also makes sure of atomicity and has better performance than synchronization   


      But if we have such code:  
      if (count.get() < 999) {  
          count.incrementAndGet();  
      }  
  
  
    Then it will not follow atomicity, because something can happen between the if and incrementAndGet()

7. Don't use string as the lock object, as s1 s2 may point to the same string object.  

8. 
