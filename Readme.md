# Assignment 9 - React

---

Q.1 What are hooks in react? how to identify hooks?

Ans. 1 Hooks are a feature introduced in React 16.8 that allow you to use state and other React features in functional components. They provide a way to reuse stateful logic without the need for class components.

You can identify hooks by their naming convention. Hooks start with the prefix "use", such as useState, useEffect, useContext, etc. Additionally, hooks can only be used directly within functional components or custom hooks. If a function uses hooks, it is considered a hook itself.

In summary, hooks are special functions in React that enable you to add state and other React features to functional components, providing a more concise and reusable way to manage component logic.

---

Q.2 Explain useState Hook & what can you achieve with it?

Ans.2 The useState hook is a built-in hook in React that allows functional components to manage state. It enables you to add stateful behavior to functional components without using class components.

With useState, you can achieve the following:

1. Declare state variables inside functional components.
2. Update the state and re-render the component when the state changes.
3. Access the current state value.

Here's a code example that demonstrates the usage of useState:

```jsx
import React, { useState } from "react";

const Counter = () => {
	const [count, setCount] = useState(0);

	const increment = () => {
		setCount(count + 1);
	};

	return (
		<div>
			<p>Count: {count}</p>
			<button onClick={increment}>Increment</button>
		</div>
	);
};
```

In this example, the useState hook is used to declare a state variable called `count` and a function called `setCount` to update the state. The initial value of `count` is set to 0. When the button is clicked, the `increment` function is called, which updates the state by incrementing the `count` value. The component re-renders with the updated count value.

---

Q.3 How to pass data from one component to another component?

Ans.3 In React, you can pass data from one component to another component using props. Props are a way to pass data from a parent component to a child component.

Here's a code example that demonstrates how to pass data from a parent component to a child component using props:

```jsx
import React from "react";

const ParentComponent = () => {
	const message = "Hello, child component!";

	return <ChildComponent message={message} />;
};

const ChildComponent = (props) => {
	return <p>{props.message}</p>;
};
```

In this example, the `ParentComponent` passes the `message` data as a prop to the `ChildComponent` by using the `message` attribute. The `ChildComponent` receives the prop as a parameter in its function signature (`props`) and can access the data using `props.message`. Finally, the `ChildComponent` renders the value of the `message` prop inside a paragraph element.

By passing props from parent to child components, you can share data and communicate between different parts of your React application.

---

Q.4 What is the significance of the "key" prop in React lists, and why is it important to use it correctly?

Ans.4 The "key" prop in React lists is used to give a unique identifier to each item in the list. It helps React efficiently update and re-render components when the list changes.

Using the "key" prop correctly is important for several reasons:

1. **Efficient updates**: React uses the "key" prop to determine which items have changed, been added, or been removed in a list. It allows React to update only the necessary components instead of re-rendering the entire list.

2. **Stable component identity**: The "key" prop ensures that each component in the list maintains its identity across re-renders. This helps React correctly reconcile and update the component state, event handlers, and any other associated data.

3. **Avoiding rendering errors**: Without a unique "key" prop, React may encounter rendering errors or warnings when reordering or removing list items. The "key" prop helps React accurately track and manage component instances.

Here's an example of using the "key" prop in a list of items:

```jsx
const MyComponent = () => {
	const items = ["apple", "banana", "orange"];

	return (
		<ul>
			{items.map((item, index) => (
				<li key={index}>{item}</li>
			))}
		</ul>
	);
};
```

In this example, the "key" prop is set to the `index` of each item. It provides a unique identifier for each list item, allowing React to efficiently update and render the list when changes occur.

By using the "key" prop correctly, you help React optimize the rendering process and ensure proper component identity and update behavior within lists.

---

Q.5 What is the significance of using "setState" instead of modifying state directly in React?

Ans.5 Using the "setState" method in React is significant because it ensures proper state management, triggers component re-rendering, and helps maintain a predictable application state.

The significance of using "setState" instead of modifying state directly can be summarized as follows:

1. **State immutability**: React enforces immutability of state, meaning you should not modify the state directly. Modifying state directly can lead to unexpected behavior and may not trigger component re-rendering. "setState" provides a safe and reliable way to update state in React.

2. **Batched updates**: React batches state updates performed with "setState" to improve performance. It intelligently groups multiple "setState" calls into a single update, reducing unnecessary re-renders and optimizing the rendering process.

3. **Async nature**: "setState" is asynchronous in nature. It allows React to optimize the rendering process by deferring state updates and performing them in batches. This ensures that the most up-to-date state is used during re-rendering and avoids potential inconsistencies.

Here's an example to illustrate the significance of using "setState" instead of modifying state directly:

```jsx
// Incorrect way: Modifying state directly
this.state = {
	count: 0,
};

// Directly modifying state
this.state.count = this.state.count + 1;

// Result: The component may not re-render, and the UI won't reflect the updated count.

// Correct way: Using setState
this.state = {
	count: 0,
};

// Using setState to update state
this.setState({ count: this.state.count + 1 });

// Result: The component will re-render, and the UI will reflect the updated count.
```

In the incorrect approach, modifying state directly may not trigger a component re-render, leading to an inconsistent UI state. The correct approach using "setState" ensures that the component re-renders properly and reflects the updated state.

By using "setState" correctly, you adhere to React's state management principles, promote component re-rendering when necessary, and maintain a predictable and reliable application state.

---

Q.6 Explain the concept of React fragments and when you should use them.

Ans.6 React Fragments provide a way to group multiple elements without adding an extra node to the DOM. They are useful when you need to return multiple elements from a component without a wrapping parent element.

Here's an example to illustrate the use of React Fragments:

```jsx
import React from "react";

const MyComponent = () => {
	return (
		<React.Fragment>
			<h1>Title</h1>
			<p>Paragraph 1</p>
			<p>Paragraph 2</p>
		</React.Fragment>
	);
};

export default MyComponent;
```

In this example, the `<React.Fragment>` tag acts as a wrapper for the multiple elements (`<h1>`, `<p>`, `<p>`) inside the component. It allows you to group them together without introducing an extra DOM element.

Using React Fragments is particularly useful when you want to return multiple elements from a component, but you don't want to add an unnecessary wrapper `<div>` or any other element. Fragments help keep the DOM structure clean and avoid introducing unnecessary styling or layout issues caused by an extra parent element.

You can also use the shorthand syntax `<>...</>` for React Fragments, which doesn't require importing `React`:

```jsx
const MyComponent = () => {
	return (
		<>
			<h1>Title</h1>
			<p>Paragraph 1</p>
			<p>Paragraph 2</p>
		</>
	);
};
```

Overall, React Fragments provide a lightweight and convenient way to group multiple elements without impacting the DOM structure, making your code cleaner and more efficient.

---

Q.7 How do you handle conditional rendering in React?

Ans.7 In React, conditional rendering is achieved by using JavaScript expressions or conditional statements to determine what content to render based on certain conditions.

Here's an example of conditional rendering in React:

```jsx
import React from "react";

const MyComponent = ({ isLoggedIn }) => {
	return (
		<div>{isLoggedIn ? <h1>Welcome, User!</h1> : <button>Login</button>}</div>
	);
};

export default MyComponent;
```

In this example, the `isLoggedIn` prop is used to conditionally render either a welcome message or a login button. If `isLoggedIn` is `true`, the `<h1>` element with the welcome message is rendered. Otherwise, the `<button>` element for login is rendered.

Conditional rendering can also be done using conditional statements, such as `if-else` or `switch` statements, within the component's `render` method. Additionally, you can use logical operators (`&&`, `||`) or ternary operators to conditionally render different components or elements based on specific conditions.

By leveraging conditional rendering, you can dynamically show or hide components, display different content based on user input or state, and create more interactive and responsive user interfaces in your React applications.

---

**Q.8** Create a Simple Todo Web App with following features Using React :

- An input button where users can type their tasks.
- On clicking the submit button, the entered task should be displayed in the UI.
- The UI layout should resemble the image provided.

Ans.8 [Source Code Link](https://github.com/yashPundhir/Todo_App_React)

---

**Q. 9** Expand the existing todo web app with two additional functionalities:

1. On clicking the "Update Status" button:
   - Update the status of the task.
2. On clicking the "Remove Todo" button:
   - Remove the selected todo from the UI.
   - Ensure that the deleted todo is no longer visible in the todo list.

Ans. 9 [Source Code Link](https://github.com/yashPundhir/Todo_App_React)

---

Q. 10 Build Calculator Web app using React, See below image for reference

Ans.10 [Source Code Link](https://github.com/yashPundhir/Calculator_App_Assignment)

---
