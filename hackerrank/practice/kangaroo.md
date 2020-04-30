# Kangaroo
* https://www.hackerrank.com/challenges/kangaroo/problem

## Solution
### fdelpini
```kotlin
// Complete the kangaroo function below.
fun kangaroo(x1: Int, v1: Int, x2: Int, v2: Int): String {
    // 기본 조건이 x1 < x2인데, 뒤의 캥거루가 점프를 더 많거나 같게 할 경우, 
    // 앞의 캥거루가 절대 따라잡을 수 없으므로 NO 리턴
    if(v1 <= v2) return "NO"
    for(i in 1 .. 10000) {  // 최초 1회 점프 이후 부터 체크, 최악의 경우 10000까지 반복
        val posX1 = v1 * i + x1
        val posX2 = v2 * i + x2
        if(posX1 == posX2) return "YES"
        else if(posX1 > posX2) return "NO"   // 앞의 캥거루가 역전할 경우, NO
    }
    return "NO"
}
```
