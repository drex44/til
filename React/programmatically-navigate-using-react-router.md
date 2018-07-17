# Programmatically navigate using React Router

When using React Router, there can be a need to navigate programatically on some event. It can be achieved by three ways. But the easiest way I found is by using withRouter HOC.

The withRouter higher-order component will inject the history object as a prop of the component. This allows you to access the push and replace methods without having to deal with the context.
```javascript
import { withRouter } from 'react-router-dom'
// this also works with react-router-native

const Button = withRouter(({ history }) => (
  <button
    type='button'
    onClick={() => { history.push('/new-location') }}
  >
    Click Me!
  </button>
))
```
For other two methods, check this answer on [stackoverflow here](https://stackoverflow.com/a/42121109/5027712).
