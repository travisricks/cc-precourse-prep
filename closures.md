# Closures

Closures are important because they control what is and isn’t in scope in a function, along with which variables are shared between sibling functions in the same containing scope. This concept is important in both functional and object oriented programming styles.

Closures are frequently used in JavaScript for object data privacy, in event handlers and callback functions, and in partial applications, currying, and other functional programming patterns.

## What is a Closure?
A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). A closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created.

To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to another function.

The inner function will have access to the variables in the outer function scope, even after the outer function has returned.

## Using Closures (Examples)
In JavaScript, closures are the primary mechanism used to enable data privacy. When you use closures for data privacy, the enclosed variables are only in scope within the containing (outer) function. You can’t get at the data from an outside scope except through the object’s privileged methods. In JavaScript, any exposed method defined within the closure scope is privileged. For example:

```javascript
const getSecret = (secret) => {
  return {
    get: () => secret
  };
};

test('Closure for object privacy.', assert => {
  const msg = '.get() should have access to the closure.';
  const expected = 1;
  const obj = getSecret(1);

  const actual = obj.get();

  try {
    assert.ok(secret, 'This throws an error.');
  } catch (e) {
    assert.ok(true, `The secret var is only available
      to privileged methods.`);
  }

  assert.equal(actual, expected, msg);
  assert.end();
});
```


---
_sources:_ https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36, 