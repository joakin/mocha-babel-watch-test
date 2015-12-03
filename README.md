# mocha-babel-watch-test

Test repo to check mocha + babel when watching files.

Illustrates the bug https://github.com/mochajs/mocha/issues/1847

When requiring mocha functions to not use globals, watching doesn't work.

```sh
npm install

mocha-babel-watch-test $ mocha -w --compilers js:babel-register test.js

  Array
    #indexOf()
      ✓ should return -1 when the value is not present

  1 passing (82ms)

	# Modify the test.js file

  0 passing (0ms)
```

If you uncomment the mocha import line, the watcher works fine.

```js
// Comment this to have it work but use evil global variables
import { describe, it } from 'mocha'
```
