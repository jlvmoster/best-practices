# How to Setup Your Local Environment for React Projects


## Install and Configure `prettier`, `husky`, and `lint-staged`

To setup automatic style formatting on a pre-commit hook, first install the required packages as `devDependencies`:

```
npm i -D prettier husky lint-staged
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
.cache
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

(optional) Setup a `.lintstagedrc.js` file for `Next.js` projects to utilize the `next lint` command:

```javascript
const path = require('path')

const buildEslintCommand = (filenames) =>
  `next lint --fix --file ${filenames
    .map((f) => path.relative(process.cwd(), f))
    .join(' --file ')}`

module.exports = {
  '*.{js,ts,jsx,tsx}': [buildEslintCommand, 'prettier --write'],
  '*.{html,css,json,yml,yaml,md,mdx}': ['prettier --write'],
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
echo "npx lint-staged" > .husky/pre-commit
```

## (Optional) Setup Eslint

Install the react app eslint config package

```
npm i -D eslint-config-react-app eslint-config-prettier
```

In your `package.json` or a separate `.eslintrc.json`, setup your linting rules:

### package.json

```
{
  ...
  "eslintConfig": {
    "globals": {
      "__PATH_PREFIX__": true
    },
    "extends": ["react-app", "prettier"],
    "rules": {
      "react/jsx-pascal-case": "off"
    }
  },
  ...
}
```

### .eslintrc.json

```json
{
  "globals": {
    "__PATH_PREFIX__": true
  },
  "extends": ["react-app", "prettier"],
  "rules": {
    "react/jsx-pascal-case": "off"
  }
}
```

Create a `.eslintignore` to exclude unneeded files (if necessary):
```
node_modules
```
