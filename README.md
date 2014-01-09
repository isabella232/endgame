#### endgame
A tiny module for ensuring uncaught exceptions are handled in Node.js.

#### Usage
Simply `require` and invoke.

```javascript
// failed.js

var endgame = require('endgame');

endgame();

throw new Error('y u no work?');

// Thu, 09 Jan 2014 20:03:18 GMT uncaughtException y u no work?
// Error: y u no work?
//    at Object._onImmediate (/Users/me/src/git/myapp/failed.js:7:0)
//    at processImmediate [as _immediateCallback] (timers.js:330:15)
```

If an `uncaughtException` handler has already been registered, `endgame` becomes a noop. If an `uncaughtException` handler
is registered *after* `endgame` has been invoked, `endgame`'s default handle is automatically removed in favor of the newly
registered handler.