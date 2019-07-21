---
layout: post
title: "React tips"
---

## Basics

1. npm (node package manager):

    ```sh
    npm init -y # Initialize the package.json file, which contains all the dependencies
    npm install react react-dom
    ```

    ```sh
    npm install -g <package> # Globally
    npm install --save-dev <package> # Package only used in the development environment
    ```

    ```sh
    npm install -g create-react-app
    create-react-app <app-name> # Beginner friendly
    ```

2. Get the content of the variables by surrounding the them with curly braces.

3. In ES6, use `const` instead of `let` or `var` whenever we can.

4. Hot Module Replacement (No more refreshing, only reloading)

    ```javascript
    // src/index.js
    ...
    if (module.hot) {
        module.hot.accept();
    }
    ```

5. Example

    ```jsx
    class ShoppingList extends React.Component {
      render() {
        return (
          <div className="shopping-list">
            <h1>Shopping List for {this.props.name}</h1>
            <ul>
              <li>Instagram</li>
              <li>WhatsApp</li>
              <li>Oculus</li>
            </ul>
          </div>
        );
      }
    }
    // props is short for properties
    // Example usage: <ShoppingList name="Mark" /> (encapsulated and reusable)
    ```

## References

* [The Road to Learn React](https://www.amazon.com/Road-learn-React-pragmatic-React-js/dp/172004399X/ref=sr_1_1?keywords=the+road+to+react&qid=1563684290&s=gateway&sr=8-1)
* <https://reactjs.org/tutorial/tutorial.html>
