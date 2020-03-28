# Structuring React Apps: Get Started

# Chapter 1: Enforcing format rules

The're only two sides of this coin, you either:

* Don't care at all mixing single quotes with duoble ones, 

  adding semicolons whenever you feel like it, adding spaces in a completely random manner, 
  declaring variables that will never be used and
  can't stand the editor highliting in red tiny errors.

**OR**

* Think that code is meant to be read by people and therefore anything that can be

  added to improve its readability is 100% worth it. You also think that having consistency
  in how the code is presented adds in quality.

No matter which side you're currently in, we'll go through the process of configuring some
tools that will handle formatting and linting. You'll see how easy it is to set up these tools and how helpful they're for development.

## Initialize a new react app

``` sh
npx create-react-app my-app
```

## Configure Eslint

> Remember to install the VS code extension [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

We'll need the following dependencies to configure eslint:

``` sh
npm i --save-dev eslint eslint-config-react-app eslint-config-standard eslint-config-standard-react eslint-loader eslint-plugin-flowtype eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-node eslint-plugin-promise eslint-plugin-react eslint-plugin-standard babel-eslint eslint-plugin-react-hooks typescript
```

After installing those dependencies, go to your package.json and make sure that the field `eslintConfig` looks like this:

``` json
"eslintConfig": {
    "extends": [
      "react-app",
      "standard"
    ],
    "settings": {
			"react": {
				"version": "999.999.999"
			}
		}
  }
```

> The react version set to 999.999.999 fixes [this issue](https://github.com/DRD4-7R/eslint-config-7r-building/issues/1)

Lets now add a vscode settings file to have linting and autoformatting.
Create a folder and name it `.vscode` , inside that folder place the following file:

`settings.json` 

``` json
{
  "javascript.format.insertSpaceBeforeFunctionParenthesis": true,
  "[javascript]": { "editor.defaultFormatter": "dbaeumer.vscode-eslint" },
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "eslint.validate": [
    "javascript",
    "javascriptreact"
  ]
}
```

Let's test that our config is working as intended:

Go to `src/index.js` and hit `CTRL + S` . You should see how your semicolons `;` go away
automatically.

This happens because one of our formatting rules don't allow semicolons in our code and by saving the file an "action" is executed in vscode formatting the file automatically.

## Configure Husky

[Husky](https://github.com/typicode/husky) is a tool that lets you run npm commands upon a git actions (E.g.commit, push).

As an extra security layer we're going to make sure that all of our files are formatted before
being commited.

First add the following `script` to your package.json:

``` json
"scripts": {
  "lint": "eslint . --ext .js,.jsx --fix"
}
```

Then install husky:

``` sh
npm install husky --save-dev
```

Last add the husky configuration to your package.json:

``` json
"husky": {
  "hooks": {
    "pre-commit": "npm run lint"
  }
}
```

This config will execute `npm run lint` whenever you do a `git commit` , this way
we guarantee that our code will always be perfectly formatted.