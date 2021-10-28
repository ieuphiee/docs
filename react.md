### What are some features of React?

- VirtualDOM
- Create reusable components
- Data flows in one direction

### How to create components in React?

Functional component:

```
function Button({ color }) {
    return <button />
}

// with arrow syntax
const Button = ({ color }) => <button/>
```

Class component:

```
class Button extends React.Component {
    constructor(props) {
        super(props)
        this.state = {
            name: "Jane Doe"
        }
        this.handleClick = this.handleClick.bind(this)
    }

    handleClick() {
        // click handler
    }

    render() {
        return <button/>
    }
}
```

### What is state?

The state of a component is an object that contains information that may change over the lifespan of the component. State is **internal** to the component and is controlled by the component itself. State can be **mutated** using the `this.setState()` function (class component).

### What are props?

Props are **inputs** to a component, data passed to a component by a parent component. Props are **external** and cannot be mutated.

### What is the purpose of callback function as an argument of `setState()`?

Is invoked after state has been updated and component has rerendered. **Since setState is asynchronous, this is useful for when you need to perform some type of action on updated state.** For example, if you wanted to print out the updated value of state after it has been updated...

```
this.setState({ name: "John Smith" }, () => console.log("component has rerendered"))
```

### What are refs? How are they used?

A ref is a reference to an element; they return the DOM node of that element.

(1) Attach a ref created using the `React.createRef()` function to the ref attribute of said element

```
class Component extends React.Component {
    constructor(props) {
        super(props)
        this.myRef = React.createRef()
    }

    render() {
        return <div ref={this.myRef}/>
    }
}
```

(2) Callback refs (class/functional components)

```
class Component extends React.Component {
    constructor(props) {
        super(props)
        this.myRef = null
        this.setMyRef = e => {
            this.myRef = e
        }
    }

    render() {
        return <div ref={this.setMyRef}/>
    }
}
```

### What is props.children?

Allows you to <b>pass components as data</b> to other components. Everything between the component's opening and closing tag will get passed to that component as `props.children`.

```
const Navigation = ({ children }) => {
    return <aside>{children}</aside>
}

<Navigation>
    <Button/>
    <Button/>
    </Button>
</Navigation>
```

### What are fragments?

A way to group multiple elements under one without adding extra nodes to the DOM.

### How are event handlers in React different?

- Event handler names are camelCase instead of lowercase
- In JSX, you pass a function as as the event handler, instead of a string

### What are the advantages of using React?

1. Lightweight - React is a library as compared to a framework like Angular which requires a steeper learning curve

2. Efficient - The concept of a Virtual DOM (which is a virtual representation of the DOM) allows the app to only apply the changes to the DOM where there's a difference instead of re-rendering the whole DOM

3. Can create reusable components - Pieces of reusable UI that can be shared across different pages or within other components, reduces amount of repeated code, and increases pace of development

### What is JSX?

Stands for Javascript XML, allows you to write HTML within Javascript

### Difference between functional and class components?

Functional – Javascript functions that can be declaring using the arrow symbol or the function keyword
Props: used like props.name, props.date, etc.
State: use the useState hook to instantiate and set state, hook returns an array, first element is the variable that holds the value of the state, second variable is the updater function to manipulate state
Class – declared using ES6 class
Props: used like this.props.name, this.props.date with the this keyword
State: instantiated within the constructor (this.state), update state using this.setState()

### What is the virtual DOM?

Virtual representation of the real DOM (essentially a lightweight copy of the DOM kept inside memory) and synced with real DOM by a library such as ReactDOM.

VirtualDOM is how React manages to be so efficient whenever the virtual DOM gets updated, React compares the two DOMs and gets to know about which virtual DOM objects were updated.

After knowing which objects were updated, React renders only those objects inside the real DOM instead of rendering the complete real DOM.

### Differences between controlled and uncontrolled components?

| Controlled                                                                                                                   | Uncontrolled                                                             |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Value of the input is controlled via React                                                                                   | Value of the input is handled by the DOM itself, not controlled by React |
| Control the value of the input by connecting the element to state by setting its value attribute within the onchange handler | Use ref to access input value                                            |

### What are the different lifecycle methods?

Functions that React exposes to allow you to tap into certain lifecycle phases: Every React component (class-based) has “lifecycle” methods that we can tap (hook) into and perform some type of action. There are 3 main phases:

- Mounting
  - Constructor – set initial state
  - Getderivedstatefromprops – set state based on props received
  - Render – render the elements on the dom
  - Componentdidmount – after component has been rendered to the dom, network requests can be executed here
- Updating
  - Shouldcomponentupdate – when you receive updated props/state, lets React know if component’s output is affected by the newly received props or by state change
  - Render – re-render elements on the dom
  - Componentdidupdate – after component gets rerendered
- Unmounting
  - Componentwillunmount – right before component will unmount, clean up, unsubscribe to network calls, unattach event listeners

### Explain React Hooks

Were introduced in React v16.8, functions that allow us to tap “hook into” React state and lifecycle features within a functional component. CANNOT BE USED IN CLASS COMPONENTS.

### What are the different ways to style a React component?

Inline styling – using inline style attributes, value of “style” attribute must be an object
Stylesheet – create separate stylesheet, import it into component

### What are keys in React?

Special attribute that React needs when rendering list of elements
Keys are unique identifiers for elements so that when items in a list are added, removed, or rearranged, React knows QUICKLY which one was changed

### What is prop drilling?

A pattern in which there’s a need to pass data from a parent component to a child component somewhere deeply nested in the tree. To get the data from parent to a specific child component, we pass the data as props to the next component in the hierachy until we reach said child component. This is problematic because (1) components that otherwise are not aware of the data have access to the data, and (2) “middle-men” components have unnecessary props.

Remediate: use global state management, Context API or Redux

### What are HOCs?

Fucntion that takes in a component and returns a new component.

Why? When there’s a need to share common functionality.
