```List list = new ArrayList();```   
is accepted by compiler but is error-prone, since developer can put any type of object to the list without causing a compiler error. For example,  
```list.add(1);``` and ```list.add("abc");``` are both acceptable. When you fetch the object out, you have to do a type casting, like,  

```Integer firstElement = (Integer) list.get(0);```,\s\s then, \s\s
```Integer secondElement = (Integer) list.get(1);``` will cause a runtime error.

To force the compiler to check the type, we use\s\s
```List<Integer> list = new ArrayList<>();```\s\s
Actually, the compiler will only check the type at the compile time, while erase the type at the runtime. 

