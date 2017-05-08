## Simple Factory  

![](https://github.com/adrrrrrrrian/notes/blob/master/Java/Design%20Patterns/Simple%20Factory.PNG)

The chart factory will have a static getInstance() method, it will be responsible for creating instances based on the input.



## Factory Method  

![](https://github.com/adrrrrrrrian/notes/blob/master/Java/Design%20Patterns/Factory%20Method.PNG)

The difference between factory method and simple factory method is that factory method will have corresponding factory for each product.


## Abstract Factory Method

![](https://github.com/adrrrrrrrian/notes/blob/master/Java/Design%20Patterns/Abstract%20Factory%20Method.PNG)

Abstract factory method is used for a set of different products, instead of just one product in factory method. It somehow does not follow 
open close principle, as when one more product is added to the set, the abstract factory will have to be modified. But it performs well 
when you want to add a new set of products. 
