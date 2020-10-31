---
title: assertFromMap
tags: unit test,jest,map,advanced
---

Unit testing with Jest and asserting values from a map match with what is expected.

- It's important that as developers we unit test our code, so this snippet shows an easy way to test a function with multiple scenarios but less lines of code.
- This is a sample unit test using `jest`. You need to have `jest` in your project to be able to run this test.
- `assertFromMap` receives the function to be tested and a map with different combinations.
- The map should be a map of `<input, expectedOutput>` input being what value you will give to the function and expectedOutput being what the function should return.

```js
const assertFromMap = (functionToTest, inputToExpectedOutput) =>
Object.keys(inputToExpectedOutput).forEach((input) => {
  const expectedOutput = inputToExpectedOutput[input]
  const functionReturn = functionToTest(input)

  expect(functionReturn).toEqual(expectedOutput)
})
```

You can use `assertFromMap` like this:

```js
// describe comes from jest
describe('isAFruit', () => {

  // test comes from jest
  test('should know what is a fruit and what is not', () => {

    // This function will probably be imported from another file
    const isAFruit = (fruit) =>
      fruit === 'Apple' || fruit === 'Banana' || fruit === 'Tomato'

    const inputToExpectedOutput = new Map()
    inputToExpectedOutput['Apple'] = true // is a fruit
    inputToExpectedOutput['Car'] = false // is not a fruit
    inputToExpectedOutput['JS'] = false // is not a fruit
    inputToExpectedOutput['Banana'] = true // is a fruit
    inputToExpectedOutput['Tomato'] = true // is a fruit

    // Calling our snippet
    assertFromMap(isAFruit, inputToExpectedOutput) // 'true' - tests will pass
  })
})
```

If you want to learn more about Jest find the documentation [here](https://jestjs.io/docs/en/getting-started).

You can have different functions and different combinations, feel free to play around.