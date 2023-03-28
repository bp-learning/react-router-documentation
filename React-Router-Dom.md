---
marp: true
footer: "![width:200px](./header_logo.png)"
math: mathjax
---

![bg width:800px](./react-router-logo.png)

---

# $~~~~~$ What is React Router DOM and why we use it?

- ## The React Router DOM is a package helps in implementing dynamic routing in web applications.
- ## The react-router-dom package contains bindings for using React Router in web applications.

- ## Create React App doesn't include page routing by default.

- ## To solve this problem of routing the most popular package is React Router DOM.

---

# $~~~~~$ How to add React Router DOM to your project?

- ## To add React Router in your application, run the below given command in the terminal from the root directory of the application.

- ## npm i react-router-dom

---

# $~$ How to update React Router DOM in your project?

- ## Use the below given command
- ## npm i react-router-dom@latest

---

# $~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~$ First Step

- ## We import BrowserRouter from react-router-dom and wrap our content with it.
- ## Then we use Routes. An application can have multiple Routes.
- ## We use Route to render specific component.
- ## Let's see it in our code

---

# Example

```
export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<div>Home Page</div>} />
        <Route path="about" element={<div>About Page</div>} />
        <Route path="contact" element={<div>Contact Page</div>} />
      </Routes>
    </BrowserRouter>
  );
}

```

---

- ## BrowserRouter - It is the parent component that is used to store all of the other components. Allowing the declaration of individual routes is the main functionality of using it.
- ## Routes - It renders a route exclusively as it displays the first child route that matches the current URL.
- ## Route - Route is the child component that renders a specific UI component when the URL matches the specified path.The path attribute specifies the path name we assign to the component and the element attribute refers to the component to render when the URL matches.

---

# $~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~$ Second Step

- ## Create separate Home, About, Contact, Error and Navbar Component.
- ## <Route>s can be nested. The first <Route> has a path of / and renders the Navbar component.
- ## The nested <Route>s inherit and add to the parent route. So the About path is combined with parent and becomes /about.
- ## If Route does not match any path mentioned in Route then we Render the Error Component.

---

# Example Code for Home, About, Contact, Error and Navbar Component

## Same code for About, Contact and Error Page

```
const Home = () => {
  return <h1>Welcome to Home Page</h1>;
};
export default Home;

```

---

```
import { Outlet, Link } from "react-router-dom";
const Navbar = () => {
  return (
    <>
      <nav>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/blogs">About</Link>
          </li>
          <li>
            <Link to="/contact">Contact</Link>
          </li>
        </ul>
      </nav>
      <Outlet />
    </>
  )
};
export default Navbar;
```

---

- ## Outlet - It should be used in parent route elements to render their child route elements. It renders the current route selected.
- ## Link - It is an element that lets the user navigate to another page by clicking or tapping on it. It is used to set the URL and keep track of browsing history.
- ## The "navbar route" is a shared component that inserts common content on all pages, such as a navigation menu.

---

```
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Layout from "./Navbar";
import Home from ".Home";
import About from "./About";
import Contact from "./Contact";
import Error from "./Error";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Navbar />}>
          <Route index element={<Home />} />
          <Route path="about" element={<About />} />
          <Route path="contact" element={<Contact />} />
          <Route path="*" element={<Error />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

---

- ## The Home component route does not have a path but has an index attribute. That specifies this route as the default route for the parent route, which is /. Index routes render into their parent's Outlet at their parent's URL
- ## Setting the path to \* will act as a catch-all for any undefined URLs.
- ## You've implemented react router dom in your React application. To explore more about React Router visit - https://reactrouter.com
