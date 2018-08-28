# Create protected routes using React Router

In Angular, we can create protected routes using AuthGuard. Now that I am creating a project in react, I want to do the same in React using React Router v4.

The idea is, we create a Higher Order Component which internally uses route and redirect based on the state of login.

```javascript
{% raw %}
import { Route, Redirect } from "react-router-dom";
// this also works with react-router-native

const PrivateRoute = ({ component: Component, ...rest }) => (
  <Route
    {...rest}
    render={props =>
      props.isLoggedIn === true ? (
        <Component {...props} />
      ) : (
        <Redirect
          to={{
            pathname: "/",
            state: { from: props.location }
          }}
        />
      )
    }
  />
);
{% endraw %}
```

### How to use it,

```javascript
let isLoggedIn = false;

<PrivateRoute
  isLoggedIn={isLoggedIn}
  path="/editList/:id"
  component={EditList}
/>;
```

    In my case, I had created a separate file for all the routes that has a connection with Redux store. this redux store tells me wether user is logged in or not.

For more information, check this article on [Medium here](https://medium.com/wineofbits/how-to-create-private-protected-route-in-react-router-v4-89cf29187a5d).
