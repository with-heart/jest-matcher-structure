<h1 align="center">
  <br>
  <img width="400" src="./logo.png" alt="jest-matcher-structure">
  <br>
  <br>
</h1>

# jest-matcher-structure

> A custom `jest` matcher for validating object structures

## Install

`$ npm install --save-dev jest-matcher-structure`

## Usage

jest-matcher-structure walks key-by-key through a structure object and a comparison object and verifies that the value in the structure object accurately describes the value in the comparison object.

It's easy to get started! Here's a quick and simple example:

```javascript
import { toMatchStructure } from 'jest-matcher-structure'

expect.extend({ toMatchStructure })

test("structure matches object's structure", () => {
  const structure = {
    string: 'string',
    number: 'number',
    boolean: 'boolean',
    function: n => n > 5,
    literal: 'literal value',
    regex: /\d+/,
    null: null,
  }

  const object = {
    string: 'hello world',
    number: 123,
    boolean: true,
    function: 10,
    literal: 'literal value',
    regex: '1234',
    null: null,
  }

  expect(structure).toMatchStructure(object)
})
```

jest-matcher-structure also comes with two helper functions--`some` and `every`--for fields where you need to test the comparison value against multiple truths. You pass them an array and jest-matcher-structure works its magic! Here's an example:

```javascript
import { some, every, toMatchStructure } from 'jest-matcher-structure'

test('some and every', () => {
  const structure = {
    field1: some(['A', 'B']),
    field2: every(['string', x => x >= 1200 && x <= 1500]),
  }

  const object = {
    field1: 'A',
    field2: '1300',
  }

  expect(structure).toMatchStructure(object)
})
```

## List of Comparisons

* literal value
* string type
* number type
* boolean type
* function
* regex
* `some`
* `every`
* ...and more to come!

## TODO

* Nested object comparison
* Array comparison

## Created By

* [Mark Chandler](http://github.com/lionize)

## License

MIT