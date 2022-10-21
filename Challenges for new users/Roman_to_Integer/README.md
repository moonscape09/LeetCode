<h1>Question: https://leetcode.com/problems/roman-to-integer</h1>

**Data structures used**: Dictionary

**Time complexity**: O(n) (presuming no limit on string length, otherwise constant)

**Space complexity**: O(1) (only 7 items)

<h3>Function</h3>
Return the numeric decimal form: <code>num</code>, of the inputted roman numerals: <code>s</code>.


**Parameters:**
- <code>s</code>: a string in the form of roman numeral's

**Variables:**
- <code>roman_map</code>: a dictionary that maps each numeral to it's corresponding number

- <code>n</code>: a variable to account for the n items (length of <code>s</code>)

**Return value:**
- <code>num</code>: an accumulator variable used to compute the sum of the inputted numerals

**Explanation:**
We iterate over all characters in the string, <code>s</code>, and we check
if the current index, <code>i</code>, is the last one. This is to constrain the <code>IndexError</code> on the last iteration as we try to access <code>i + 1</code> in the future.

Then we check whether the current numeral's value
is less than that of the next one.

1) if not, it increments by the current numeral's value through mapping with our dictionary.

2) if so, this signifies any of the given patterns (IV, IX, CM etc.) as shown in the description. num would decrement by the current numeral's (<code>i</code>) value through mapping. Then it indexes to the next character (<code>i + 1</code>) and behave like case 1.

  i.e <code>"IX"</code>, when <code>i = 0</code>: <code>num -= 1 </code>, when <code>i = 1</code>: <code>num += 10</code>
      <code>num = 9</code>

Hence, <code>num</code> accurately represents the net values of such patterns.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>III</code>  | 3  |
| <code>LVIII</code>  | 58  |
| <code>MCMXCIV</code> | 1994 |
