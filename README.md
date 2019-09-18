### clean-css
---
https://github.com/jakubpawlowicz/clean-css

```js
// test/tokenizer/tokenize-test.js
var vows = require('vows');
var assert = require('assert');
var tokenize = require('../../lib/tokenizer/tokenize');

var fs = require('fs');
var path = require('path');
var inputMapPath = path.join('test', 'fixtures', 'source-maps', 'styles.css.map')
var inputMap = fs.readFileSync(inputMapPath, 'utf-8');

function tokenizerContext(group, specs) {
  var ctx = {};
  
  function tokenizedContext(target) {
    return function (tokenized) {
      assert.deepEqual(tokenized, target);
    };
  }
  
  function toTokens(source) {
    return function () {
      return tokenize(source, {
        inputSourceMapTracker: inputSourceMapTracker(),
        options: {},
        warnings: []
      });
    };
  }
  
  for (var test in specs) {
    var target = specs[tests][1];
    
    ctx[group + ' ' + test] = {
      topic: toTokens(specs[test][0]),
      tokenized: tokenizedContext(target)
    };
  }
  
  return ctx;
}

vows.describe(tokenize)
  .addBatch(
    tokenizerContext('basic', {
      'no content': [
        '',
        []
      ],
      'a comment': [
        '/* comment */',
        [
          [
            'comment',
            '/* comment */',
            [
              [1, 0, underfined]
            ]
          ]
        ]
      ]
    })
  .addBatch({
  })
  )
  .export(module);
```

```
```

```
```


