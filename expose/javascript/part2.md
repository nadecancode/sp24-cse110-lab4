For the answer below, if it's just a simple value then it implies the value is being printed during function call. If I put an error then it means such error happened during function call, if question asked what the function returns then that value will be the value that function returned.

1`3`, this is because `var` doesn't care about block scope so we can access the variable `i` outside of for-loop as well. Since we have finished looping which means loop reached termination condition which means `i = prices.length`. Since we supplied a 3-element array as `prices`, `i`, after the loop, will be equal to the length of this array, which is `3`.
2. `150`, `discountedPrice` is accessible outside of the while loop for the same reason as Question 1. However, it just keeps getting updated until the for loop terminates and since the last valid index for `i` is `2` (`i = 3` will not make for loop run since at that point it got terminated). The value of `discountedPrice` is essentially just `prices[2] * (1 - discount)`, which is `300 * (1 - 0.5) = 150`.
3. `150`, this is essentially same as `discountedPrice` except the `var` it declared outside of the for-loop, which doesn't make a difference in this context. At the final iteration of the for-loop before it terminates, `finalPrice = Math.round(150 * 100) / 100` which is just `150`.
4. `[50, 100, 150]`. This function basically takes each value in `prices` and transform them into discounted value with this formula: `finalPrice = round(price * (1 - discount))`, since the discount rate is `0.5` in this case, it will just push `[100 * 0.5, 200 * 0.5, 300 * 0.5]` to the `discounted` array which then becomes `[50, 100, 150]`.
5. `ReferenceError: i is not defined` since function switched to `let` for variable declaration therefore it's not possible to access `i` outside of the for loop due to block scope.
6. `ReferenceError: discountedPrice is not defined` since function switched to `let` for `discountedPrice` declaration so it's not possible to access it outside of the block scope.
7. `150`, since the print statement is in the same block as `finalPrice` it is fine to access it that way. Otherwise, it is same as Question 3 which is why it yields `150`.
8. `[50, 100, 150]`. This is same as Question 4 and it does not yield any error since there's no case that a variable declared with `let` within one block got called from outside so in this context, the returned value will be same as Question 4 for the same reason.
9. `ReferenceError: i is not defined` since `i` is declared inside the for-loop block scope and line 11 tries to call it from outside of that block, therefore it violates the `let` constraint and since there're no other `i`s defined with `var` or `let` in the same scope (or `var` from other blocks) the variable `i` will be undefined and therefore throws such error.
10. `3`, since `length` print statement is in the same scope as `length` it'll print properly. Because `length` is just the length of array `prices`'s size, in this case it will be 3.
11. `[50, 100, 150]`. There is no error because all variables are declared and referenced in their respective scope. Other than that, the behavior of this function basically takes `prices` and transform each value by multiplying them with `1 - discount`. Since the `discount` here is `0.5` it basically just halves each value in the `prices` array, therefore it returns `[50, 100, 150]`.
12. Answers:
- A: `student.name`
- B: `student['Grad Year']`
- C: `student['greeting']()`
- D: `student['Favorite Teacher'].name`
- E: `student.courseLoad[0]`
13. Answers:
- A: `32`, when you add integer to a string it maps integers to their string representation so it becomes string concatenation.
- B: `1`, when you subtract integer from a string, the string is casted to integer instead (since there's no string un-concatenation) so it becomes evaluating `3 - 2`
- C: `3`, `null` maps to `0` according to type conversions so this is just `3 + 0 = 3`
- D: `3null`, since we're adding a string to `null` this means `null` is being converted to string, which is just `'null'` therefore it's just string concatenation.
- E: `4`. Since `true` maps to 1 in arithmetic operation this becomes `1 + 3 = 4`
- F: `0`, since false maps to 0 in arithmetic operation this becomes `0 + null`, since this is integer + null the `null` gets converted to integer instead, which is `0`. Therefore this is just `0 + 0 = 0`
- G: `3undefined`, since this is string concatenation the `undefined` gets casted to string as well, which is just `'undefined'` and this becomes string concatenation of `'3'` and `'undefined'` which is `'3undefined'`
- H: `NaN`, since this is integer arithmetic operation, the `undefined` gets casted to its number representation, `NaN` so this becomes `'3' - NaN` (the undefined gets casted to number instead of string because this is a subtract) and since string - number converts the string to number, this becomes `3 - NaN` which is `NaN`.
14. Answers:
- A: `true`, when comparing values of different types, the values are converted to numbers. This becomes `2 > 1 = true`
- B: `false`, this is string comparison and since `2` has higher order than `1` it means `'2' > '12'` which makes `'2' < '12'` false.
- C: `true`, without strict equality converts types to numbers, so this becomes `2 == 2 = true`
- D: `false`, strict equality checking does not convert types so this is equality-checking string to a number, which is intuitively false.
- E: `false`, `true` after number conversion evaluates to `1`, `1 == 2` is false.
- F: `true`, `Boolean(number)` evaluates to true for any non-intuitively-empty number to `true`, which is the case for `2`. This means it is `true === true` which is true.
15. `==` is non-strict equality which for values with different types, it converts the types to numbers instead. While `===` only checks for equality without converting the types.
16. See `part2-question16.js`
17. It will return `[2, 4, 6]`. So basically this `modifyArray` iterates through the input array and call the function `callback` with `array[i]` as input, then pushes the output from `callback(array[i])` to `newArr` then returns the array. In other words, it basically transforms the `array` based on function `callback` with input `array[i]`. Since `doSomething` basically returns the double its integer input, this `modifyArray` function will just double each element in the array, hence the result.
18. See `part2-question18.js`
19. `1 4 3 2` (space = line separator). This is due to how the javascript does event loop queue, setTimeout pushes this specific operation and a time value to the event loop queue and later the event loop polls according to the specific time. This means `setTimeout(xxx, 0)` will be executed later than the code under it. Therefore `1` will be printed first, then `4` gets printed since it's not in the event loop queue, then `3` gets printed since it's the first thing in the event loop queue (sorted by timeout attribute) and then finally it's `2`.