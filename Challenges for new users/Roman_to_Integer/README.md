Question: [https://leetcode.com/problems/roman-to-integer/]()

Data structures used: Dictionary

Time complexity: O(n)

Space complexity: O()

Function:
- Return the numeric decimal form: <code>num</code>, of the inputted roman numerals: <code>s</code>.

Parameters:
- s: a string in the form of roman numeral's

Variables:
- roman_map: a dictionary that maps each numeral to it's corresponding number

- n: a variable to account for the n items (length of s)

Return value:
- num: an accumulator variable used to compute the sum of the inputted numerals

Explanation:
We iterate over all characters in the string, s, and we check
if the current index, i, is the last one. This is to constrain the IndexError on the last iteration as we try to access i + 1 in the future.

Then we check whether the current numeral's value
is less than that of the next one.

1) if not, it increments by the current numeral's value through mapping with our dictionary.

2) if so, this signifies any of the given patterns (IV, IX, CM etc.) as shown in the description. num would decrement by the current numeral's (i) value through mapping. Then it indexes to the next character (i + 1) and behave like case 1.

  i.e "IX", when i = 0: num -= 1, when i = 1: num += 10
      num = 9

Hence, num accurately represents the net values of such patterns.
