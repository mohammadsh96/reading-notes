# Hooks and Context
[back to main ](./README.md)
## context behavior 

- Context is like a global variable - or a global Hook - that's passed to every child. Context is a component that wraps around any other component. Every child component has access to it without being passed around through props. There are four steps to using context:
```
-Initiate context
-Provide the initiated context
-Implement context in our app
-Update context in our app
```
- We're going to have an app that renders two components, one for authorized users and one for unauthorized users. This is the file structure:
```
1.index.js
2.App.js
3.UserContext.js
4.AuthApp.js
5.UnauthApp.js
```
- That looks like a lot! Don't worry, I also created a CodePen with everything condensed into one file. It's 75 lines of code, including whitespace.

**Step One: Initiate Context**

- Initiating context is super easy. We create a variable and set it to createContext(). We're going to set it to a default "fallback" value. If we left it blank, it would default to an empty object, which is okay too.
- 
```js
const UserContext = createContext({ name: '', auth: false });
// This also works: const UserContext = createContext();
```
**Step Two: Provide Context**

- Creating a function to provide our initiated context is the most complicated part.

- We're going to call a provider function with children as a prop. This function will be the parent of every other component in our app. This allows us to provide any method we create within the provider function to any other component.
```js
const UserProvider = ({ children }) => {
  return (
    <UserContext.Provider value={{ user, login, logout }}>
      {children}
    </UserContext.Provider>
  );
}
```
- We're creating a function that provides our newly initiated context to every child component. You probably are wondering where the value prop with user, login and logout is coming from. Those are the methods that will be accessible to any child component.

`Let's create them:`

```js
const UserProvider = ({ children }) => {
  // User is the name of the "data" that gets stored in context
  const [user, setUser] = useState({ name: '', auth: true });

  // Login updates the user data with a name parameter
  const login = (name) => {
    setUser((user) => ({
      name: name,
      auth: true,
    }));
  };

  // Logout updates the user data to default
  const logout = () => {
    setUser((user) => ({
      name: '',
      auth: false,
    }));
  };

  return (
    <UserContext.Provider value={{ user, login, logout }}>
      {children}
    </UserContext.Provider>
  );
}
```
**Step Three: Implement Context in our App**

- Remember, context is a global variable. So we need to implement it as the highest level in our app, i.e. where React renders our app.
```js
import React from 'react';
import ReactDOM from 'react-dom';
import { UserProvider } from './UserContext';
import App from './App';

ReactDOM.render(
    <UserProvider>
      <App />
    </UserProvider>
  document.getElementById('root')
);
```
**Step Four: Update Context**

- From here on out, we're going to be consuming context (i.e. using and updating it). Using context just requires importing it and calling it! In App.js, we import it as well as authenticated and unauthenticated components.
```js
import React, { useContext } from 'react';
import { UserContext } from './UserContext';
import AuthApp from './AuthApp';
import UnauthApp from './UnauthApp';

function App() {
  const { user } = useContext(UserContext);

  return user.auth ? <AuthApp /> : <UnauthApp />;
}

export default App;
```
- We simply import user context. Then because it's an object, we can access the auth property. Then we use a ternary operator (fancy if statement) to either return <AuthApp /> or <UnauthApp />.

- `AuthApp.js `and `UnauthApp.js` similarly import the user context, and also methods to update the user context.

 - `AuthApp.js`
```js
import React, { useContext } from 'react';
import { UserContext } from './UserContext';

function AuthApp() {
  const { user, logout } = useContext(UserContext);

  return (
    <>
      <h1>Hello, {user.name}!</h1>
      <button onClick={logout}>Logout</button>
    </>
  );
}

export default AuthApp;
UnauthApp.js
import React, { useContext, useState } from 'react';
import { UserContext } from './UserContext';

function UnauthApp() {
  const { login } = useContext(UserContext);
  const [name, setName] = useState();

  return (
    <>
      <h1>Please, log in!</h1>

      <label>Name:</label>
      <input
        type="text"
        onChange={(event) => {
          setName(event.target.value);
        }}
      />
      <button onClick={() => login(name)}>Log in</button>
    </>
  );
}

export default UnauthApp;
```