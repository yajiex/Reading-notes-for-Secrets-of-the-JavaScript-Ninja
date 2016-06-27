# Chapter 4: Wielding functions
* 
* Make use of function properties:
      var store = {
        nextId: 1,
        cache: {},
        add: function(fn) {
          if (!fn.id) {
            fn.id = store.nextId++;
            return !!(store.cache[fn.id] = fn);
          }
        }
      };
* `Memoization` is the process of building a function that's capable of remembering its previously computed values.
      function isPrime(value) {
        if (!isPrime.anwers) isPrime.answers = {};
        if (isPrime.answers[value] != null) {
          return isPrime.answers[value];
        }
        var prime = value != 1; // 1 can never be prime
        for (var i = 2; i < value; i++) {
          if (value % i == 0) {
            prime = false;
            break;
          }
        }
        return isPrime.answers[value] = prime;
      }
* Memorize DOM elements:
      function getElements(name) {
        if (!getElements.cache) getElements.cache = {};
        return getElements.cache[name] =
          getElements.cache[name] ||
          document.getElementsByTagName(name);
        }
* Within a function, we can determine two things about its arguments:
  1. How many named parameters it was declared with, via the `length` property
  2. How many arguments were passed on the invocation, via `arguments.length`
* A method-overloading function:
      function addMethod(object, name, fn) {
        var old = object[name];
        object[name] = function(){
          if (fn.length == arguments.length)
            return fn.apply(this, arguments)
          else if (typeof old == 'function')
            return old.apply(this, arguments);
        };
      }
      

