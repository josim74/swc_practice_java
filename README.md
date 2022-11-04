# Set
- Java Set interface is a member of the Java Collections Framework.
- Unlike List, Set DOES NOT allow you to add duplicate elements.
- Set allows you to add at most one null element only.
- Unlike List and arrays, Set does NOT support indexes or positions of it’s elements.

### Java Set Class Diagram
Java Set interface extends Collection interface. Collection interface extends Iterable interface. Some of the frequently used Set implementation classes are -
- HashSet
- LinkedHashSet
- TreeSet
- CopyOnWriteArraySet
- ConcurrentSkipListSet

![image](https://user-images.githubusercontent.com/17778031/200018601-5d949513-3cb3-46ab-9669-5ba94cc533a6.png)

### Set methods
- int size(): to get the number of elements in the Set.
- boolean isEmpty(): to check if Set is empty or not.
- boolean contains(Object o): Returns true if this Set contains the specified element.
- Iterator iterator(): Returns an iterator over the elements in this set. The elements are returned in no particular order.
- Object[] toArray(): Returns an array containing all of the elements in this set. If this set makes any guarantees as to what order its elements are returned by its iterator, this method must return the elements in the same order.
- boolean add(E e): Adds the specified element to this set if it is not already present (optional operation).
- boolean remove(Object o): Removes the specified element from this set if it is present (optional operation).
- boolean removeAll(Collection c): Removes from this set all of its elements that are contained in the specified collection (optional operation).
- boolean retainAll(Collection c): Retains only the elements in this set that are contained in the specified collection (optional operation).
- void clear(): Removes all the elements from the set.
- Iterator iterator(): Returns an iterator over the elements in this set.

### Java Array to Set
Unlike List, We cannot convert a Java Set into an array directly as it’s NOT implemented using an Array.
```java
// Aproach-1 Array > List > Set
String[] vowels = {"a","e","i","o","u"};
Set<String> vowelsSet = new HashSet>(Arrays.asList(vowels));
System.out.println(vowelsSet);

//Aproach-2 copy Array elements to Set using Collection.addAll()
String[] vowels = {"a","e","i","o","u"};
Set<String> vowelsSet = new HashSet<>();
Collections.addAll(vowelsSet, vowels); 
System.out.println(vowelsSet);
```
### Set to Array
We can convert Set to Array using Set.toArray() method as shown below-
```java
Set<String< vowelsSet = new HashSet<>();
vowelsSet.add("a");
vowelsSet.add("e");
vowelsSet.add("i");
vowelsSet.add("o");
vowelsSet.add("u");
  
//convert Set to Array
String strArray[] = vowelsSet.toArray(new String[vowelsSet.size()]);
System.out.println(Arrays.toString(strArray));
```

### Set Sorting
As we know, Set (HashSet) does NOT support sorting elements directly. It stores and display it’s elements in random order. However, we have some approaches to sort it’s elements as shown below-
```java
Set<Integer> intsSet = new HashSet<>(); // Assuming intSet have some random integer value
Set<Integer> sortedSet = new TreeSet<>(intsSet);
System.out.println("Sorted Set: " + sortedSet);
```
### Set Iterator
Below is a simple example showing how to iterate over Java Set-
```java
Set<Integer> set = new HashSet<>();
for(int i=0; i<5; i++) 
	set.add(i);
  
Iterator iterator = set.iterator();
	
//simple iteration
while(iterator.hasNext()){
	int i = (int) iterator.next();
	System.out.print(i + ", ");
}
System.out.println("\n" + set);
	
//modification of set using iterator
iterator = set.iterator();
while(iterator.hasNext()){
	int x = (int) iterator.next();
	if(x%2 ==0) iterator.remove();
}
System.out.println(set);
		
//changing set structure while iterating
iterator = set.iterator();
while(iterator.hasNext()){
    //ConcurrentModificationException here
		int x = (int) iterator.next(); 
		if(x==1) set.add(10);
	}
```
### Set to Stream
Below is a simple example showing how to convert a Java Set to Stream and perform some operations as per our requirements-
```java
Set<String> vowelsSet = new HashSet<>();
// add example
vowelsSet.add("a");
vowelsSet.add("e");
vowelsSet.add("i");
vowelsSet.add("o");
vowelsSet.add("u");
		
//convert set to stream
vowelsSet.stream().forEach(System.out::println);
```
