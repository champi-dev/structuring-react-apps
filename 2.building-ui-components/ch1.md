# Structuring React Apps: Building UI Components

# Chapter 1: UI Configuration

Let's install [styled components](https://styled-components.com/) and [react router](https://reacttraining.com/react-router/web/guides/quick-start) right away:

```sh
npm i styled-components react-router-dom
```

## Add a uiConfig.js file

This file holds the most important information about our ui such as:

* Which font to use
* Colors
* Spaces
* Breakpoints

Create the folder `src/assets/styles/` and add:

`uiConfig.js`
```javascript
const config = {
  font: {
    mainFamily: 'Roboto, sans-serif',
    responsiveSize: '62.5%',
    baseSize: '1.6rem',
    mediumWeight: 400,
    fatWeight: 700
  },
  colors: {
    primary: {
      action: '#f600fa',
      background: '#1A1B1F',
      text: '#FFFFFF'
    },
    secondary: {
      text: '#5D6C76'
    },
    feedback: {
      success: '#00E65A',
      error: '#FF0000'
    }
  },
  spaces: {
    xxsmall: '0.4rem',
    xsmall: '0.8rem',
    small: '1.2rem',
    medium: '1.6rem',
    large: '2rem',
    xlarge: '2.4rem',
    xxlarge: '4rem',
    xxxlarge: '5.6rem',
    huge: '7.2rem'
  },
  breakpoints: {
    mobile: '375px',
    desktop: '1440px'
  }
}

export default config
```

## Add a normalize.scss file

In case you're not familiar with this go ahead and visit [this link](https://necolas.github.io/normalize.css/).
Download it and go to `src/assets/styles/` and add it with the .scss extension.

> We rename the file from .css to .scss to be consistent, it's recommended but not necessary

## Add a general.scss file

This file holds global css styles for the app.
We'll use it to remove some margins that are applied by default
(and not resseted with normalize) and to set our font.

> We'll add the Roboto font files in a bit

Go to `src/assets/styles/` and add:

`general.scss`
```scss
@font-face {
	font-family: "Roboto";
	font-style: normal;
	src: url("../fonts/Roboto-Black.ttf") format("ttf"),
  url("../fonts/Roboto-BlackItalic.ttf") format("ttf"),
  url("../fonts/Roboto-Bold.ttf") format("ttf"),
  url("../fonts/Roboto-BoldItalic.ttf") format("ttf"),
  url("../fonts/Roboto-Italic.ttf") format("ttf"),
  url("../fonts/Roboto-Light.ttf") format("ttf"),
  url("../fonts/Roboto-LightItalic.ttf") format("ttf"),
  url("../fonts/Roboto-Medium.ttf") format("ttf"),
  url("../fonts/Roboto-MediumItalic.ttf") format("ttf"),
  url("../fonts/Roboto-Regular.ttf") format("ttf"),
  url("../fonts/Roboto-Thin.ttf") format("ttf"),
  url("../fonts/Roboto-ThinItalic.ttf") format("ttf");
}

h1, h2, h3, h4, p {
  margin: unset;
}

p, label, span, button {
  font-size: inherit;
  font-weight: inherit;
}
```

```
/* 
  TODO: Writing for article

  styled components | react router
  .js file with color variables 
  App general styles
  Add font *
  Components showcase page 

  rafce (shortcut)
  https://github.com/airbnb/javascript/issues/1235 (good info)
*/
```