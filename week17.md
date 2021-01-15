## 1. Strings in Java
- Strings in Java are not a primitive data type
- Java has a class named String
- All Strings that we implement are instances of said class
- Strings are immutable, their values remain constant after they're created

### 1.1 String Pool
The String pool is a special memory region, located in the Heap, where Strings are allocated. The reason that the String Pool exists is to try to optimize memory. For example if we create the following strings
```java
String s1 = "Luis"
String s2 = "Luis"
```
The JVM will optimize memory by storing only one copy of the value `Luis`, so `s1` and `s2` can reference the same value.

### 1.2 Different ways of initializing a String
There is something courious about strings, and that is peculiar. And that is that you can initialize them in 2 different ways.
```java
String s1 = "Luis";
String s2 = new String("Luis");
```
### 1.3 Comparing Strings
There is a difference if you compare Strings using `==` or the `.equals` operator. And we can appreciate that in this example.
```java
String s1 = "Luis";
String s2 = new String("Luis");

if(s1 != s2) System.out.println("True, because == will comparate memory reference instead of actual values");
if(s1.equals(s2)) System.out.println("True, because .equals is comparing actual values instead of memory reference");
```

### Array vs ArrayList in Java
|                 | Array                                                                                                                                    | ArrayList                                                                                                                                                    | Details                                                                                                                                                   |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Declaration     | int[] arr = new int[10];                                                                                                                 | ArrayList<Type> arrList = new ArrayList();                                                                                                                   | - Arrays need to be initialized with a fixed size<br>- ArrayList have dynamic size                                                                         |
| Origin          | It comes from basic Java functionality                                                                                                   | It comes with the Collections Java Framework                                                                                                                 | - To use ArrayLists you need to import a class<br>- ArrayLists have methods to access and modify its members<br>- Arrays members are accessed trough `[]` |
| Type of members | Can contain both primitive datatypes and objects<br>(only one datatype at the same time)                                                 | ArrayLists only supports object entries                                                                                                                      | - If you use `arrList.add(1)` It will convert it to an Integer object.                                                                                    |
| Storage         | If the datatype of the array is primitive, they're stored at a contiguous location.<br><br>If not, the storage is similar as ArrayLists. | Members of ArrayLists are always references to objects at different memory locations.<br><br>Therefore the objects are never stores in contiguous locations. | - ArrayLists have many methods like `indexOf` and `remove` which are not supported by Arrays                                                              |
