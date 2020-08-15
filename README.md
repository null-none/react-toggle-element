# react-toggle-element

A stateless react component that toggles the display of it's children. It's like `ng-show`, `ng-hide` or `ng-if` but for react.

This allows you to DRY up statements like this:

```javascript
<div className={this.props.shouldHide ? 'hidden' : ''}>
```

Example usage:

```javascript
import React, { Component } from 'react';
import ToggleDisplay from 'react-toggle-element';

class App extends Component {
  constructor() {
    super();
    this.state = { show: false };
  }

  handleClick() {
    this.setState({
      show: !this.state.show
    });
  }

  render() {
    return (
      <div className="App">
        <p className="App-intro">
          <button onClick={ () => this.handleClick() }>Toggle things</button>
        </p>
        <ToggleDisplay show={this.state.show}>
          I am rendered in a span (by default) and hidden with display:none when show is false.
        </ToggleDisplay>

        <ToggleDisplay if={this.state.show} tag="section">
          I am rendered in a section and removed from the DOM when if is false.
        </ToggleDisplay>
      </div>
    );
  }
}

export default App;

```

## Props

`hide` - boolean

`show` - boolean

`if` - boolean

`tag` - string. The tag name to use as the ToggleDisplay element. Defaults to span.

The two first props are simply the inverse of each other. Using both at the same time will result in canceling each other out.


## Install

```
npm install react-toggle-element
```

## Tests

To run tests: `npm test`

