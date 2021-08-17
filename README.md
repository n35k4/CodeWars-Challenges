# CodeWars-Challenges
Solutions for different katas with SWIFT !


## 6kyu


## 7kyu


# 8kyu
All [8kyu] Solutions <br />

## Array Katas
> Only Array Katas

### [8kyu] Sum Mixed Array - Swift Solution
>Given an array of integers as strings and numbers, return the sum of the array values as if all were numbers. <br />
>Return your answer as a number. <br />
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

### [8kyu] Get the mean of an array - Swift Solution
>It's the academic year's end, fateful moment of your school report. The averages must be calculated. All the students come to you and entreat you to calculate their average for them. Easy ! You just need to write a script. <br />
>Return the average of the given array rounded down to its nearest integer. <br />
>The array will never be empty. <br />
>https://www.codewars.com/kata/563e320cee5dddcf77000158/swift
```swift
// Solution1
func getAverage(_ marks: [Int]) -> Int { 
    return marks.reduce(0, +) / marks.count
}

// Solution2
func getAverage(_ marks: [Int]) -> Int {
    marks.reduce(0) {($0 + $1)} / marks.count
}
```
## Strings
> Only String Katas
