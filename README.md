# CodeWars-Challenges
Solutions for different katas with SWIFT !


# [6kyu]
All [6kyu] Solutions <br />

## [6kyu] Array Katas

## [6kyu] String Katas

### [6kyu] CamelCase Method
>Write a simple camelCase function for strings. All words must have their first letter capitalized and all spaces removed.
>https://www.codewars.com/kata/587731fda577b3d1b0001196
```swift
// Solution1
func camelCase(_ str: String) -> String {
  return str.capitalized.replacingOccurrences(of: " ", with: "")
}

//Solution2
func camelCase(_ str: String) -> String {
  return str.capitalized.split(separator: " ").joined()
}

//Solution3
func camelCase(_ str: String) -> String {
    var test = [String]()
    let items = str.components(separatedBy: " ")
    for item in items {
        test.append(item.capitalized)
    }
    return test.joined()
}
```

# [7kyu]

## [7kyu] Array Katas

## [7kyu] String Katas

# [8kyu]
All [8kyu] Solutions <br />

## [8kyu] Array Katas
> List with all [8kyu] Array katas

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
