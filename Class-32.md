# React router 

## Fast start 

    ---> in the terminal 

    ```
    npx create-react-app some-app-name
    cd some-app-name 
    
    npm install react-router-dom

    ```

We have two examples today, Basic routing and nested routing 

## Basic routeing 
we will have 3 pages to be handled by the router 
home , about , and users  and the links between them 

``` 
import React from 'react';
import{
    BrowserRouter as Router,
    Switch,
    Route,
    Link
} from "react-router-dom";

export default function App(){
    return (
        <Router>
            <div>
                <nav>
                    <ul>
                    <li>
                        <Link to="/">Home</Link>
                    </li>
                    <li>
                    <Link to="/about">About </Link>
                    </li>
                    <li>
                    <Link to "/users"> Users </Link>
                    </li>
                  </ul>
                </nav>



                {/* A <Switch> looks through its children <Route>s and
            renders the first one that matches the current URL. */}
    )
   <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/users">
            <Users />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
         );
    }

    function Home() {
    return <h2>Home</h2>;
    }

    function About() {
    return <h2>About</h2>;
    }

    function Users() {
    return <h2>Users</h2>;
    }
}

``` 



## Nested Routing 

This example shows how nested routing works. The route /topics loads the Topics component, which renders any further <Route>'s conditionally on the paths :id value.


```
import React from "react";
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link,
  useRouteMatch,
  useParams
} from "react-router-dom";

export default function App() {
  return (
    <Router>
      <div>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <Link to="/topics">Topics</Link>
          </li>
        </ul>

        <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/topics">
            <Topics />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function Topics() {
  let match = useRouteMatch();

  return (
    <div>
      <h2>Topics</h2>

      <ul>
        <li>
          <Link to={`${match.url}/components`}>Components</Link>
        </li>
        <li>
          <Link to={`${match.url}/props-v-state`}>
            Props v. State
          </Link>
        </li>
      </ul>

      {/* The Topics page has its own <Switch> with more routes
          that build on the /topics URL path. You can think of the
          2nd <Route> here as an "index" page for all topics, or
          the page that is shown when no topic is selected */}
      <Switch>
        <Route path={`${match.path}/:topicId`}>
          <Topic />
        </Route>
        <Route path={match.path}>
          <h3>Please select a topic.</h3>
        </Route>
      </Switch>
    </div>
  );
}

function Topic() {
  let { topicId } = useParams();
  return <h3>Requested topic ID: {topicId}</h3>;
}


```



Resource: https://reactrouter.com/web/guides/quick-start
