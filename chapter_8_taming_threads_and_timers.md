# Chapter 8: Taming threads and timers
* Timers are provided as part of the objects and methods that the web browser makes available. This means that if we choose to use JavaScript in a non-browser environment, it's very likely that timers may not exist
* The browser will not queue up more than one instance of a specific `interval` handler.
* The `setTimeout()` will always have at least a 10 ms delay after the previous callback execution (it may end up being more, but never less), whereas `setInterval()` will attempt to execute a callback every 10 ms regardless of when the last callback was executed.
      setTimeout(function repeatMe() {
        /* Some long block of code... */
        setTimeout(repeatMe, 10);
      }, 10);
      setInterval(function() {
        /* Some long block of code... */
      }, 10);
* `setTimeout(callback, interval, arg1, arg2, arg3)` would cause arguments arg1, arg2, and arg3 to be passed to the timeout callback.
* 
