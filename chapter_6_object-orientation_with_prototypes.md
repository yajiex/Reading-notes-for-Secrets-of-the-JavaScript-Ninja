# Chapter 6: Object-orientation with prototypes
* All functions have a `prototype` property that initially references an empty `object`.
* Instance members created inside a `constructor` will occlude properties of the same name defined in the `prototype`. Binding operations within the `constructor` always take precedence over those in the `prototype`.
* Each `object` in JavaScript has an implicit property named `constructor` that references the constructor that was used to create the object. And because the `prototype` is a property of the constructor, each object has a way to find its `prototype`.
* The best technique for creating prototype chain is to use an instance of an `object` as the other object's prototype: `SubClass.prototype = new SuperClass();`
* We advise strongly against to use the `Person` prototype object directly as the `Ninja` prototype, like this: `Ninja.prototype = Person.prototype;`. By doing this, any changes to the `Ninja` prototype will also change the `Person` prototype because they're the same object, and that's bound to have undesirable side effects.
* JavaScript provides a method called `hasOwnProperty()`, which can be used to determine whether properties are actually defined on an object instance versus imported from a prototype.
* The expression `this instanceof arguments.callee` will evaluate to `true` when executed within a constructor, but `false` when executed within a regular function.
