## Installation

1. Run `npm init @eslint/config`
2. Install the following:

```sh
npm install --save-dev eslint-plugin-prettier
npm install --save-dev eslint-config-prettier
npm install --save-dev --save-exact prettier
npm

```

3. Then you need to add `plugin:prettier/recommended` as the _last_ extension in your `.eslintrc.json`:

   ```json
   {
     "extends": ["plugin:prettier/recommended"]
   }
   ```

   You can then set Prettier's own options inside a `.prettierrc` file.

Exactly what does `plugin:prettier/recommended` do? Well, this is what it expands to:

```json
{
  "extends": ["prettier"],
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error",
    "arrow-body-style": "off",
    "prefer-arrow-callback": "off"
  }
}
```

- `"extends": ["prettier"]` enables the config from `eslint-config-prettier`, which turns off some ESLint rules that conflict with Prettier.
- `"plugins": ["prettier"]` registers this plugin.
- `"prettier/prettier": "error"` turns on the rule provided by this plugin, which runs Prettier from within ESLint.
- `"arrow-body-style": "off"` and `"prefer-arrow-callback": "off"` turns off two ESLint core rules that unfortunately are problematic with this plugin – see the next section.

## Sample Prettierrc Options

```json
{
  "semi": false,
  "trailingComma": "none",
  "singleQuote": true,
  "printWidth": 80
}
```

