# New Year Chaos
* https://www.hackerrank.com/challenges/new-year-chaos/problem

## Solution
### fdelpini
#### First Solution
- 버블 정렬을 기본으로 하고 있음. 알고리즘 복잡도로 인해 Time Limit이 발생하는 상황
```kotlin
// Complete the minimumBribes function below.
fun minimumBribes(q: Array<Int>): Unit {
    var count : Int = 0
    val persons = mutableMapOf<Int, Int>()
    for(i in 0 until q.size) {
        for(j in 0 until q.size - i - 1) {
            if(q[j] > q[j + 1]) {
                count++
                if(persons.containsKey(q[j])) {
                    var swapCount = persons.get(q[j])!! + 1
                    if(swapCount > 2) {
                        println("Too chaotic")
                        return
                    }
                    persons.put(q[j], swapCount)
                }
                else {
                    persons.put(q[j], 1)
                }
                // swap
                var temp = q[j]
                q[j] = q[j + 1]
                q[j + 1] = temp
            }
        }
    }
    println(count)
}
```

### skygrapher
```swift
/// 해결전략.
/// n 부터 1 순서로 진행(큰 수부터 작은수 순서로)
/// 해당 숫자가 제자리에 없다면, 2번 이내에서 해당 숫자를 뒤쪽의 숫자와 자리를 교체한다.
/// 2번까지 교체했는데도 제자리에 없다면 Too chaotic 에러.
/// O(4n)

/// 배열에서 해당 넘버가 제 자리에 위치해 있는가?
func isProperPosition(q: [Int], number: Int) -> Bool {
    guard number >= 1 && number <= q.count else { fatalError() }
    return q[(number - 1)] == number
}

let maxMove = 2 // 최대 2번까지만 움직일 수 있음.(최대 뇌물 주는 회수랑 같음.)

func indexOf(number: Int, q: [Int]) -> Array<Int>.Index? {
    let start = max(0, number - 3)
    let end = number - 1
    for index in start...end {
        if q[index] == number {
            return index
        }
    }
    return nil
}

/// 입력으로 받은 배열을 순차적인 배열로 변경하면서 swap한 회수를 리턴한다. swap제한을 넘어가면 nil 리턴.(too chatic 상황)
func recoverChaos(q: [Int]) -> Int? {
    var recovered = q
    var stepCount = 0
    for number in (1...q.count).reversed() {
        for _ in 0..<maxMove {
            if !isProperPosition(q: recovered, number: number) {
                stepCount += 1
                guard let index = indexOf(number: number, q: recovered) else { return nil }
                recovered.swapAt(index, index+1)
            }
        }
        if !isProperPosition(q: recovered, number: number) {
            return nil
        }
    }
    return stepCount
}

```
