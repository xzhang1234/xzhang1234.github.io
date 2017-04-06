1. ```static``` class  
..a. no top-level ```static``` class
..b. only nested ```static``` class  
...```public class A {
	public static class B {
	}
      }
      B b = new B();```
Or  
...```public class A {  
        public class B {
        }
      }
      A a = new A();
      B b = a.new B();```  
 
