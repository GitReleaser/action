## bootstrapping

This a [JavaScript](https://help.github.com/en/articles/about-actions#types-of-actions) action but uses [TypeScript](https://www.typescriptlang.org/docs/home.html) to generate that JavaScript.

You can bootstrap your environment with a modern version of npm and by running `npm i` at the root of this repo.

## testing

Tests can be found under under `__tests__` directory and are runnable with the `npm t` command.

## source code

Source code can be found under the `src` directory. Running `npm run build` will generate the JavaScript that will run within GitHub workflows.

## formatting

A minimal attempt at keeping a consistent code style is can be applied by running `npm run fmt`.

## contributing to alignAssetName function

The `alignAssetName` function is used to replace spaces with dots in asset names. This is useful when uploading assets to GitHub releases, as GitHub may rename asset filenames that have special characters, non-alphanumeric characters, and leading or trailing periods.

### Example

```javascript
const { alignAssetName } = require('./util');

const assetName = "John Doe.bla";
const alignedName = alignAssetName(assetName);

console.log(alignedName); // Output: John.Doe.bla
```

### Testing

To test the `alignAssetName` function, add your test cases in the `__tests__/util.test.ts` file. Here is an example of how to test the function:

```javascript
describe("alignAssetName", () => {
  it("replaces all spaces with dots", () => {
    expect(alignAssetName("John Doe.bla")).toBe("John.Doe.bla");
  });

  it("handles names with multiple spaces", () => {
    expect(alignAssetName("John William Doe.bla")).toBe("John.William.Doe.bla");
  });

  it("returns the same string if there are no spaces", () => {
    expect(alignAssetName("JohnDoe")).toBe("JohnDoe");
  });
});
```
