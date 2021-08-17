# CodeWars-Challenges
Solutions for different katas with SWIFT !


## 6kyu


## 7kyu


## 8kyu
All [8kyu] Solutions </ br>
###[8kyu] Sum Mixed Array - Swift Solution
>Given an array of integers as strings and numbers, return the sum of the array values as if all were numbers.
>Return your answer as a number.
>https://www.codewars.com/kata/57eaeb9578748ff92a000009
```swift
// Solution1
func sumMix(_ arr: [Any]) -> Int {
    return arr.reduce(0) { $0 + (Int("\($1)") ?? 0) }
}

// Solution2
func sumMix(_ arr: [Any]) -> Int {
  return arr
          .compactMap { Int("\($0)") }
          .reduce(0,+)
}

// Solution3
unc sumMix(_ arr: [Any]) -> Int {

    var result = 0
    for item in arr {
        if item is String{
            result += Int(item as! String) ?? 0
        }
        else if item is Int{
            result += item as! Int
        }
    }
    return result
}
```


