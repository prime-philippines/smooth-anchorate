# smooth anchorate

> Smooth Scroll to anchor links.

Smooth Scroll to anchor links with client-side routes e.g. with [history]'s `listen`, [React Router]'s `onUpdate`, or [Gatsby]'s `onRouteChange`.
Register a listener to call this and when `window.location.hash` isn't empty,
it'll [scrollIntoView] first matching element by `id` or `name` per [spec].

Originally based on: https://github.com/reactjs/react-router/issues/394#issuecomment-220221604

## Install
```
npm install --save smooth-anchorate
```

## Use

### [history]
```js
import { smoothAnchorate } from 'smooth-anchorate'
import { createHistory } from 'history'
 
const history = createHistory()

history.listen(() => {
  smoothAnchorate()
})
```

### [React Router]
```js
import { smoothAnchorate } from 'smooth-anchorate'
import { render } from 'react-dom'
import { Router, browserHistory } from 'react-router'

function onUpdate () {
  smoothAnchorate()
}

// ...

render((
  <Router
    onUpdate={onUpdate}
    history={browserHistory}
  />
), document.getElementById('app'))
```

### [Gatsby]
In `gastby-browser.js`:
```js
import { smoothAnchorate } from 'smooth-anchorate'

exports.onRouteChange = () => {
  smoothAnchorate()
}
```

[react router]: https://github.com/reactjs/react-router
[history]: https://github.com/ReactJSTraining/history
[gatsby]: https://github.com/gatsbyjs/gatsby
[scrollIntoView]: https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollIntoView
[spec]: https://www.w3.org/TR/html4/struct/links.html#h-12.1.3
