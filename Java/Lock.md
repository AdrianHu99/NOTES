Finally will be called after the execution of the try or catch code blocks.

The only times finally won't be called are:

If you invoke System.exit();  
If the JVM crashes first;  
If the JVM reaches an infinite loop (or some other non-interruptable, non-terminating statement) in the try or catch block;  
If the OS forcibly terminates the JVM process; e.g. "kill -9 " on UNIX.  
If the host system dies; e.g. power failure, hardware error, OS panic, etcetera.  
If finally block is going to be executed by daemon thread and all other non daemon threads exit before finally is called.  

So if we have such a lock system: 

    try {
      if (!Locks.lock(backoff, Locks.LockInstance.xxx, hostGroupID, context)) {
        throw new SQLException("Can't grab lock!");
      }

      do something;
    } catch (Exception ex) {
      log.warn("Unable to grab lock!", ex);
    } finally {
      Locks.unlock(CloudSupportingServices.acquireLockContract(Locks.LockInstance.xxx, hostGroupID, context), context);
    }

When if process A successfully got the lock, and process B failed at it -> process A has not finished yet, and process B will throw exception, but `finally` block will still be executed and trying to unlock that lock which A holds -> lock inconsistency.
