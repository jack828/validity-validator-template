# validity-validator-template

A template for bootstrapping validity style validators.

## Using this template

:warning: Make sure you delete this section before publishing! :warning:

1. Create your new EMPTY repo, matching the validity naming convention e.g. `validity-validate-foobar`
2. Clone down this repository to your new destination:
    `git clone git@github.com:jack828/validity-validator-template.git validity-validate-foobar`
3. Tell git that you want to use YOUR repo as `origin`:
    `git remote set-url origin git@github.com:jack828/validity-validator-template.git`
4. Push, and verify it's going to the right location.
5. Edit the validator provided in [index.js](./index.js), not forgetting to write [complete test cases](./test/validator.test.js)!
6. Update this README with your usage documentation, and [package.json](./package.json) fields as appropriate.
7. When ready, run `npm version {patch, minor, major}` and `npm publish`!
8. ???
9. Profit!

You can use any ES2016 feature, spread, rest, await, etc thanks to Babel!

## Installation

```
$ npm install validity-validator-template
$ yarn add validity-validator-template
```

## Usage

This is designed to be used with [Schemata](https://npmjs.org/package/schemata).

```javascript
const validator = require('validity-validator-template')
const schemata = require('schemata')
const schema = schemata({
  field: {
    type: String,
    validators: [validator]
  }
})

// Valid case
schema.validate(
  { field: 'foo-bar' },
  (error, errors) => {
    // errors = {}
  }
)

// Invalid case
schema.validate(
  { field: 'foo bar qux' },
  (error, errors) => {
    // errors = { field: 'Field must conform to my validator' }
  }
)
```

## API

### const validator = createValidator()

### validate(String:key, String:keyDisplayName, Object:object, Function:cb)

This is a [validity](https://npmjs.org/package/validity) compatible function, which in turn is
used by [schemata](https://npmjs.org/package/schemata) for schema validation.

The callback signature `cb(error, errorMessage)`.
- `error` is an `Error` object if something bad happened and `null` otherwise.
- `errorMessage` is a `String` if a validation error happened and `undefined` otherwise.
- Your `errorMessage` string should use `keyDisplayName`, i.e. `${keyDisplayName} must be ...`

## Author

[Jack Burgess](https://github.com/jack828)

## Licence
Licensed under [GNU GPLv3](https://opensource.org/licenses/GPL-3.0).
