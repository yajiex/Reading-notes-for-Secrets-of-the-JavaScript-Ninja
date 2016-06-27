# Chapter 3: Functions are fundamental
* All functions have a property named `name` that stores the function's name as a string. Functions with no name still possess this property, set to the empty string. Please be aware in the following sample, the function `name` is still empty string.
      var shout = function() {};
* The `!!` construct is a simple way of turning any JavaScript expression into its Boolean equivalent      
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
