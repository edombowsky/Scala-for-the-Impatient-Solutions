1. Set up a map of prices for a number of gizmos that you covet. Then produce a second map with the same keys and the prices at a 10 percent discount.
 ```scala
    val coveted = ("iphone" -> 500.0, "mac book pro" -> 2000.0)
    val discountCoveted = for ((k,v) <- coveted ) yield (k, v*0.9)
```

2. Write a program that reads words from a file. Use a mutable map to count how often each word appears. To read the words, simply use a `java.util.Scanner`:
 ```scala
    val in = new java.util.Scanner(new java.io.File("myfile.txt"))
    while (in.hasNext()) process in.next()
```
 Or look at Chapter 9 for a Scalaesque way.

 At the end, print out all words and their counts.
 ```scala
    import scala.collection.mutable.HashMap
    import java.util.Scanner
    import java.io.File

    def count(word: String) = {
      if (words.contains(word)) words(word) += 1
      else words(word) = 1
    }

    val words = new HashMap[String, Int]

    val in = new Scanner(new File("words.txt")) 
    while (in.hasNext()) {
      count(in.next())
    }
    
    println(words)
```

3. Repeat the preceding exercise with an immutable map.
4. Repeat the preceding exercise with a sorted map, so that the words are printed in sorted order.
5. Repeat the preceding exercise with a `java.util.TreeMap` that you adapt to the Scala API.
6. Deﬁne a linked hash map that maps `"Monday"`` to `java.util.Calendar.MONDAY`, and similarly for the other weekdays. Demonstrate that the elements are visited in insertion order.
7. Print a table of all Java properties, like this:

 |   |   |
 |---|---|
 | java.runtime.name     | Java(TM) SE Runtime Environment
 | sun.boot.library.path | /home/apps/jdk1.6.0_21/jre/lib/i386
 | java.vm.version       | 17.0-b16
 | java.vm.vendor        | Sun Microsystems Inc.
 | java.vendor.url       | http://java.sun.com/
 | path.separator        | :
 | java.vm.name          | Java HotSpot(TM) Server VM
 
 You need to find the length of the longest key before you can print the table.
8. Write a function `minmax(values: Array[Int])`` that returns a pair containing the smallest and largest values in the array.
9. Write a function `lteqgt(values: Array[Int], v: Int)`` that returns a triple containing the counts of values less than v, equal to v, and greater than v.
10. What happens when you zip together two strings, such as `"Hello".zip("World")`? Come up with a plausible use case.
