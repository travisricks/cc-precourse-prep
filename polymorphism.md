# Polymorphism
Polymorphism — the ability to write a single function that handles many data-types — is a fundamental form of abstraction. It is one of the tenets of Object-Oriented Programming (OOP). It is the practice of designing objects to share behaviors and to be able to override shared behaviors with specific ones. Polymorphism takes advantage of inheritance in order to make this happen.

In OOP everything is considered to be an object. This abstraction can be taken all the way down to nuts and bolts for a car, or as broad as simply a car type with a year, make, and model.

To have a polymorphic car scenario there would be the base car type, and then there would be subclasses which would inherit from car and provide their own behaviors on top of the basic behaviors a car would have. For example, a subclass could be TowTruck which would still have a year make and model, but might also have some extra behaviors and properties which could be as basic as a flag for IsTowing to as complicated as the specifics of the lift.

Using an example of people and employees, all employees are people, but all people are not employees. So people will be the super class, and employee the sub class. People may have ages and weights, but they do not all have salaries. Employees are people so they will inherently have an age and weight, but also because they are employees they will have a salary.

```javascript
function Person(age,weight){
 this.age = age;
 this.weight = weight;
}
```
And we will give Person the ability to share their information:
```javascript
Person.prototype.getInfo = function(){
 return "I am " + this.age + " years old " +
    "and weighs " + this.weight +" kilo.";
};
```
Then we add an Employee subclass of Person:
```javascript
function Employee(age,weight,salary){
 this.age = age;
 this.weight = weight;
 this.salary = salary;
}
Employee.prototype = new Person();
```
And override the behavior of getInfo by defining one which is more fitting to an Employee:
```javascript
Employee.prototype.getInfo = function(){
 return "I am " + this.age + " years old " +
    "and weighs " + this.weight +" kilo " +
    "and earns " + this.salary + " dollar.";  
};
```
---
_sources:_ https://stackoverflow.com/questions/27642239/what-is-polymorphism-in-javascript, https://medium.com/yld-blog/program-like-proteus-a-beginners-guide-to-polymorphism-in-javascript-867bea7c8be2, https://www.codeproject.com/Articles/315169/Polymorphism-in-JavaScript