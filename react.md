# React Toolbox

## Recipes

## Prototyping

[Storybook](https://storybook.js.org/) makes it easy to start writing React components.

## Updating state

### When the state depends on the previous state

React's `setState()` is asynchronous, so you can't expect `this.state` to contain the latest values when your new state is evaluated. As such, the pattern to use here is:

```js
this.setState(
  previous_state => {
    return {
      value: previous_state.value + 1
    }
  }
)
```

It might be that your new value is the same as the previous value. Starting with React 16, within the function that returns the new state, you can return `null` to prevent the state from updating.

### Refactoring the `setState()` callback

There's one style of `setState()` in React wherein you provide a callback function to execute after the state has been updated:

```js
this.setState(newState, callback);
```

However, notifying parent components in this callback that the state has changed is an anti-pattern that negates the performance benefits of React's batching of `setState()` calls, causing you callback to be called much more frequently than the state actually updates.

Instead, use the `componentDidUpdate` lifecycle method to notify the part that a particular value in the state has changed:

```js

someAction() {
  this.setState({ value: 'somevalue' });
}

componentDidUpdate(previous_props, previous_state) {
  if (this.state.value !== previous_state.value) {
    this.props.onChange(this.state.value);
  }
}
```

## Performance

### Checking for unnecessary renders

Set up [why-did-you-update](https://github.com/maicki/why-did-you-update) to have it notify you in the console if any of your React components are rendering unnecessarily.

### PureComponents vs. this.props.children

If your component receives arbitrary children from outside the component, they will update more often than you'd like. `why-did-you-update` will report unnecessary renders. 

Given this, it might be that using `PureComponent` on any component that renders arbitrary children is an anti-pattern.
