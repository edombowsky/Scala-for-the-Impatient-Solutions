1. Write a code snippet that sets `a` to an array of `n` random integers between `0` (inclusive) and `n` (exclusive).
 ```scala
    import util.Random

    def rndArray(n: Int) = {
      val a = new Array[Int](n)

      for (i <- 0  until a.size) a(i) = Random.nextInt(n)
      a
    }
```

2. Write a loop that swaps adjacent elements of an array of integers.  For example, `Array(1,2,3,4,5)` becomes `Array(2,1,4,3,5)`
 ```scala
    for (i <- 0 until(a.size, 2) if (i < a.length-1)) {
      val tmp = a(i)
      a(i) = a(i+1)
      a(i+1) = tmp
    }
```

3. Repeat the preceding assignments, but produces a new array with the swapped values.  Use `for/yield`.
 ```scala
    for (i <- 0 until a.length) yield 
      if (i % 2 != 0) a(i - 1) 
      else {
        if (i == a.length - 1) a(i) else a( i + 1)
      }
```

 and just looking ahead a bit here are are a few more more Scala like versions:
 ```scala
    array.grouped(2).toArray.flatMap(_.reverse)
  
    array match {
      case Array(x, y, z @ _*) => Array(y, x) ++ z
      case _ => array
    }

    array.grouped(2).flatMap{ 
      case Array(x,y) => Array(y,x)
      case Array(x) => Array(x)
    }.toArray
```
4. Given an array of integers, produce a new array that contains all positive values of the original array, in their original order, followed by all values that are zero or negative, in their original order.
5. How do you compute the average of an `Array[Double]`
6. How do you rearrange the elements of an `Array[Int]` so that they appear in reverse sorted order?  How do you do the same with an `ArrayBuffer[Int]`?
7. Write a code snippet that produces all values from an array with duplicates removed.  (Hint: Look at Scaladoc)
8. Rewrite the example at the end of Section 4 using the `drop` method for dropping the index of the first match.  Look the method up in Scaladoc.
9. Make a collection of all time zones returned by `java.util.TimeZone.getAvailableIds` that are in America.  Strip off the `"America/"` prefix and sort the result.
10. Import `java.awt.datatransfer._` and make an object of type `SystemFlavorMap` with the call
 ```java
 val flavors = SystemFlavorMap.getDefaultFlavorMap().asInstanceOf[SystemFlavorMap]`
 ```
 
 Then call the `getNativesForFlavor` method with parameter `DataFlavor.imageFlavor` and get the return value as a Scall Buffer.  (Why this obscure class?  It;s hard to find uses of `java.util.List` in the standard Java library.)
