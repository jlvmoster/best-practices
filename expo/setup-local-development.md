# How to Setup Your Local Environment for Expo React Native Projects

> At the time of writing, `Expo v50` is the current major version...

## Install ESlint and Prettier for Expo

Following this [documentation](https://docs.expo.dev/guides/using-eslint/), run the command below:

```
npm i -D eslint prettier eslint-config-universe
```

## Create an ESLint config file called `.eslintrc.js` in the project root

```javascript
module.exports = {
  root: true,
  extends: [
    'universe/native',
  ],
  rules: {
    // Ensures props and state inside functions are always up-to-date
    'react-hooks/exhaustive-deps': 'warn',
  },
};
```

## ESLint is slow? Add an `.eslintignore` file

```
.expo
node_modules
```

## Install and Configure `prettier`, `husky`, and `lint-staged`

To setup automatic style formatting on a pre-commit hook, first install the required packages as `devDependencies`:

```
npm i -D husky lint-staged
```

### Prettier

Then create a `.prettierrc.json` file with your preferred styling rules. Here's mine:

```json
{
  "arrowParens": "avoid",
  "bracketSpacing": true,
  "endOfLine": "auto",
  "jsxSingleQuote": true,
  "printWidth": 80,
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5"
}
```

Create a `.prettierignore` to exclude unneeded files (if necessary):
```
.expo
.idea
node_modules
package-lock.json
```

### Husky and Lint-Staged

To setup pre-commit on staged files, first setup a lint-staged script in `package.json` to run prettier on all specified files:

```
{
  ...
  "lint-staged": {
    "*.{js,ts,jsx,tsx}": [
      "eslint --fix",
      "prettier --write"
    ],
    "*.{html,css,json,yml,yaml,md,mdx}": [
      "prettier --write"
    ]
  }
  ...
}
```

Next, setup husky to install a pre-commit hook on `npm install` by adding an `npm prepare` script:

```
npm pkg set scripts.prepare="husky"
```

Run husky init

```
npx husky init
```

Set pre-commit hook

```
echo "lint-staged" > .husky/pre-commit
```
