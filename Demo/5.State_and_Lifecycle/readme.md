*** State and Lifecycle ***     

State is similar to props, but it is private and fully controlled by the component.

Converting a Function to a Class

    You can convert a function component like Clock to a class in five steps:

        1. Create an ES6 class, with the same name, that extends React.Component.
        2. Add a single empty method to it called render().
        3. Move the body of the function into the render() method.
        4. Replace props with this.props in the render() body.
        5. Delete the remaining empty function declaration.


Adding Lifecycle Methods to a Class

    In applications with many components, it’s very important to free up resources taken by the components when they are destroyed.

    We want to set up a timer whenever the Clock is rendered to the DOM for the first time. This is called “mounting” in React.

    We also want to clear that timer whenever the DOM produced by the Clock is removed. This is called “unmounting” in React.

    We can declare special methods on the component class to run some code when a component mounts and unmounts:

Now the clock ticks every second.

Let’s quickly recap what’s going on and the order in which the methods are called:

    1. When <Clock /> is passed to ReactDOM.render(), React calls the constructor of the Clock component. Since Clock needs to display the current time, it initializes this.state with an object including the current time. We will later update this state.
    2. React then calls the Clock component’s render() method. This is how React learns what should be displayed on the screen. React then updates the DOM to match the Clock’s render output.
    3. When the Clock output is inserted in the DOM, React calls the componentDidMount() lifecycle method. Inside it, the Clock component asks the browser to set up a timer to call the component’s tick() method once a second.
    4. Every second the browser calls the tick() method. Inside it, the Clock component schedules a UI update by calling setState() with an object containing the current time. Thanks to the setState() call, React knows the state has changed, and calls the render() method again to learn what should be on the screen. This time, this.state.date in the render() method will be different, and so the render output will include the updated time. React updates the DOM accordingly.
    5. If the Clock component is ever removed from the DOM, React calls the componentWillUnmount() lifecycle method so the timer is stopped.

The Data Flows Down 
    Neither parent nor child components can know if a certain component is stateful or stateless, and they shouldn’t care whether it is defined as a function or a class.

    This is why state is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it.

    This is commonly called a “top-down” or “unidirectional” data flow. Any state is always owned by some specific component, and any data or UI derived from that state can only affect components “below” them in the tree.

    If you imagine a component tree as a waterfall of props, each component’s state is like an additional water source that joins it at an arbitrary point but also flows down.

    To show that all components are truly isolated, we can create an App component that renders three <Clock>s:

    Each Clock sets up its own timer and updates independently.

    In React apps, whether a component is stateful or stateless is considered an implementation detail of the component that may change over time. You can use stateless components inside stateful components, and vice versa.s