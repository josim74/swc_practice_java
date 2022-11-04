<details><summary>Java Set</summary>
<p>
	
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
</p>
</details>


<details><summary>Java Map</summary>
<p>
	
# Map
- The Map interface is not a subtype of the Collection interface.
- HashMap is Hash table based implementation.
- Maps are perfect to use for key-value association mapping such as dictionaries.
- A Map cannot contain duplicate keys and each key can map to at most one value. Some implementations allow null key and null values like the HashMap and LinkedHashMap, but some do not like the TreeMap.
- The order of a map depends on the specific implementations. For example, TreeMap and LinkedHashMap have predictable orders, while HashMap does not.
- There are two interfaces for implementing Map in java. They are Map and SortedMap, and three classes: HashMap, TreeMap, and LinkedHashMap.

### Java Map Use Cases and Class Diagram
- A map of error codes and their descriptions.
- A map of zip codes and cities.
- A map of managers and employees. Each manager (key) is associated with a list of employees (value) he manages.
- A map of classes and students. Each class (key) is associated with a list of students (value).

![image](https://user-images.githubusercontent.com/17778031/200038388-41dfa5ba-c9cd-4590-a327-11562a56f485.png)

### Map methods (Similar to HashMap)
- V put(Object key, Object value)	It is used to insert an entry in the map.
- void putAll(Map map)	It is used to insert the specified map in the map.
- V putIfAbsent(K key, V value)	It inserts the specified value with the specified key in the map only if it is not already specified.
- V remove(Object key)	It is used to delete an entry for the specified key.
- boolean remove(Object key, Object value)	It removes the specified values with the associated specified keys from the map.
- Set keySet()	It returns the Set view containing all the keys.
- Set<Map.Entry<K,V>> entrySet()	It returns the Set view containing all the keys and values.
- void clear()	It is used to reset the map.
- V compute(K key, BiFunction<? super K,? super V,? extends V> remappingFunction)	It is used to compute a mapping for the specified key and its current mapped value (or null if there is no current mapping).
- V computeIfAbsent(K key, Function<? super K,? extends V> mappingFunction)	It is used to compute its value using the given mapping function, if the specified key is not already associated with a value (or is mapped to null), and enters it into this map unless null.
- V computeIfPresent(K key, BiFunction<? super K,? super V,? extends V> remappingFunction)	It is used to compute a new mapping given the key and its current mapped value if the value for the specified key is present and non-null.
- boolean containsValue(Object value)	This method returns true if some value equal to the value exists within the map, else return false.
- boolean containsKey(Object key)	This method returns true if some key equal to the key exists within the map, else return false.
- boolean equals(Object o)	It is used to compare the specified Object with the Map.
- void forEach(BiConsumer<? super K,? super V> action)	It performs the given action for each entry in the map until all entries have been processed or the action throws an exception.
- V get(Object key)	This method returns the object that contains the value associated with the key.
- V getOrDefault(Object key, V defaultValue)	It returns the value to which the specified key is mapped, or defaultValue if the map contains no mapping for the key.
- int hashCode()	It returns the hash code value for the Map
- boolean isEmpty()	This method returns true if the map is empty; returns false if it contains at least one key.
- V merge(K key, V value, BiFunction<? super V,? super V,? extends V> remappingFunction)	If the specified key is not already associated with a value or is associated with null, associates it with the given non-null value.
- V replace(K key, V value)	It replaces the specified value for a specified key.
- boolean replace(K key, V oldValue, V newValue)	It replaces the old value with the new value for a specified key.
- void replaceAll(BiFunction<? super K,? super V,? extends V> function)	It replaces each entry's value with the result of invoking the given function on that entry until all entries have been processed or the function throws an exception.
- Collection values()	It returns a collection view of the values contained in the map.
- int size()	This method returns the number of entries in the map.

### Methods of Map.Entry interface
- K getKey()	It is used to obtain a key.
- V getValue()	It is used to obtain value.
- int hashCode()	It is used to obtain hashCode.
- V setValue(V value)	It is used to replace the value corresponding to this entry with the specified value.
- boolean equals(Object o)	It is used to compare the specified object with the other existing objects.
- static <K extends Comparable<? super K>,V> Comparator<Map.Entry<K,V>> comparingByKey()	It returns a comparator that compare the objects in natural order on key.
- static <K,V> Comparator<Map.Entry<K,V>> comparingByKey(Comparator<? super K> cmp)	It returns a comparator that compare the objects by key using the given Comparator.
- static <K,V extends Comparable<? super V>> Comparator<Map.Entry<K,V>> comparingByValue()	It returns a comparator that compare the objects in natural order on value.
- static <K,V> Comparator<Map.Entry<K,V>> comparingByValue(Comparator<? super V> cmp)	It returns a comparator that compare the objects by value using the given Comparator.

### Create Map then insert value and retrieve
Shows old style and new style with same Map-
```java
Map map = new HashMap();
map.put(1,"Amit");  
map.put(5,"Rahul");  
map.put(2,"Jai");  
map.put(6,"Amit");  
//Traversing Map old style
Set set = map.entrySet();//Converting to Set so that we can traverse  
Iterator itr=set.iterator();  
while(itr.hasNext()){  
    //Converting to Map.Entry so that we can get key and value separately  
    Map.Entry entry = (Map.Entry)itr.next();  
    System.out.println(entry.getKey()+" "+entry.getValue());  
}
//Traversing Map new style
for(Map.Entry m:map.entrySet()){  
   System.out.println(m.getKey()+" "+m.getValue());  
}

//Compare by key
map.entrySet()  //Returns a Set view of the mappings contained in this map        
.stream()  //Returns a sequential Stream with this collection as its source  
.sorted(Map.Entry.comparingByKey())  //Sorted according to the provided Comparator  
.forEach(System.out::println);  //Performs an action for each element of this stream  

//Compare by value
map.entrySet()  //Returns a Set view of the mappings contained in this map    
.stream()  //Returns a sequential Stream with this collection as its source  
.sorted(Map.Entry.comparingByValue(Comparator.reverseOrder()))  //Sorted according to the provided Comparator  
.forEach(System.out::println);  //Performs an action for each element of this stream   
```

### Tree Map
- Contains values based on the key. It implements the NavigableMap interface and extends AbstractMap class.
- Contains only unique elements.
- Cannot have a null key but can have multiple null values.
- TreeMap is non synchronized.
- Maintains ascending order.

### Constructor
- TreeMap()	It is used to construct an empty tree map that will be sorted using the natural order of its key.
- TreeMap(Comparator<? super K> comparator)	It is used to construct an empty tree-based map that will be sorted using the comparator comp.
- TreeMap(Map<? extends K,? extends V> m)	It is used to initialize a treemap with the entries from m, which will be sorted using the natural order of the keys.
- TreeMap(SortedMap<K,? extends V> m)	It is used to initialize a treemap with the entries from the SortedMap sm, which will be sorted in the same order as sm.

### Methods of Java TreeMap class
- Map.Entry<K,V> ceilingEntry(K key)	It returns the key-value pair having the least key, greater than or equal to the specified key, or null if there is no such key.
- K ceilingKey(K key)	It returns the least key, greater than the specified key or null if there is no such key.
- void clear()	It removes all the key-value pairs from a map.
- Object clone()	It returns a shallow copy of TreeMap instance.
- Comparator<? super K> comparator()	It returns the comparator that arranges the key in order, or null if the map uses the natural ordering.
- NavigableSet<K> descendingKeySet()	It returns a reverse order NavigableSet view of the keys contained in the map.
- NavigableMap<K,V> descendingMap()	It returns the specified key-value pairs in descending order.
- Map.Entry firstEntry()	It returns the key-value pair having the least key.
- Map.Entry<K,V> floorEntry(K key)	It returns the greatest key, less than or equal to the specified key, or null if there is no such key.
- void forEach(BiConsumer<? super K,? super V> action)	It performs the given action for each entry in the map until all entries have been processed or the action throws an exception.
- SortedMap<K,V> headMap(K toKey)	It returns the key-value pairs whose keys are strictly less than toKey.
- NavigableMap<K,V> headMap(K toKey, boolean inclusive)	It returns the key-value pairs whose keys are less than (or equal to if inclusive is true) toKey.
- Map.Entry<K,V> higherEntry(K key)	It returns the least key strictly greater than the given key, or null if there is no such key.
- K higherKey(K key)	It is used to return true if this map contains a mapping for the specified key.
- Set keySet()	It returns the collection of keys exist in the map.
- Map.Entry<K,V> lastEntry()	It returns the key-value pair having the greatest key, or null if there is no such key.
- Map.Entry<K,V> lowerEntry(K key)	It returns a key-value mapping associated with the greatest key strictly less than the given key, or null if there is no such key.
- K lowerKey(K key)	It returns the greatest key strictly less than the given key, or null if there is no such key.
- NavigableSet<K> navigableKeySet()	It returns a NavigableSet view of the keys contained in this map.
- Map.Entry<K,V> pollFirstEntry()	It removes and returns a key-value mapping associated with the least key in this map, or null if the map is empty.
- Map.Entry<K,V> pollLastEntry()	It removes and returns a key-value mapping associated with the greatest key in this map, or null if the map is empty.
- V put(K key, V value)	It inserts the specified value with the specified key in the map.
- void putAll(Map<? extends K,? extends V> map)	It is used to copy all the key-value pair from one map to another map.
- V replace(K key, V value)	It replaces the specified value for a specified key.
- boolean replace(K key, V oldValue, V newValue)	It replaces the old value with the new value for a specified key.
- void replaceAll(BiFunction<? super K,? super V,? extends V> function)	It replaces each entry's value with the result of invoking the given function on that entry until all entries have been processed or the function throws an exception.
- NavigableMap<K,V> subMap(K fromKey, boolean fromInclusive, K toKey, boolean toInclusive)	It returns key-value pairs whose keys range from fromKey to toKey.
- SortedMap<K,V> subMap(K fromKey, K toKey)	It returns key-value pairs whose keys range from fromKey, inclusive, to toKey, exclusive.
- SortedMap<K,V> tailMap(K fromKey)	It returns key-value pairs whose keys are greater than or equal to fromKey.
- NavigableMap<K,V> tailMap(K fromKey, boolean inclusive)	It returns key-value pairs whose keys are greater than (or equal to, if inclusive is true) fromKey.
- boolean containsKey(Object key)	It returns true if the map contains a mapping for the specified key.
- boolean containsValue(Object value)	It returns true if the map maps one or more keys to the specified value.
- K firstKey()	It is used to return the first (lowest) key currently in this sorted map.
- V get(Object key)	It is used to return the value to which the map maps the specified key.
- K lastKey()	It is used to return the last (highest) key currently in the sorted map.
- V remove(Object key)	It removes the key-value pair of the specified key from the map.
- Set<Map.Entry<K,V>> entrySet()	It returns a set view of the mappings contained in the map.
- int size()	It returns the number of key-value pairs exists in the hashtable.
- Collection values()	It returns a collection view of the values contained in the map.

### Tree Map Practice
```java
TreeMap<Integer,String> map=new TreeMap<Integer,String>();    
map.put(100,"Amit");    
map.put(102,"Ravi");    
map.put(101,"Vijay");    
map.put(103,"Rahul");
//remove item
map.remove(102);
//Travarse TreeMap
for(Map.Entry m:map.entrySet()){    
    System.out.println(m.getKey()+" "+m.getValue());    
}
```
### Navigable Map
```java
NavigableMap<Integer,String> map=new TreeMap<Integer,String>();    
map.put(100,"Amit");    
map.put(102,"Ravi");    
map.put(101,"Vijay");    
map.put(103,"Rahul"); 
   
System.out.println("descendingMap: "+map.descendingMap());  //Maintains descending order  
System.out.println("headMap: "+map.headMap(102,true));  //Returns key-value pairs whose keys are less than or equal to the specified key.  
System.out.println("tailMap: "+map.tailMap(102,true));  //Returns key-value pairs whose keys are greater than or equal to the specified key.  
System.out.println("subMap: "+map.subMap(100, false, 102, true));   //Returns key-value pairs exists in between the specified key.  
```
### Sorted Map
```java
SortedMap<Integer,String> map=new TreeMap<Integer,String>();    
map.put(100,"Amit");    
map.put(102,"Ravi");    
map.put(101,"Vijay");    
map.put(103,"Rahul");

System.out.println("headMap: "+map.headMap(102));  //Returns key-value pairs whose keys are less than the specified key.       
System.out.println("tailMap: "+map.tailMap(102));  //Returns key-value pairs whose keys are greater than or equal to the specified key.  
System.out.println("subMap: "+map.subMap(100, 102));    //Returns key-value pairs exists in between the specified key.   
```
</p>
</details>
