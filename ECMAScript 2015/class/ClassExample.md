**`class.js`**
===
- [**`class.js`**](#classjs)
- [`class`](#class)
- [`constructor` Method](#constructor-method)
- [`class` Methods](#class-methods)
- [Hoisting](#hoisting)
- [`get` and `set`](#get-and-set)
- [`class` Inheritance](#class-inheritance)
- [Method Overriding](#method-overriding)
- [`static` Methods](#static-methods)
- [Private `class` features](#private-class-features)
- [Private instance methods](#private-instance-methods)
- [Private static methods](#private-static-methods)
  - [Example `class.js`](#example-classjs)

---
# `class`
- Use the keyword `class` to create a `class`.
- Always add a method named `constructor()`
- The class has two initial properties: "name" and "year".

# `constructor` Method
- The `constructor` method is a special method
- It has to have the exact name `constructor`
- It is executed automatically when a new object is created
- It is used to initialize object properties
- If you do not define a `constructor` method, JavaScript will add an empty `constructor` method.

# `class` Methods
- `class` methods are created with the same syntax as object methods.
- We can add any number of methods.
- method can/may `return` data with `return` keyword
- method can/may have parameter

# Hoisting
- Unlike functions, and other JavaScript declarations, `class` declarations are not hoisted.That means that you must declare a class before you can use it:

# `get` and `set`
- classes also allows you to use getters and setters.
- It can be smart to use getters and setters for your properties, especially if you want to do something special with the value before returning them, or before you set them.
- To add getters and setters in the `class`, use the `get` and `set` keywords.
- you do not use parentheses when you want to get the property value.

# `class` Inheritance
- To create a `class` inheritance, use the extends keyword.
- A `class` created with a `class` inheritance inherits all the methods from another class
- The `super()` method refers to the parent `class`.
- By calling the `super()` method in the constructor method, we call the parent's constructor method and gets access to the parent's properties and methods
- Inheritance is useful for code reusability: reuse properties and methods of an existing class when you create a new class.

# Method Overriding
- is a mechanism by which the child `class` redefines the superclass method
- The `super` keyword is used to refer to the immediate parent of a `class` and can be used to invoke the parent method in the subclass

# `static` Methods
- `static class` methods are defined on the `class` itself.
- You cannot call a `static` method on an `object`, only on an `object class`
- There is a restriction on `private static` fields: Only the `class` which defines the private `static` field can access the field. This can lead to unexpected behavior when using this.
- `private static` fields are only accessible on the `class` itself or on the this context of `static` methods, but not on the this context of instance methods

# Private `class` features
- `class` fields are public by default, but private `class` members can be created by using a hash `#` prefix.
- The privacy encapsulation of these `class` features is enforced by JavaScript itself.
- Private fields include private instance fields and private `static` fields.
- Private instance fields are declared with `# names` (pronounced "hash names")
- Private fields are accessible on the `class constructor` from inside the `class` declaration itself.
- They are used for declaration of field names as well as for accessing a field's value.
- 
# Private instance methods
- Private instance methods are methods available on `class` instances whose access is restricted in the same manner as private instance fields.
- Private instance methods may be generator, `async`, or `async` generator functions.
- Private getters and setters are also possible, although not in generator, `async`, or `async` generator forms.

# Private static methods
- Like their public equivalent, `private static` methods are called on the `class` itself, not instances of the class.
- Like `private static` fields, they are only accessible from inside the `class` declaration.
- The same restriction previously mentioned for private static fields holds for private static methods, and similarly can lead to unexpected behavior when using this

## Example `class.js`
```js
class Car {
    #privateField;
    static #staticPrivateField;

    //defeult constructor  
    constructor(name, year) {
        this.name = name;
        this.year = year;
    }

    #privateMethod() {
        return 'private hello world';
    }

    static #staticPrivateMethod(){
        return 'static private hello world';
    }

    get Name(){
        return this.name;
    }

    set Name(x){
        this.name = x;
    }

    //methods
    age() {
        let date = new Date();
        return date.getFullYear() - this.year;
    }

    methodwithparameter(x)
    {
        return "i received" + x;
    }

    static staticMethod() {
        return "static Hello!!";
    }
}

class Model extends Car {
    constructor(brand,year,model){
        super(brand,year);
        this.model = model;
    }

    show() {
        return this.age() + ', it is a ' + this.model;
    }

    //overrides the parent method
    methodwithparameter(x)
    {
        super.methodwithparameter(x); //invokes the parent method
        return "i received" + x;
    }
}

//usage
let myCar = new Car("Ford", 2014);
document.getElementById("demo").innerHTML =
"My car is " + myCar.age() + " years old.";
myCar.Name = "swift";

//inheritance
let myCar = new Model("Ford", "Mustang");
document.getElementById("demo").innerHTML = myCar.show();


```
