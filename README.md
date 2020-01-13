# JS-Stuffs
Some good-to-know stuffs about JavaScript that is not that necessary to be aware of. If someone's curious they should know these stuffs. If you already know something, feel free to contribute.

## Contents
* ["use strict"](#use-strict)

## "use strict"
The purpose of `"use strict"` is to indicate that the code should run in *strict mode*. In the strict mode JS gives some extra errors and warnings that is ignored in the normal mode to make debugging easy.

It is written as a string in the code. So that the browsers that doesn't support the latest version of JS can ignore it. It is usually declared in the beginning of a script or a function.

```js
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

> The `"use strict"` directive is only recognized at the beginning of a script or a function.

Strict mode can be declared in the global or scope or in a function. When a function is in strict mode, it won't affect the codes that are outside the function;

```js
trump = "BAD";
console.log(trump); // BAD

function makeNoakhaliABivag() {
  "use strict";
  noakhali = "BIVAG";
}

makeNoakhaliABivag(); // ReferenceError: noakhali is not defined
```

### Stuffs not allowed in strict mode:
* Using a variable without declaring it (Check the example given before)
* Deleting a variable
  ```js
  "use strict";

  const trump = "BAD";
  delete trump; // SyntaxError: Delete of an unqualified identifier in strict mode.

  function makeNoakhaliABivag() {
    const noakhali = "BIVAG";
  }
  delete makeNoakhaliABivag(); // SyntaxError: Delete of an unqualified identifier in strict mode.
  ```
* Duplicating a parameter in a function
  ```js
  "use strict";

  function makeNoakhaliABivag(noakhali, noakhali) {
    noakhali = "BIVAG";
  } // SyntaxError: Duplicate parameter name not allowed in this context
  ```
* Octal numeric literals and octal escape characters
  ```js
  "use strict";

  const octalNumber = 012; // SyntaxError: Octal literals are not allowed in strict mode.
  const octalNumber = "\012"; // SyntaxError: Octal escape sequences are not allowed in strict mode.
  ```
* Writing to a read-only or get-only property of an object
  ```js
  "use strict";

  var districts = {};
  Object.defineProperty(districts, "noakhali", {
    value: "BIVAG",
    writable: false
  });
  districts.noakhali = "NOT BIVAG"; // TypeError: Cannot assign to read only property 'noakhali' of object '#<Object>'
  
  var districts = {
    get dhaka() {
      return "UNINHABITABLE";
    }
  };
  districts.dhaka = "INHABITABLE"; // TypeError: Cannot set property dhaka of #<Object> which has only a getter
  ```
* Some keyword are reserved by JS and can't be used as variable or function names like `eval`, `arguments`, `let` etc
* Some statements like `eval()`, `with()` etc is not allowed in the strict mode
> All of the examples pointed before does work fine in normal mode!
