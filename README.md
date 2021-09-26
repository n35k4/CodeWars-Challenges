# CodeWars-Challenges
Solutions for different katas with SWIFT !

# [5kyu]
All [5kyu] Solutions <br />

## [5kyu] Array Katas

## [5kyu] String Katas

## [5kyu] Integer Katas

### [5kyu] Integers: Recreation One - Swift Solution
> Find all integers between m and n (m and n integers with 1 <= m <= n) such that the sum of their squared divisors is itself a square. <br />
> We will return an array of subarrays or of tuples (in C an array of Pair) or a string. The subarrays (or tuples or Pairs) will have two elements: first the number the squared divisors of which is a square and then the sum of the squared divisors. <br />
> https://www.codewars.com/kata/55aa075506463dac6600010d/swift
```swift
// Solution 1 
func listSquared(_ m: Int, _ n: Int) -> [(Int, Int)] {
  return (m...n).flatMap { (val) -> (Int, Int)? in
    let divisors = (1...(Int(sqrt(Double(val)))))
      .flatMap({val % $0 == 0 ? [$0, val / $0] : []})
    let sum = Array(Set(divisors)).reduce(0, {$0 + ($1 * $1)})
    if sqrt(Double(sum)).truncatingRemainder(dividingBy: 1) == 0 {
      return (val, sum)
    }
    return nil
  }
}


// Solution 2
func getDivisors(_ x:Int) -> [Int] {
    let sqr = sqrt(Double(x))
    var list = [Int]()
    for i in 1..<Int(sqr)+1 {
        if x % i == 0 {
            list.append(i)
            if i != (x/i) {
                list.append((x/i))
            }
        }
    }
    return list
}

func numberIsSquare(_ x: Int) -> Bool {
    return Int(sqrt(Double(x))) * Int(sqrt(Double(x))) == x
}

func listSquared(_ m: Int, _ n: Int) -> [(Int, Int)] {
    var list = [(Int, Int)]()
    for value in m ... n{
        let sumOfDivisors = getDivisors(value).map{$0 * $0}.reduce(0, +)
        if numberIsSquare(sumOfDivisors){
            list.append((value, sumOfDivisors))
        }
    }
    return list
}

// Solution 3
func listSquared(_ m: Int, _ n: Int) -> [(Int, Int)] {
    var returnedArray: [(Int, Int)] = []
    for value in m...n {
        
        var divisors: [Int] = []
        for divisor in 1...value {
            if value % divisor == 0 {
                divisors.append(divisor)
            }
        }
        
        let sumOfSquaresOfDivisors = divisors.map { $0 * $0 }.reduce(0, +)
        if Double(sumOfSquaresOfDivisors).squareRoot().truncatingRemainder(dividingBy: 1.0) == 0 {
            returnedArray.append((value, sumOfSquaresOfDivisors))
        }
    }
    
    return returnedArray
}
```

<br />

# [6kyu]
All [6kyu] Solutions <br />

## [6kyu] Array Katas

## [6kyu] String Katas

### [6kyu] Write Number in Expanded Form - Swift Solution
> You will be given a number and you will need to return it as a string in Expanded Form. <br />
> https://www.codewars.com/kata/5842df8ccbd22792a4000245/swift <br />
```swift
// Solution 1
func expandedForm(_ num: Int) -> String {
  let array = String(num).flatMap{ Int(String($0)) }
    var count = array.count
    let result = array.map({ (number) -> String in
        count -= 1
        return String(number * Int(pow(10.0,Double(count))))
    }).filter({ $0 != "0" }).joined(separator: " + ")
    return result
}

// Solution 2 *Best practice*
func expandedForm(_ num: Int) -> String {
    let digits = String(num).characters
    let maxZeros = digits.count - 1
    
    let parts = digits
        .enumerated()
        .filter { $0.element != "0" }
        .map { String($0.element) + String(repeating: "0", count: maxZeros - $0.offset) }
    
    return parts.joined(separator: " + ")
}

```

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
### [7kyu] Square Every Digit - Swift Solution
>Welcome. In this kata, you are asked to square every digit of a number and concatenate them.

For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

Note: The function accepts an integer and returns an integer

>Examples:

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
