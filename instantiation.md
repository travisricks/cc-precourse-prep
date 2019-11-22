# Instantiation Patterns
__Instantiation__ means to create an instance of an object in an object-oriented programming language.

An instantiation pattern in JavaScript is a way to create an object using functions. Essentially a template for the objects you want to make.

There are five instantiation patterns: Functional, Functional-shared, Prototypical, Pseudoclassical, and ES6(`class`).

* Functional-shared is ideal over functional, because the methods are not repeated in memory for every object
* Of the four pre-ES6 options, Psuedoclassical is the most complex, but the most optimized

The first four were used before ES6. Since ES6 is the current standard, I'm focusing on that.

## ES6 (using `class`)
* This uses the `constructor` method.
* _Inheritance_ is when we create a parent class with properties and methods that we can extend to child classes.
* We use the `extends` keyword to create a subclass.
* The `super` keyword calls the `constructor()` of a parent class.
* Static methods are called on the class, but not on instances of the class.
```javascript
class HospitalEmployee {
  constructor(name) {
    this._name = name;
    this._remainingVacationDays = 20;
  }
  
  get name() {
    return this._name;
  }
  
  get remainingVacationDays() {
    return this._remainingVacationDays;
  }
  
  takeVacationDays(daysOff) {
    this._remainingVacationDays -= daysOff;
  }
  
  static generatePassword () {
    return Math.floor(Math.random()*10000);
  }
}

class Nurse extends HospitalEmployee {
  constructor(name, certifications) {
    super(name);
    this._certifications = certifications;
  } 
  
  get certifications() {
    return this._certifications;
  }
  
  addCertification(newCertification) {
    this.certifications.push(newCertification);
  }
}

const nurseOlynyk = new Nurse('Olynyk', ['Trauma','Pediatrics']);
nurseOlynyk.takeVacationDays(5);
console.log(nurseOlynyk.remainingVacationDays);
// ==> 15

nurseOlynyk.addCertification('Genetics');
console.log(nurseOlynyk.certifications);
// ==> [ 'Trauma', 'Pediatrics', 'Genetics' ]
```


---
_sources:_ https://medium.com/@taylorshephard1/instantiation-patterns-in-javascript-7f9463b95839, https://www.codecademy.com/