# REACT NOTES

## JSX
JSX (JavaScript XML) is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file.

## Rules of JSX
+ Return a single root element. Wrap all elements in div element `<div></div>` or use fragment `<></>`
+ Close all tags explicitly.
+ Use camelCase for most of the things like props.

## JS in JSX markup
+ Use anywhere as text in markup: `<h1>{name}'s To Do List</h1><h1>{name}'s To Do List</h1>`
+ Use in props: `src={avatar}`
+ To pass object use double curly brackets: `person={{ name: "Hedy Lamarr", inventions: 5 }}`

## Conditional Rendering
+ Ternary operator: `condition ? true : false`
+ Logical AND operator: `condition && true`

## Rendering List
+ `map()` can be used to map JS variable to create element.
+ `filter()` can be used to filter array.
+ Provide unique `key` to each list item. For local data use `crypto.randomUUID()`.

## Component:
React component is a JavaScript function that you can sprinkle with markup. Name of the component always starts with a `Captial Letter`. Never define a component inside another component. These functions are pure functions which means for an input it should always return same output.

### Example of a Component
You can use markup with JavaScript code:
```
function Profile() {
  return (
    <img />
  );
}

export default function Gallery() {
  return (
    <section>
      <h1>Amazing scientists</h1>
      <Profile />
      <Profile />
      <Profile />
    </section>
  );
}
```

## Exporting the Component
+ Default Export: We can only have 1 default export in a file. Syntax to export: `export default function Test()`. Syntax to import: `import Test from './Test'`
+ Named Export: We can have multiple named exports in one file. While importing name have to match the exact name of the exported component. Syntax to export: `export function Test()`. Syntax to import: `import { Test } from './Test'`

## Component Render
+ Initial render
+ Component's or its ancestors' state has been updated.
+ In development enviornment component is remounted after initial mount to help catch errors like if we forgot to close connection.

## Component Props
Props are the information that you pass to a JSX tag.
+ Pass props like this: `<Avatar person={{ name: 'Hamza' }} size={100} />`
+ React component functions accept a single argument, a `props` object. Accept props like this: `function Avatar({ person, size = 10 }) { }` or `function Avatar(props) { }`
+ Pass all props to child components: `<Avatar {...props} />`
+ Using `children` props key you can wrap component around child:
```
function Card({ children }) {
  return (
    <div className="card">
      {children}
    </div>
  );
}

export default function Profile() {
  return (
    <Card>
      <Avatar />
    </Card>
  );
}
```
+ props are immutable meaning `unchangeable`.

## Using props in Multiple Components
+ A method `lifting state up` can be used to move the state up the tree to a common parent. But in case of too deep tree and long distance between nodes it can lead to a situation called `prop drilling` which is handled by Context.

## Context
Context lets a parent component provide data to the entire tree below it. Steps to use it:
+ Create the context. We pass default value to `createContext()`.
```
import { createContext } from 'react';

export const LevelContext = createContext(1);
```
+ Import context from react and your new file
```
import { useContext } from 'react';
import { LevelContext } from './LevelContext.js';

const level = useContext(LevelContext);
```
+ Provide the context by wraping children into `<LevelContext value={level}>`

## Well Structured Context File
+ Create Context
+ Create Provider
+ Create context use functions
+ Create reducer function
+ Create initial state
```
import { createContext, useContext, useReducer } from 'react';

const TasksContext = createContext(null);

const TasksDispatchContext = createContext(null);

export function TasksProvider({ children }) {
  const [tasks, dispatch] = useReducer(
    tasksReducer,
    initialTasks
  );

  return (
    <TasksContext value={tasks}>
      <TasksDispatchContext value={dispatch}>
        {children}
      </TasksDispatchContext>
    </TasksContext>
  );
}

export function useTasks() {
  return useContext(TasksContext);
}

export function useTasksDispatch() {
  return useContext(TasksDispatchContext);
}

function tasksReducer(tasks, action) {
  switch (action.type) {
    case 'added': {
      return [...tasks, {
        id: action.id,
        text: action.text,
        done: false
      }];
    }
    case 'changed': {
      return tasks.map(t => {
        if (t.id === action.task.id) {
          return action.task;
        } else {
          return t;
        }
      });
    }
    case 'deleted': {
      return tasks.filter(t => t.id !== action.id);
    }
    default: {
      throw Error('Unknown action: ' + action.type);
    }
  }
}

const initialTasks = [
  { id: 0, text: 'Philosopher’s Path', done: true },
  { id: 1, text: 'Visit the temple', done: false },
  { id: 2, text: 'Drink matcha', done: false }
];
```

## Event Handlers
Event handlers are your own functions that will be triggered in response to user interactions like clicking, hovering, focusing on form inputs, and so on.
+ Pass function as prop to a JSX tag.
+ We can use passed props in event handler function.

## Event Propagation
+ If we have a `div` which contains a `button` and both have `onClick` handler if you click on button first button handler will be called then div handler will be called. We say that an event `propagates` up the tree: it starts with where the event happened, and then goes up the tree.
+ To stop propagation use `e.stopPropagation();` in your handler.
+ To stop default browser behavior of an event use `e.preventDefault()`

## Hooks
Hooks allow functions to have access to state and other React features without using classes. All functions starting with `use` are hooks like `useContext`, `useState`...

## State
Retain the data between renders. Trigger React to render the component with new data (re-rendering).

## Using State
+ Import `useState` function from `react` like `import { useState } from 'react';`
+ `const [variable, setVariable] = useState(value);` Here `useState(value)` will create a state variable with given value and return two items in array. At 0 index it will return the variable and at 1 index it will return setter function.

## Structuring States
+ **Group related states**. If you always update two or more state variables at the same time, consider merging them into a single state variable. 
+ **Avoid contradictions**. When the state is structured in a way that several pieces of state may contradict and “disagree” with each other, you leave room for mistakes. Try to avoid this.
+ **Avoid redundant state**. If you can calculate some information from the component’s props or its existing state variables during rendering, you should not put that information into that component’s state.
+ **Avoid duplicates**. When the same data is duplicated between multiple state variables, or within nested objects, it is difficult to keep them in sync. Reduce duplication when you can.
+ **Avoid deeply nested state**. Deeply hierarchical state is not very convenient to update. When possible, prefer to structure state in a flat way.

## Reducer
You can move state logic into a single function outside your component, called a `reducer`. Reducers are a different way to handle state. You can migrate from `useState` to `useReducer` in three steps:
+ Move from setting state to dispatching actions.
```
function handleAddTask(text) {
  setTasks([
    ...tasks,
    {
      id: nextId++,
      text: text,
      done: false,
    },
  ]);
}

function handleAddTask(text) {
  dispatch({
    type: 'added',
    id: nextId++,
    text: text,
  });
}
```
+ Write a reducer function.
```
function tasksReducer(tasks, action) {
  switch (action.type) {
    case 'added': {
      return [
        ...tasks,
        {
          id: action.id,
          text: action.text,
          done: false,
        },
      ];
    }
    default: {
      throw Error('Unknown action: ' + action.type);
    }
  }
}
```
+ Use the reducer from your component. First add reducer to component `import { useReducer } from 'react';`. Now replace `useState` with reducer like this `const [tasks, dispatch] = useReducer(tasksReducer, initialTasks);`.

## Referencing values using refs
When you want a component to `remember` some information, but you don’t want that information to trigger new renders, you can use a ref `const ref = useRef(0);`.
+ `useRef(0)` returns object like this `{ current: 0 // The value you passed to useRef }`.
+ Doesn’t trigger re-render when you change it.
+ Mutable you can modify and update current’s value outside of the rendering process.
+ You shouldn’t read (or write) the current value during rendering.

## Using ref with DOM node
You can then access this DOM node from your event handlers and use the built-in browser APIs defined on it.
+ `myRef.current.scrollIntoView();`
+ `myRef.current.focus();`
+ ref is set during the commit phase not the rendering phase.

## Effects
It allows you to perform side effects in your components. Effects are called after every render.

## Using Effect
Steps to use Effect:
+ `import { useEffect } from 'react';`
+ Put this function at top of component
```
function MyComponent() {
    useEffect(() => {
        // Code here will run after *every* render
    });
    return <div />;
}
```
+ We can pass dependency as 2nd parameter (array of dependencies) to `useEffect` function to skip Effect in case dependency is not changed.
+ Write a clean up code in `return () => {}`.

## Memo
Used to cache the calculation.
+ `useMemo(function, dependencies)`.