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

## Add the font

Grab the Roboto font [from here](https://fonts.google.com/specimen/Roboto) and
put the files in `src/assets/fonts/`

## Import the styles configuration into index.jsx

Now we need to import `uiConfig`, `normalize.scss` and `general.scss` in our `index.jsx`.
We'll also set the font related styles using our variables from `uiConfig`.

Your `index.jsx` should look like this:

```javascript
import React from 'react'
import ReactDOM from 'react-dom'
import { BrowserRouter } from 'react-router-dom'
import App from './App'
import * as serviceWorker from './serviceWorker'
import uiConfig from 'assets/styles/uiConfig'
import 'assets/styles/normalize.scss'
import 'assets/styles/general.scss'

ReactDOM.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>,
  document.getElementById('root')
)

const htmlEl = document.querySelector('html')
htmlEl.style.fontSize = uiConfig.font.responsiveSize

const bodyEl = document.querySelector('body')
bodyEl.style.fontSize = uiConfig.font.baseSize
bodyEl.style.fontWeight = uiConfig.font.mediumWeight
bodyEl.style.fontFamily = uiConfig.font.mainFamily

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister()
```

## Add UIGuide.jsx

Create a `UIGuide.jsx` file under `src/containers`, we'll use this file to showcase and
develop all of the ui components.

`UIGuide.jsx`
```javascript
import React from 'react'
import styled from 'styled-components'
import Button from 'components/UI/Button'
import uiConfig from 'assets/styles/uiConfig'

const UIGuide = styled.div`
  width: 100%;
  padding: ${uiConfig.spaces.small};
  background: ${uiConfig.colors.primary.background};

  h1 {
    color: ${uiConfig.colors.primary.text};
    margin-bottom: ${uiConfig.spaces.small};
  }
`

export default () => {
  return (
    <UIGuide>
      <h1>Button</h1>
      <Button>Hello React!</Button>
    </UIGuide>
  )
}
```

## Add a route for UIGuide.jsx

Now we need a route for our `UIGuide.jsx`.

Your `App.jsx` file should look like this:

```javascript
import React from 'react'
import {
  Route,
  Switch,
  Redirect
} from 'react-router-dom'
import styled from 'styled-components'
import UIGuide from 'containers/UIGuide'

const App = styled.div`
  display: flex;
  height: 100vh;
  overflow-y: auto;  
`

export default function () {
  return (
    <App>
      <Switch>
        <Route path="/" exact component={UIGuide} />
        <Redirect to="/" />
      </Switch>
    </App>
  )
}
```

---

If you now start you local server with `npm start` your browser should show
this:

<img src="https://firebasestorage.googleapis.com/v0/b/devsarmico-portfolio.appspot.com/o/Screenshot-from-2020-05-03-17-38-31-compressor.png?alt=media&token=bbba064e-1691-4f65-8f27-7f7ccc988977" style="object-fit:contain; border-radius: 4px;">