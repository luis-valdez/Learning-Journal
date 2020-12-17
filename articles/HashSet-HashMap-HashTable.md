# 1. HashSet vs HashMap vs HashTable
The goal of this article is to get a general idea of each one of these data structures, understand their similarities and differences.

To do so, we will look at some code snippets of each one of them to demonstrate their functionality and also we will focus on how they compare to each other.

## 2. HashSet
HashSet is part of the Java Collection Framework. It extends from the interface Set. This means that it is a collection which has no duplicate elements.

You can think of a HashSet as a list that has unique items and allows you to quickly verify if one of the items is present by taking advantage of the `hashCode()` functionality.

Let's see a real world example of a HashSet. Suppose we're building a command line interface system, and we want to:

1. Have a data structure with all the valid commands.
2. Be able to quickly verify if the input of the user is a valid command.

We can accomplish this using a HashSet:
```java
    public static void main(String[] args) {
        Set<String> commands = new HashSet();
        commands.add("install"); // Declare valid commands
        commands.add("update");
        commands.add("delete");
        
        String input = "install"; // Define user's input
        
        if (commands.contains(input)) { // Validate users input
            System.out.println("Hooray! Your command is valid");
        } else {
            System.out.println("Not a valid command");
        }
    }
```

Now that we have some notion about what a HashSet can do, let's dig in deeper.

### 2.1 **How does HashSet works under the hood?**

Here's how the constructor of `HashSet.java` looks like:
```java
    /**
     * Constructs a new, empty set; the backing <tt>HashMap</tt> instance has
     * default initial capacity (16) and load factor (0.75).
     */
    public HashSet() {
        map = new HashMap<>();
    }
```
I want to focus on the fact that a HashSet is actually backed by a `HashMap`. A better way to understand this is to take a look of how a HashSet adds new elements.
```java
public boolean add(E e) {
        return map.put(e, PRESENT)==null;
    }	
```
The main takeaways you should consider from this code snippet are:
- The parameter `E` indicates the element to be added.
- It uses the `.put()` method of a `map` to add a new element.
- The second parameter in the put method, `PRESENT` is just a dummy value declared in the `HashSet.java` class.

## 3. HashMap
We already saw how the HashSet works and that it is backed by a `HashMap` internally. So now let's see what is a HashMap and how does it work.

As its name says a HashMap is a `Map`, this means that it's a data structure that maps together a pair of two things: a `key` and a `value`. Each key is mapped to exactly one value, and we can use this key to retrieve the corresponding value.

Two important things to remember about HashMaps are:

1. Keys are unique.
2. Values can be repetead.

Let's look at an example. Imagine we want to create a phone directory where we will store the name of a person and their phone number. To do this we will store the person's name as a key and their phone aswell as the correspondent value.

Here is how we would do that with a HashMap:
```java
    public static void main(String[] args) {
        // We declare a HashMap that has String keys and Integer values
        HashMap<String, Integer> phoneDirectory  = new HashMap<>();
        // We add data to our phone directory
        phoneDirectory.put("Bob", 661234567);
        phoneDirectory.put("Alice", 661234567);
        phoneDirectory.put("Elizabeth", 12345678);

        // We can retrieve the value from any of them providing the key
        
        System.out.println(phoneDirectory.get("Alice")); // Prints 661234567
    }
```


## 3. HashTable
Here is where it gets interesting. What if I tell you that we can achieve exactly the same that we did in with the HashMap, but using a HashTable. Just by changing the type of object:
```java
    public static void main(String[] args) {
        
        // Notice we're now using a Hashtable instead of a HashMap
        Hashtable <String, Integer> phoneDirectory  = new Hashtable();
        phoneDirectory.put("Bob", 661234567);
        phoneDirectory.put("Alice", 661234567);
        phoneDirectory.put("Elizabeth", 12345678);

        System.out.println(phoneDirectory.get("Alice")); // Prints 661234567
    }
```
You're probably wondering right now, if they're the same why do both exist?

The answer to that question is that they're not exactly the same, there are some cases when you should use a HashTable instead of a Hashmap.

Here are some key differences that will help you decide between both of them:
- **Hashtable is thread safe**, HashMaps are not.
- **HashMaps can have one key null, and as many null values as you want**, HashTables can't have null values neither in a key or in values.
- HashMap uses iterator, wheras HashTable uses enumerator to iterate over values.


## 4. Conclusion
If you need a list of values that are unique and are quickly retrievable go for a HashSet.

When you have a key-value mapping scenario, go with either a HashMap or a HashTable. If you need have a single thread application go with the HashMap, else go with the HashTable.
