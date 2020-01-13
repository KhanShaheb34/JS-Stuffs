# JS-Stuffs
Some good-to-know stuffs about JavaScript that is not that necessary to be aware of. If someone's curious they should know these stuffs. If you already know something, feel free to contribute.

## Contents
* ["use strict"](#use-strict)

## "use strict"
The purpose of `"use strict"` is to indicate that the code should run in *strict mode*. In the strict mode JS gives some extra errors and warnings that is ignored in the normal mode to make debugging easy.

It is written as a string in the code. So that the browsers that doesn't support the latest version of JS can ignore it. It is usually declared in the beginning of a script or a function.

```javascript
// normal mode
trump = "BAD";
console.log(trump); // BAD
```

```js
// strict mode
"use strict";

trump = "BAD";
console.log(trump); // ReferenceError: x is not defined
```
