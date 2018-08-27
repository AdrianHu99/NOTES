1. Collectors.toSet() returns an unordered Set, and please remember Set does not have any duplicate elements.
2. Arrays.toList() will return a fixed-size Array, we can not add() or remove() from there.   
        
        To solve this, we need to do a *new LinkedList<>(Arrays.asList(all));*  

3. 
