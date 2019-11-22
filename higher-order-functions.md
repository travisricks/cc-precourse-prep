# Higher-order functions
Functions that operate on other functions, either by taking them as arguments or by returning them, are called **higher-order functions**. One of their biggest benefits is reusability. The `map`, `filter`, and `reduce` array methods are examples of HOFs.

Higher-order functions allow you to abstract over actions, not just values. They come in several forms. 

## Examples

Functions that create new functions:
```javascript
function greaterThan(n) {
  return m => m > n;
}
let greaterThan10 = greaterThan(10);
console.log(greaterThan10(22)); // this argument is 'm'
// → true
```


Functions that provide new types of control flow:
```javascript
function unless(test, then) {
  if (!test) then();
}

repeat(3, n => {
  unless(n % 2 == 1, () => {
    console.log(n, "is even");
  });
});
// → 0 is even
// → 2 is even
```

Rewriting `Array.map`:
```javascript
function map(array, func) {
    let result = [];
    for (let i = 0; i < array.length; i++>) {
        let original = array[i];
        let modified = func(original);
        result[i] = modified;
    }
    return result;
}
```