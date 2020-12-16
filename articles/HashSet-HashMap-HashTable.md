# HashSet vs HashMap vs HashTable

## HashSet
HashSet is part of the Java Collection Framework. It extends from the interface Set. This means that it is a collection which has no duplicate elements.

You can think of a HashSet as a list that has unique items and allows you to quickly verify if one of the items is present by taking advantage of the `hashCode()` functionality.

Let's see a real world example of a HashSet. Suppose we're building a command line interface system, and we want to:

1. Have a data structure with all the valid commands.
2. Be able to quickly verify if the input of the user is a valid command.

We can accomplish this using a HashSet:
```java
    public static void main(String[] args) {
        Set<String> commands = new HashSet();
        commands.add("install"); //Declare valid commands
        commands.add("update");
        commands.add("delete");
        
        String input = "install"; //Define user's input
        
        if (commands.contains(input)) { //Validate users input
            System.out.println("Hooray! Your command is valid");
        } else {
            System.out.println("Not a valid command");
        }
    }
```

Now that we have some notion about what a HashSet can do, let's dig in deeper.

### **How does HashSet works under the hood?**

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
- This methods returns a true if it was succesful and false otherwise.
- The parameter `E` indicates the element to be added.
- It uses the `.put()` method of a `map` to add a new element.
- The second parameter in the put method, `PRESENT` is just a dummy value declared in the `HashSet.java` class.

## HashMap
We already saw how the HashSet works and that it is backed by a `HashMap` internally. So now let's see what is a HashMap and how does it work.

As its name says a HashMap is a `Map`, this means that it's a data structure that maps together a pair of two things: a `key` and a `value`. Each key is mapped to exactly one value, and we can use this key to retrieve the corresponding value.

Two important things to remember about HashMaps are:

1. Keys are unique.
2. Values can be repetead.

Let's look at an example. Imagine we want to create a phone directory where we will store a name of a person and their phone number. To do this we will store the person's name as a key and their phone as the correspondent value.

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

