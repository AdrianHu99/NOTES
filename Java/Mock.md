1. Stub a method

If you need to stub a method, when you do:  

      Mockito.when(mock.method()).thenXYZ();
this will actually still call the method itself, and can cause something wrong (like NullPointerException).  
To avoid that, you need to do:  

      Mockito.doXYZ().when(mock).method();
      
For a static method, then you need to do: 

      PowerMockito.doReturn("something").when(MyClass.class);
      MyClass.myMethod(Matchers.anyString());
