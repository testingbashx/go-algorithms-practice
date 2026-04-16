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