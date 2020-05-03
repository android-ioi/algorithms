# Save the Prisoner!
* https://www.hackerrank.com/challenges/save-the-prisoner/problem

## Solution
### fdelpini
```kotlin
// Complete the saveThePrisoner function below.
fun saveThePrisoner(n: Int, m: Int, s: Int): Int {
    if(n == 1) return 1 // 죄수의 수가 1명일 경우
    // x회 반복 후 남은 사탕의 수 계산
    // m % n == 0 인 경우는 n, 그 외에는 m % n
    val remainSweets = (if(m % n == 0) n else m % n)
    // 남은 사탕수로 카운팅
    var result = remainSweets + (s - 1)
    if(result > n) {    // 결괏값이 죄수의 수보다 클 경우, 나머지 계산
        result = result % n
    }
    return result
}
```

### member2 
```swift
```