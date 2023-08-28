---
title: Stylelint config
date: 2023-08-28
author: Dmitry
description: My faforite stylelint config
math: true
tags:
  - vscode
  - workspace
  - styles
  - css
  - scss
---

Let's do it

```js
npm i -D stylelint stylelint-order stylelint-order-config-standard stylelint-config-standard
```

Create new file  `.stylelintrc.json`
```json
{
	"extends": [
		"stylelint-config-standard",
		"stylelint-order-config-standard"
	],
	"plugins": [
		"stylelint-order"
	],
	"rules": {
		"indentation": [
			"tab"
		],
		"color-hex-case": "upper"
	}
}
```

Then add new line in `./package.json` 

```json
"stylelint": "stylelint \"**/*.css\" --fix"
```

