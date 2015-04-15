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

    val words = new HashMap[String, Int]
    
    def count(word: String) = {
      if (words.contains(word)) words(word) += 1
      else words(word) = 1
    }

    val in = new Scanner(new File("words.txt")) 
    while (in.hasNext()) {
      count(in.next())
    }
    
    words foreach { case (word, count) => printf("%5d %s\n", count, word) }
```

3. Repeat the preceding exercise with an immutable map.
 ```scala
    import java.util.Scanner
    import java.io.File

    def countWordsImmutable() = {
      var words = Map[String, Int]()

      def process(word: String) {
        val count = words.getOrElse(word, 0)
        words = words + (word -> (count + 1))
      }
    
      val in = new Scanner(new File("words.txt"))
      while (in.hasNext()) {
        process(in.next())
      }
      words
    }
    
    val wordsImmutable = countWordsImmutable()
    wordsImmutable foreach { case (word, count) => printf("%5d %s\n", count, word) }
```

4. Repeat the preceding exercise with a sorted map, so that the words are printed in sorted order.
5. Repeat the preceding exercise with a `java.util.TreeMap` that you adapt to the Scala API.
6. Deﬁne a linked hash map that maps `"Monday"`` to `java.util.Calendar.MONDAY`, and similarly for the other weekdays. Demonstrate that the elements are visited in insertion order.
 ```scala
    import scala.collection.mutable.LinkedHashMap

    val daysOfTheWeek = LinkedHashMap(
      "Monday"    -> java.util.Calendar.MONDAY,
      "Tuesday"   -> java.util.Calendar.TUESDAY,
      "Wednesday" -> java.util.Calendar.WEDNESDAY,
      "Thursday"  -> java.util.Calendar.THURSDAY,
      "Friday"    -> java.util.Calendar.FRIDAY,
      "Saturday"  -> java.util.Calendar.SATURDAY,
      "Sunday"    -> java.util.Calendar.SUNDAY)

    println(daysOfTheWeek)
```

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
 ```scala
    import scala.collection.JavaConverters._

    val props = System.getProperties().asScala
    val longestKey = props.keysIterator.reduceLeft((x,y) => if (x.length > y.length) x else y)

    for ((k,v) <- props) {
      print(k + (" " * (longestKey.length - k.length)) + "| " + v + '\n')
    }
```
 or this:
 ```scala
    import scala.collection.JavaConverters._

    val props = System.getProperties().asScala
    val longestKey = props.keys.map(_.length).max

    for ((k,v) <- props) {
      print(k + (" " * (longestKey - k.length)) + "| " + v + '\n')
    }
```
 
 the `print` statement above could be replaced by:
 ```scala
   print(f"%-" + longestKey + "$k | $v%n")
```

8. Write a function `minmax(values: Array[Int])` that returns a pair containing the smallest and largest values in the array.
 ```scala
    def minmax(a: Array[Int]) = (a.min, a.max)

    println(minmax(Array(0,1,2,3,4,5,6,7,8,9)))
  ```
  
9. Write a function `lteqgt(values: Array[Int], v: Int)` that returns a triple containing the counts of values less than v, equal to v, and greater than v.
 ```scala
    def lteqgt(values: Array[Int], v: Int) = {
      (values.count(_ < v), values.count(_ == v), values.count(_ > v))
    }

    val testArray = Array(1, 3, 6, 8, 3, 6, -1, 2)

    println(lteqgt(testArray, 3))
```
10. What happens when you zip together two strings, such as `"Hello".zip("World")`? Come up with a plausible use case.
 - You are left with a vector of pairs of characters, with each character pair set to letters in the same position in the sequence (i.e. `Vector((H,W), (e,o), (l,r), (l,l), (o,d))`). 
 - A plausible use case could be matching upper case to lower case letters in the alphabet.

  ```scala
     val caseConverter = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".zip("abcdefghijklmnopqrstuvwxyz").toMap

     var lower = caseConverter('D')

     println(lower)
```
