# Day of the Programmer
* https://www.hackerrank.com/challenges/day-of-the-programmer/problem

## Solution
### fdelpini
```kotlin
// Complete the dayOfProgrammer function below.
fun dayOfProgrammer(year: Int): String {
    val days = arrayOf(31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31)  // 1 ~ 12월 기본
    if(year == 1918) { // 율리우스력에서 그레고리언력으로 전환되는 해
        days[1] = 28 - 13 // 2월이 14일부터 시작되기 때문에, 28일에서 13일을 제외
    }
    else if(year > 1918) {  // 그레고리언력
        val isLeapYear = (year % 400 == 0) || ((year % 4 == 0) && (year % 100 != 0))
        days[1] = if(isLeapYear) 29 else 28
    }
    else { // year < 1918, 율리우스력
        days[1] = if(year % 4 == 0) 29 else 28
    }
    // 256번째 날짜 계산
    var sumOfDays = 0
    for(month in 0 until days.size) {
        sumOfDays += days[month]
        if(sumOfDays > 256) {
            // 256을 넘어갔으므로, 256 + 해당 월의 날짜 수 - 합산
            //val dd = 256 + days[month] - sumOfDays
            return "${256 + days[month] - sumOfDays}.0${month + 1}.${year}"
        }
    }
    return ""
}
```

### member2 
```swift
```