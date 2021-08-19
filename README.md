# CodeWars-Challenges
Solutions for different katas with SWIFT !


# [6kyu]
All [6kyu] Solutions <br />

## [6kyu] Array Katas

## [6kyu] String Katas

### [6kyu] CamelCase Method - Swift Solution
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
    var caCase = [String]()
    let items = str.components(separatedBy: " ")
    for item in items {
        caCase.append(item.capitalized)
    }
    return caCase.joined()
}
```

# [7kyu]

## [7kyu] Array Katas

### [7kyu] Odder Than the Rest - Swift Solution
>Create a function oddOne that takes an [Int] as input and outputs the index at which the sole odd number is located.
>This method should work with arrays with negative numbers. If there are no odd numbers in the array, then the method should output nil.
>Examples:
```swift
oddOne([2,4,6,7,10]) // => 3
oddOne([2,16,98,10,13,78]) // => 4
oddOne([4,-8,98,-12,-7,90,100]) // => 4
oddOne([2,4,6,8]) // => nil

```
>https://www.codewars.com/kata/587731fda577b3d1b0001196
```swift
// Solution1
func oddOne(_ arr: [Int]) -> Int? {
  return arr.firstIndex { $0 % 2 != 0 }
}

// Solution2
func oddOne(_ arr: [Int]) -> Int? {
    for ar in arr {
        if ar % 2 == 0 {
            continue
        }
        return arr.firstIndex(of: ar)
    }
    return nil
}
```


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
