# 🧠 Go (Golang) Practice

A collection of Go (Golang) exercises focused on building strong problem-solving skills.  
Covers string manipulation, character handling, and base conversion.

---

## 📌 Table of Contents

- First Rune
- Last Rune
- Nth Rune
- Compare Strings
- Alpha Count
- Index (Substring Search)
- Concat Strings
- Is Upper
- Is Alpha
- Is Printable
- To Upper
- To Lower
- Print Numbers in Order
- Trim Atoi
- Capitalize Words
- Basic Join
- Join with Separator
- Print Number in Base
- Atoi Base

---

## Problem 1: First Rune

### 🧩 Question
Write a function that returns the first rune of a string.

### 💡 Simplified Breakdown
- Loop through the string
- Return the first rune immediately

### ✅ Solution
```go
func FirstRune(s string) rune {
	for _, r := range s {
		return r
	}
	return 0
}

----------------

Problem 2: Last Rune
🧩 Question

Write a function that returns the last rune of a string.

💡 Simplified Breakdown
Loop through all runes
Keep updating the variable
Last value is the answer


✅ Solution

func LastRune(s string) rune {
	var last rune
	for _, r := range s {
		last = r
	}
	return last
}

Problem 3: Nth Rune
🧩 Question

Return the nth rune of a string. If not possible, return 0.

💡 Simplified Breakdown
Count runes (1-based index)
Return when position matches

✅ Solution

package piscine

func NRune(s string, n int) rune {
	if n <= 0 {
		return 0
	}

	count := 1
	for _, r := range s {
		if count == n {
			return r
		}
		count++
	}

	return 0
}

Problem 4: Compare Strings
🧩 Question

Compare two strings and return:

0 if equal
-1 if a < b
1 if a > b
💡 Simplified Breakdown
Compare characters one by one
If equal, compare lengths

✅ Solution

package piscine

func Compare(a, b string) int {
	i := 0

	for _, ra := range a {
		if i >= len([]rune(b)) {
			return 1
		}

		rb := []rune(b)[i]

		if ra < rb {
			return -1
		}
		if ra > rb {
			return 1
		}
		i++
	}

	if i < len([]rune(b)) {
		return -1
	}

	return 0
}

Problem 5: Alpha Count
🧩 Question

Count only alphabet letters in a string.

💡 Simplified Breakdown
Count only A–Z and a–z

✅ Solution

package piscine

func AlphaCount(s string) int {
	count := 0

	for _, r := range s {
		if (r >= 'a' && r <= 'z') || (r >= 'A' && r <= 'Z') {
			count++
		}
	}
	return count
}

Problem 6: Index (Substring Search)
🧩 Question

Return the index of first occurrence of substring.

💡 Simplified Breakdown
Slide over string
Compare characters manually

✅ Solution

package piscine

func Index(s string, toFind string) int {
	if len(toFind) == 0 {
		return 0
	}

	for i := 0; i <= len(s)-len(toFind); i++ {
		match := true
		for j := 0; j < len(toFind); j++ {
			if s[i+j] != toFind[j] {
				match = false
				break
			}
		}
		if match {
			return i
		}
	}

	return -1
}


Problem 7: IsUpper
🧩 Question

Check if string contains only uppercase letters.

💡 Simplified Breakdown
Every character must be between 'A' and 'Z'

✅ Solution

package piscine

func IsUpper(s string) bool {
	for _, v := range s {
		if v < 'A' || v > 'Z' {
			return false
		}
	}

	return true
}

Problem 8: IsAlpha
🧩 Question

Check if string is alphanumeric.

💡 Simplified Breakdown
Allow letters and digits only

✅ Solution

package piscine

func IsAlpha(s string) bool {
	for _, r := range s {
		if !((r >= 'a' && r <= 'z') || (r >= 'A' && r <= 'Z') || (r >= '0' && r <= '9')) {
			return false
		}
	}
	return true
}


Problem 9: IsPrintable
🧩 Question

Check if string contains only printable characters.

💡 Simplified Breakdown
ASCII range: 32–126

✅ Solution

package piscine

func IsPrintable(s string) bool {
	for _, r := range s {
		if r < 32 || r > 126 {
			return false
		}
	}
	return true
}

Problem 10: To Upper
🧩 Question

Convert string to uppercase.

💡 Simplified Breakdown
Lowercase → subtract 32

✅ Solution

package piscine

func IsUpper(s string) bool {
	for _, v := range s {
		if v < 'A' || v > 'Z' {
			return false
		}
	}

	return true
}


Problem 11: ToLower
🧩 Question

Convert all letters in a string to lowercase.

💡 Simplified Breakdown
Convert uppercase letters to lowercase
Leave others unchanged


✅ Solution

func ToLower(s string) string {
	result := ""

	for _, r := range s {
		if r >= 'A' && r <= 'Z' {
			r += 32
		}
		result += string(r)
	}

	return result
}


Problem 12: PrintNumbers in Order
🧩 Question

Write a function that prints the digits of an integer in ascending order.

💡 Simplified Breakdown
Extract digits from the number
Store them
Sort them in ascending order
Print each digit

✅ Solution

package piscine

import "github.com/01-edu/z01"

func PrintNbr(n int) {
	if n < 0 {
		z01.PrintRune('-')
		if n/10 != 0 {
			PrintNbr(-(n / 10))
		}
		z01.PrintRune(rune('0' + -(n % 10)))
		return
	}

	if n >= 10 {
		PrintNbr(n / 10)
	}
	z01.PrintRune(rune('0' + n%10))
}


Problem 13: Trim Atoi
🧩 Question

Write a function that extracts digits from a string and returns them as an integer.

💡 Simplified Breakdown
Loop through string
Collect digits only
Handle optional - sign before digits
Build number step by step

✅ Solution

func TrimAtoi(s string) int {
	result := 0
	sign := 1
	found := false

	for _, r := range s {
		if r == '-' && !found {
			sign = -1
		}
		if r >= '0' && r <= '9' {
			result = result*10 + int(r-'0')
			found = true
		}
	}

	return result * sign
}


Problem 14: CapitalizeWords
🧩 Question

Write a function that capitalizes the first letter of each word and lowercases the rest.

💡 Simplified Breakdown
Detect start of a word
Uppercase first letter
Lowercase remaining letters
Reset when hitting non-alphanumeric characters

✅ Solution

package piscine

func Capitalize(s string) string {
	runes := []rune(s)
	newWord := true

	for i, r := range runes {
		if (r >= 'a' && r <= 'z') || (r >= 'A' && r <= 'Z') || (r >= '0' && r <= '9') {
			if newWord {
				if r >= 'a' && r <= 'z' {
					runes[i] = r - 32
				}
			} else {
				if r >= 'A' && r <= 'Z' {
					runes[i] = r + 32
				}
			}

			newWord = false
		} else {
			newWord = true
		}
	}

	return string(runes)
}

Problem 15: Basic Join
🧩 Question

Write a function that concatenates all strings in a slice.

💡 Simplified Breakdown
Loop through slice
Append each string to result

✅ Solution


func BasicJoin(elems []string) string {
	result := ""
	for _, s := range elems {
		result += s
	}
	return result
}


Problem 16: Join with Separator
🧩 Question

Write a function that joins strings with a separator.

💡 Simplified Breakdown
Start with first element
Add separator before each next element
Avoid extra separator at the end

✅ Solution

package piscine

func Join(strs []string, sep string) string {
	if len(strs) == 0 {
		return ""
	}

	result := strs[0]

	for i := 1; i < len(strs); i++ {
		result = result + sep
		result = result + strs[i]
	}
	return result
}


Problem 17: PrintNumber in Base
🧩 Question

Write a function that prints an integer in a given base.

💡 Simplified Breakdown
Validate the base
Handle negative numbers
Convert using division and remainder
Print digits recursively

✅ Solution

func PrintNbrBase(nbr int, base string) {
	if !isValidBase(base) {
		z01.PrintRune('N')
		z01.PrintRune('V')
		return
	}

	if nbr < 0 {
		z01.PrintRune('-')
	} else {
		nbr = -nbr
	}

	printRecursive(nbr, base)
}


Problem 18: Atoi Base
🧩 Question

Write a function that converts a string in a given base to an integer.

💡 Simplified Breakdown
Validate base
For each character:
Find its value in base
Multiply result by base length
Add value

✅ Solution

package piscine

func IsValidBase(base string) bool {
	if len(base) < 2 {
		return false
	}

	for i := 0; i < len(base); i++ {
		if base[i] == '+' || base[i] == '-' {
			return false
		}
		for j := i + 1; j < len(base); j++ {
			if base[i] == base[j] {
				return false
			}
		}
	}

	return true
}

func getIndex(r rune, base string) int {
	for i, b := range base {
		if r == b {
			return i
		}
	}
	return -1
}

func AtoiBase(s string, base string) int {
	if !IsValidBase(base) {
		return 0
	}

	baseLen := len(base)
	result := 0

	for _, r := range s {
		val := getIndex(r, base)
		if val == -1 {
			return 0
		}

		result = result*baseLen + val
	}
	return result
}


## Interactive Factorial

package piscine

func IterativeFactorial(nb int) int {
	if nb < 0 {
		return 0
	}

	number := 1

	maxInt := int(^uint(0) >> 1)

	for i := 2; i <= nb; i++ {

		if number > maxInt/i {
			return 0
		}
		number *= i
	}

	return number
}

## Recursive Factorial

package piscine

func RecursiveFactorial(nb int) int {
	if nb < 0 {
		return 0
	}

	if nb > 20 {
		return 0
	}

	if nb == 0 {
		return 1
	}

	return nb * RecursiveFactorial(nb-1)
}


## Iterative Power

package piscine

func IterativePower(nb int, power int) int {
	if power < 0 {
		return 0
	}

	result := 1

	for i := 1; i <= power; i++ {
		result *= nb
	}

	return result
}

## Recursive Power

package piscine

func RecursivePower(nb int, power int) int {
	if power < 0 {
		return 0
	}

	if power == 0 {
		return 1
	}

	return nb * RecursivePower(nb, power-1)
}

## Fibonacci

package piscine

func Fibonacci(index int) int {
	if index < 0 {
		return -1
	}

	if index == 0 {
		return 0
	}

	if index == 1 {
		return 1
	}

	return Fibonacci(index-1) + Fibonacci(index-2)
}

## SQRT
package piscine

func Sqrt(nb int) int {
	if nb < 0 {
		return 0
	}

	for i := 1; i <= nb/i; i++ {
		if i*i == nb {
			return i
		}
	}

	return 0
}

## IsPrime

package piscine

func IsPrime(nb int) bool {
	if nb <= 1 {
		return false
	}
	for i := 2; i <= nb/i; i++ {
		if nb%i == 0 {
			return false
		}
	}

	return true
}

## Findnextprime

package piscine

func IsPrimeNum(nb int) bool {
	if nb <= 1 {
		return false
	}
	for i := 2; i <= nb/i; i++ {
		if nb%i == 0 {
			return false
		}
	}

	return true
}

func FindNextPrime(nb int) int {
	if nb <= 2 {
		return 2
	}

	if nb%2 == 0 {
		nb++
	}

	for !IsPrimeNum(nb) {
		nb += 2
	}

	return nb
}

