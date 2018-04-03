# To setup eslint

Create
+ .eslintignore

```shell
packages
node_modules
```

+ .eslintrc
```json
{
	"parser": "babel-eslint",
	"parserOptions": {
		"allowImportExportEverywhere": true
	},
	"plugins": [
		"meteor",
		"security"
	],
	"extends": [
		"plugin:security/recommended",
		"eslint:recommended",
		"airbnb",
		"@meteorjs/eslint-config-meteor"
	],
	"settings": {
		"import/resolver": "meteor"
	},
	"rules": {
		"security/detect-object-injection": "off",
		"security/detect-non-literal-fs-filename": "off",
		"security/detect-non-literal-regexp": "off",
		"security/detect-unsafe-regex": "off",
		"no-undef": "error",
		"no-implicit-globals":"error",
		"no-restricted-globals": "off",
		"object-curly-newline": "off",
		"no-control-regex": "off",
		"prefer-destructuring": "off",
		"no-unused-vars": "off",
		"camelcase": "off",
		"no-useless-escape": "off",
		"consistent-return": "off",
		"no-extra-boolean-cast": "off",
		"spaced-comment": "off",
		"no-loop-func": "off",
		"no-restricted-properties": "off",
		"new-cap": "off",
		"indent": [
			"error",
			"tab",
			{
				"ArrayExpression": 1,
				"ObjectExpression": 1
			}
		],
		"no-mixed-spaces-and-tabs": [
			"error",
			"smart-tabs"
		],
		"semi": [
			"error",
			"always"
		],
		"brace-style": "off",
		"key-spacing": "off",
		"no-new-func": "off",
		"no-plusplus": "off",
		"no-global-assign": "off",
		"no-param-reassign": "off",
		"prefer-arrow-callback": "off",
		"prefer-template": "off",
		"no-template-curly-in-string": "off",
		"default-case": "off",
		"max-len": ["off"],
		"comma-dangle": "off",
		"no-else-return": "off",
		"no-trailing-spaces": ["error", { "skipBlankLines": true }],
		"no-multi-spaces": [
			"error",
			{
				"exceptions": {
					"BinaryExpression": true,
					"VariableDeclarator": true,
					"ImportDeclaration": true
				}
			}
		],
		"no-underscore-dangle": "off",
		"eqeqeq": "off",
		"space-infix-ops": "error",
		"no-lonely-if": "error",
		"no-tabs": "off",
		"no-extra-semi": "error",
		"no-prototype-builtins": "off",
		"meteor/no-session": "off",
		"no-console": "off",
		"radix": [
			"error",
			"as-needed"
		],
		"meteor/template-names": "off",
		"meteor/eventmap-params": "off"
	},
	"env": {
		"browser": true,
		"node": true,
		"meteor": true
	}
}
```

+ In the package.json

```json
"devDependencies": {
		"@meteorjs/eslint-config-meteor": "^1.0.5",
		"babel-core": "^6.26.0",
		"babel-eslint": "^8.2.2",
		"babel-jest": "^22.0.4",
		"babel-preset-env": "^1.6.1",
		"eslint": "^4.18.0",
		"eslint-config-airbnb": "^16.1.0",
		"eslint-import-resolver-meteor": "^0.4.0",
		"eslint-plugin-import": "^2.8.0",
		"eslint-plugin-jsx-a11y": "^6.0.3",
		"eslint-plugin-meteor": "^4.2.0",
		"eslint-plugin-react": "^7.7.0",
		"eslint-plugin-security": "^1.4.0",
	}
```

+ In VSCODE download

![eslint](https://vscode-doc-jp.github.io/docs/nodejs/images/reactjs/eslint-extension.png)
