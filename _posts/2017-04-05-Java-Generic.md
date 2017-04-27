##### ```List list = new ArrayList()``` v.s ```List<Integer> list = new ArrayList<>()```  

```
List list = new ArrayList();
list.add(1);
list.add("abc");
Integer firstElement = (Integer) list.get(0);
Integer secondElement = (Integer) list.get(1); //typecast runtime error

List<Integer> list = new ArrayList<>();
list.add(1);
// list.add("abc"); //typecast compile time error

```

```List list = new ArrayList()``` is accepted by the compiler but may cause a typecast runtime error. This is because a developer can put any type of object to the list without causing a compiler error. For example,
```list.add(1)``` and
```list.add("abc")```
are both acceptable. When we fetch the object out, we have to do a type casting, then ```Integer secondElement = (Integer) list.get(1)``` 
will cause a runtime error.


```List<Integer> list = new ArrayList<>()``` will force the compiler to check the type at the compile time. Actually, the compiler will only check the type at the compile time, and erase the type at the runtime. 

##### ```List<? extends Object> list = new ArrayList<Integer>()```  

```
ArrayList<Integer> arrayList = new ArrayList<Integer>();
List<? extends Object> list = arrayList;

arrayList.add(1);
// list.add(2); //compiler error
list.get(0);

```