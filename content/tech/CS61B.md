---
title: "CS61B"
date: 2024-02-21T20:00:26-08:00
draft: false
tags: ["Java", "Data Structures", "Algorithms", "CS61B"]
---

## Notes

### Language Constructs (Java vs. Python)

#### Types 
**Java** is a *statically typed* language, which means that every variable has a type that is known at **compile time**, meaning you must specify it in your code. 
In contrast, **Python** is a *dynamically typed* language, which means that the type of variables are generally only known at **runtime**, meaning you do not need to specify them in your code.

In Java, there are two kinds of types: primitive types and reference types. 
**Primitive types** are lowercase, and we named these: `boolean`, `int`, `char`, `double`. Pretty much every other type is a **reference type**, such as `String`. If a type starts with a capital letter, it is likely a reference type. 

Each primitive has a corresponding reference type (`Boolean`, `Integer`, `Character`, `Double`). **If you are using "generics" to declare a data structure, you must use the reference type.** You can (usually) seamlessly convert between a primitive type and its reference type.

![alt](/images/primitive_types.png)

#### null
Java also has `null`, which is the approximate equivalent of `None` in Python. Any reference type can be assigned a value of `null`. If we try to access an instance member or call an instance method from a value of `null`, we will see an error called a `NullPointerException`.

#### Arrays (fixed-size)
Java arrays are a lot like Python lists. However, Java arrays are fixed-size, so we can't add or remove elements (that is, no `append`, `remove`, etc.).

**python:**
```python
zeroedLst = [0, 0, 0]
lst = [4, 7, 10]
lst[0] = 5
print(lst[0])
print(lst)
print(len(lst))
```
**java:**
```java
int[] zeroedArray = new int[3];
int[] array = {4, 7, 10};
array[0] = 5;
System.out.println(array[0]);
System.out.println(Arrays.toString(array));
System.out.println(array.length);
```

- In new `int[3]`, the int is the type in the array; and `3` is the length. With this syntax, all elements take on their "default value". For `int`, this is 0.
- Arrays do not print nicely, for reasons beyond the scope of HW 0. To print an array, you can call `Arrays.toString(array)`.
- Arrays do not have a length method. It is an instance variable, so it does not have parentheses.
- Java does **not** support negative indexing or slicing.

#### Foreach Loop / Enhanced For Loop
**python:**
```python
lst = [1, 2, 3]
for i in lst:
    print(i)
```
**java:**
```java
int[] array = {1, 2, 3};
for (int i : array) {
    System.out.println(i);
}
```

- Notice the type declaration of the iterating variable, as well as the usage of `:` instead of `in`.
- We can also use this syntax on certain other types, such as `Lists` and `Set`s.

#### Lists (resizable)
**python:**
```python
lst = []
lst.append("zero")
lst.append("one")
lst[0] = "zed"
print(l[0])
print(len(l))
if "one" in lst:
    print("one in lst")

for elem in lst:
    print(elem)
```
**java:**
```java
List<String> lst = new ArrayList<>();
lst.add("zero");
lst.add("one");
lst.set(0, "zed");
System.out.println(lst.get(0));
System.out.println(lst.size());
if (lst.contains("one")) {
    System.out.println("one in lst");
}
for (String elem : lst) {
    System.out.println(elem);
}
```

- Java has the `List` interface. We largely use the `ArrayList` implementation.
The `List` interface is parameterized by the type it holds, using the angle brackets `<` and `>`.
`List`s, again, do not support slicing or negative indexing.

#### Sets
**python:**
```python
s = set()
s.add(1)
s.add(1)
s.add(2)
s.remove(2)
print(len(s))
if 1 in s:
    print("1 in s")

for elem in s:
    print(elem)
```
**java:**
```java
Set<Integer> set = new HashSet<>();
set.add(1);
set.add(1);
set.add(2);
set.remove(2);
System.out.println(set.size());
if (set.contains(1)) {
    System.out.println("1 in set");
}
for (int elem : set) {
    System.out.println(elem);
}
```

- Java has the `Set` interface. There are two main implementations: `TreeSet`, and `HashSet`. `TreeSet` keeps its elements in "sorted" order, and is fast. In contrast, `HashSet` does not have a defined "order", but is (usually) really fast.   
     -  We will formalize these notions of "fast" later on in the course when we learn about asymptotic analysis. 
- A `Set` cannot contain duplicate items. If we try to add an item already in the set, nothing happens.

#### Dictionaries / Maps
**python:**
```python
d = {}
d["hello"] = "hi"
d["hello"] = "goodbye"
print(d["hello"])
print(len(d))
if "hello" in d:
    print("\"hello\" in d")

for key in d.keys():
    print(key)
```
**java:**
```java
Map<String, String> map = new HashMap<>();
map.put("hello", "hi");
map.put("hello", "goodbye");
System.out.println(map.get("hello"));
System.out.println(map.size());
if (map.containsKey("hello")) {
    System.out.println("\"hello\" in map");
}
for (String key : map.keySet()) {
    System.out.println(key);
}
```

- Java has the `Map` interface. There are two main implementations: `TreeMap`, and `HashMap`. Similarly to sets, `TreeMap` keeps its keys sorted and is fast; `HashMap` has no defined order and is (usually) really fast.
- A `Map` cannot contain duplicate keys. If we try to add a key already in the map, the value is overwritten.
- In the angle brackets, we have the "key type" first, followed by the "value type".
- `Map`s cannot directly be used with the `:` for loop. Typically, we call `keySet` to iterate over a set of the keys, and use those to retrieve the values. One may also iterate over the `entrySet` to get both the keys and values.

#### Classes
**python:**
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def distanceTo(self, other):
        return math.sqrt(
            (self.x - other.x) ** 2 +
            (self.y - other.y) ** 2
        )

    def translate(self, dx, dy):
        self.x += dx
        self.y += dy
```
**java:**
```java
public class Point {
    public int x;
    public int y;
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
    public Point() {
        this(0, 0);
    }
    public double distanceTo(Point other) {
        return Math.sqrt(
            Math.pow(this.x - other.x, 2) +
            Math.pow(this.y - other.y, 2)
        )
    }
    public void translate(int dx, int dy) {
        this.x += dx;
        this.y += dy;
    }
}
```

We can use these classes as follows:
**python:**
```python
p1 = Point(5, 9)
p2 = Point(-3, 3)
print(f"Point 1: ({p1.x}, {p1.y})")
print("Distance:", p1.distanceTo(p2))
p1.translate(2, 2)
print(f"Point 1: ({p1.x}, {p1.y})")
```
**java:**
```java
Point p1 = new Point(5, 9);
Point p2 = new Point(-3, 3);
System.out.println("Point 1: ( " + p1.x
    + ", " + p1.y + ")");
System.out.println("Distance: "
    + p1.distanceTo(p2));
p1.translate(2, 2);
System.out.println("Point 1: ( " + p1.x
    + ", " + p1.y + ")");
```

#### Main
Java programs may also have a special method called `main`. When you execute a program, the `main` method is called. The `main` method runs whatever code is inside, which may call other methods defined within the program.

We define the `main` method with the signature `public static void main(String[] args)`. For now, you can treat `main` as a "play button" for the code you have written.

To run the code in the previous example, we may create a `main` method in the `Point` class like this:
**python:**
```python
class Point:

    # other methods...
    # end of Point class

if __name__ == '__main__':
    p1 = Point(5, 9)
    p2 = Point(-3, 3)
    print(f"Point 1: ({p1.x}, {p1.y})")
    print("Distance:", p1.distanceTo(p2))
    p1.translate(2, 2)
    print(f"Point 1: ({p1.x}, {p1.y})")

```
**java:**
```java
public class Point {

    // other methods...

    public static void main(String[] args) {
        Point p1 = new Point(5, 9);
        Point p2 = new Point(-3, 3);
        System.out.println("Point 1: ( " + p1.x
            + ", " + p1.y + ")");
        System.out.println("Distance: "
            + p1.distanceTo(p2));
        p1.translate(2, 2);
        System.out.println("Point 1: ( " + p1.x
            + ", " + p1.y + ")");
    }

    // end of Point class
}
```

Notice that in Java, the `main` method is defined within a class.

If you are coding in IntelliJ, you can actually "play" the `main` method! IntelliJ will display a green play button to the left of the `main` method's signature. Click it to run the code inside.

### Programs
Let's look at some Java programs that use data structures and classes. Here are some simple ones that you might find yourself referring to if you forget how to do something.

#### Index of Minimum of a List of Numbers
**python:**
```python
def min_index(numbers):
    # Assume len(numbers) >= 1
    m = numbers[0]
    idx = 0
    for i in range(len(numbers)):
        if numbers[i] < m:
            m = numbers[i]
            idx = i
    return idx
```
**java:**
```java
public static int minIndex(int[] numbers) {
    // Assume numbers.length >= 1
    int m = numbers[0];
    int idx = 0;
    for (int i = 0; i < numbers.length; i++) {
        if (numbers[i] < m) {
            m = numbers[i];
            idx = i;
        }
    }
    return idx;
}
```
### Exceptions
Lastly, let's look at how we can throw exceptions in Java compared to Python with previous example.
**python:**
```python
def minIndex(numbers):
    if len(numbers) == 0:
        raise Exception("There are no elements in the list!")
    m = numbers[0]
    idx = 0

    ...

    return m
```
**java:**
```java
public static int minIndex(int[] numbers) {
    if (numbers.length == 0) {
        throw new Exception("There are no elements in the array!");
    }
    int m = numbers[0];
    int idx = 0;

    ...

    return m;
}
```