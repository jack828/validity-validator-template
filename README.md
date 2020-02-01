# validity-validator-template

A template for bootstrapping validity style validators.

To use this template, edit this file with usage, update the tests, and write a validator in `index.js`.

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
