1. The _signum_ of a number is 1 if the number is positive, -1 if it is negative and 0 if it is zero. Write a function that computes this value.
 ```scala
 def signnum(x: Int) = {
      if (x < 0) -1 
      else if (x > 0) 1 
      else 0
 }
 ```
2. What is the value of an empty block expression {}? What is its type?
  
  Value is blank and type is `Unit`

3. Come up with one situation where the assignment `x = y = 1` is valid in Scala.  \(Hint: Pick a sutable type of x\)
 ```scala
 var y: Int = 0                            //> y  : Int = 0
 val x: Unit = y = 1                       //> x  : Unit = ()
 ```

 Therefore, x should be of type Unit.

4. Write a Scala equivalent for the Java loop
 ```java
  for (int i = 10; i >= 0; i--) System.out.println(i);
  ```

 Answer:
 ```scala
 for (i <- 10 to 0 by -1) {
    println(i)
}
 ```

5. Wite a procedure `countdown(n: Int)` that prints the numbers from n to 0.
 ``` scala
 def countdown(n: Int) {
    for (i <- n to 0 by -1) {
        println(i)
    }
 }
 ```

6. Write a `for` loop for computing the product of the Unicode codes oc all letters in a string.  For example, the product of the characters in `"Hello` is `825152896`
 ```scala
 var prod = 1L
 for (c <- "Hello") prod *= c
 prod
 ```

7. Solve the preceding exercise without a loop (Hint: Look at the `StringOps` Scaladoc)
 ```scala
 "Hello".foldLeft(1L)((a, b) => a * b) 
 ```

8. Write a  function `product(s: String)` that computes the product as described in the preceding exercises.
 ```scala
 def product(s: String) = {
    var ans: Long = 1L;
    for (c <- s) {
        ans *= c.toLong
    }
    ans
 }
 ```

9. Make the function of the preceding exercise a recursive function.
 ```scala
 def product(s: String): Long = {
    if (s.length == 0) 1
    else s(0) * product(s drop 1)
 }
 ```

10. Write a function that computes x<sup>n</sup> , where `n` is an integer.  Use the following recursice definition:

 x<sup>n</sup> = y<sup>2</sup> if `n` is even and positive, where y = x<sup>n/2</sup>

 x<sup>n</sup> =  x * x<sup>n-1</sup> if `n` is odd and positive

 x<sup>0</sup> = 1

 x<sup>n</sup> = 1 / x<sup>-n</sup> if `n` is negative

 Don't use a return statement
 ```scala
 def pow(x: Int, n: Int): BigInt = {
    if (n > 0 && n % 2 == 0) pow(x, n/2) * pow(x, n/2)
    else if (n > 0) x * pow(x, n - 1)
    else if (n == 0) 1
    else 1 / pow(x, -n)
 }
 ```
