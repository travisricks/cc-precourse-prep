A recursive function is a function that calls itself. 

A classic example from math is factorial. A factorial is the product of all positive integers less than or equal to it. For example 5! = 5 * 4 * 3 * 2 * 1 = 120.

Without using recursion, you can write this in JavaScript using a for loop:
```javascript
function factorial(n) {
    let result = 1;
    for (let i = n; i > 1; i--) {
        result *= i;
    }
    return result;
}
```

But using recursion, it can be expressed like this:
```javascript
function factorial(x) {
  // TERMINATION
  if (x < 0) return;
  // BASE
  if (x === 0) return 1;
  // RECURSION
  return x * factorial(x - 1);
}

factorial(5);
// 120
```

## 3 Features of a Recursive Function
1. A Termination Condition <br>
`if something bad happens` **stop**<br>
This is the fail-safe case.
1. A Base Case <br>
`if X happens` Similar to termination that it stops the recursion, but this is the **goal** of the function. In the factorial example, it's n=1.
1. The Recursion<br>
`where the function calls itself`

---
When the function returns everything will **unwind**. This is because recursion is simply a group of nested function calls. With nested functions, **the most inner nested function will return first**.

```
factorial(3);

// how it works
factorial(0) returns 1
factorial(1) returns 1 * factorial(0), or just 1*1
factorial(2) returns 2 * factorial(1), or just 2*1*1
factorial(3) returns 3 * factorial(2), or just 3*2*1*1

---
// another explanation
factorial(3) returns 3 * factorial(2)
factorial(2) returns 2 * factorial(1)
factorial(1) returns 1 * factorial(0)
factorial(0) returns 1
// once base case executes, the function will return/unwind in order from inner to outer:

factorial(0) returns 1                 => 1
factorial(1) returns 1 * factorial(0)  => 1 * 1
factorial(2) returns 2 * factorial(1)  => 2 * 1 * 1
factorial(3) returns 3 * factorial(2)  => 3 * 2 * 1 * 1
// 3 * 2 * 1 * 1 = 6
```

## Example: reversing a string
```
function revStr(str){
  if (str === '') return '';
  return revStr(str.substr(1)) + str[0];
}
revStr('cat');
// tac
```

what's happening as the function **unwinds**:
```
revStr('cat')  returns revStr('at') + 'c'
revStr('at')   returns revStr('t') +  'a'
revStr('t')    returns revStr('') +   't'
revStr('')     returns               ''

// unwinds to:
revStr('')     returns                ''  => ''
revStr('t')    returns revStr('') +   't' => '' + 't'
revStr('at')   returns revStr('t') +  'a' => '' + 't' + 'a'
revStr('cat')  returns revStr('at') + 'c' => '' + 't' + 'a' + 'c'
// tac
```

---
_sources:_ EloquentJS, https://codeburst.io/learn-and-understand-recursion-in-javascript-b588218e87ea