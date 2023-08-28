---
title: ESlint config
date: 2023-08-27
author: Dmitry
description: My eslint config
math: true
tags:
  - vscode
  - workspace
  - eslint
---

Let's do it

```js
npm i -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

Create new file  `.eslintrc`
```json
{
	"root": true,
	"parser": "@typescript-eslint/parser",
	"plugins": [
		"@typescript-eslint"
	],
	"rules": {
		"semi": "on",
		"@typescript-eslint/semi": [
			"warn"
		],
		"@typescript-eslint/no-empty-interface": [
			"error",
			{
				"allowSingleExtends": true
			}
		]
	},
	"extends": [
		"eslint:recommended",
		"plugin:@typescript-eslint/eslint-recommended",
		"plugin:@typescript-eslint/recommended"
	]
}
```