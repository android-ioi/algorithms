# Extra Long Factorials
* https://www.hackerrank.com/challenges/extra-long-factorials/problem

## Solution
### fdelpini
#### Use BigInteger
```kotlin
// Complete the extraLongFactorials function below.
fun extraLongFactorials(n: Int): Unit {
    var result = n.toBigInteger()
    for(i in n-1 downTo 1) {
        result = result * (i.toBigInteger())
    }
    println(result)
}
```