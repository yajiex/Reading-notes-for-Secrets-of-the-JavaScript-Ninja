# Chapter 5: Closing in on closures
* A `closure` is the scope created when a function is declared that allows the function to access and manipulate variables that are external to that function. A declared function can be called at any later time, even after the scope in which it was declared has gone away.
* A polyfill for `Function.prototype.bind`:
      Function.prototype.bind = function(){
          var fn = this,
              args = Array.prototype.slice.call(arguments), 
              object = args.shift();
          return function(){
              return fn.apply(object, args.concat(Array.prototype.slice.call(arguments)));
          };
      };
* A polyfill for `Function.prototype.partial`
      Function.prototype.partial = function() {
          var fn = this,
              args = Array.prototype.slice.call(arguments);
          return function() {
              var arg = 0;
              for (var i = 0; i < args.length && arg < arguments.length; i++) {
                  if (args[i] === undefined) {
                      args[i] = arguments[arg++];
                  }
              }
              return fn.apply(this, args);
          };
      };
* A polyfill for Function wrapping, which is a technique for encapsulating the logic of a function while overwriting it with new or extended functionality in a single step.
      function wrap(object, method, wrapper) {
          var fn = object[method];
          return object[method] = function() {
              return wrapper.apply(this, [fn.bind(this)].concat(
                  Array.prototype.slice.call(arguments)));
          };
      }
      
      if (Prototype.Browser.Opera) {
          wrap(Element.Methods, "readAttribute", function(original, elem, attr) {
              return attr == "title" ? elem.title : original(elem, attr);
          });
      }
