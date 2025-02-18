# JavaScript Coding Challenge: Add Two Numbers

## Problem Statement

Create a function `addTwoNumbers` that takes two numerical arguments and returns their sum. Ensure that the function handles various edge cases, such as:

- Both numbers are positive.
- Both numbers are negative.
- One number is positive, and the other is negative.
- One or both numbers are zero.

**Constraints:**

- The function should handle both integer and floating-point numbers.
- Do not use the `+` operator to perform the addition.

## Solution

To solve this problem without using the `+` operator, we can utilize bitwise operations. Specifically, we can use the bitwise XOR (`^`) and bitwise AND (`&`) operators along with bit shifting to perform the addition. This method is based on how binary addition works at the bit level.

Here's the step-by-step approach:

1. **Bitwise XOR (`^`)**: This operation adds two bits without carrying. For example:
   - `0 ^ 0 = 0`
   - `1 ^ 0 = 1`
   - `1 ^ 1 = 0`

   Applying XOR to two numbers gives us the sum without considering the carry.

2. **Bitwise AND (`&`) and Left Shift (`<<`)**: The AND operation identifies where carries are needed (i.e., where both bits are 1). Shifting this result to the left by one position (`<< 1`) gives us the carry values that need to be added to the sum.

3. **Iterative Addition**: By repeatedly applying the above two operations—updating the sum with XOR and the carry with AND and left shift—and combining the results, we can compute the total sum. This process continues until there are no more carries.

<details>
 <summary>Solution</summary>

Here's the implementation of the `addTwoNumbers` function:

```javascript
function addTwoNumbers(a, b) {
  while (b !== 0) {
    let carry = a & b; // Calculate carry bits
    a = a ^ b;         // Add without considering carry
    b = carry << 1;    // Prepare carry for next addition
  }
  return a;
}
```
</details>
