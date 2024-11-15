1. What do props help us accomplish?
   Make a component more reusable.

2. How do you pass a prop into a component?
   <MyAwesomeHeader title="???" />

3. Can I pass a custom prop (e.g. `blahblahblah={true}`) to a native
   DOM element? (e.g. <div blahblahblah={true}>) Why or why not?
   No, because the JSX we use to describe native DOM elements will
   be turned into REAL DOM elements by React. And real DOM elements
   only have the properties/attributes specified in the HTML specification.
   (Which doesn't include properties like `blahblahblah`)

4. How do I receive props in a component?
   function Navbar(props) {
   console.log(props.blahblahblah)
   return (
   <header>
   ...
   </header>
   )
   }

5. What data type is `props` when the component receives it?
   An object!

6. What does the `.map()` array method do?
   Returns a new array. Whatever gets returned from the callback
   function provided is placed at the same index in the new array.
   Usually we take the items from the original array and modify them
   in some way.

7. What do we usually use `.map()` for in React?
   Convert an array of raw data into an array of JSX elements
   that can be displayed on the page.

8. Why is using `.map()` better than just creating the components
   manually by typing them out?
   It makes our code more "self-sustaining" - not requiring
   additional changes whenever the data changes.

**Props VS States**

1. How would you describe the concept of "state"?
   A way for React to remember saved values from within a component.
   This is similar to declaring variables from within a component,
   with a few added bonuses (which we'll get to later)

2. When would you want to use props instead of state?
   Anytime you want to pass data into a component so that
   component can determine what will get displayed on the
   screen.

3. When would you want to use state instead of props?
   Anytime you want a component to maintain some values from
   within the component. (And "remember" those values even
   when React re-renders the component).

4. What does "immutable" mean? Are props immutable? Is state immutable?
   Unchanging. Props are immutable. State is mutable.

**array.map()**

1. What does the `.map()` array method do?
   Returns a new array. Whatever gets returned from the callback
   function provided is placed at the same index in the new array.
   Usually we take the items from the original array and modify them
   in some way.

2. What do we usually use `.map()` for in React?
   Convert an array of raw data into an array of JSX elements
   that can be displayed on the page.

3. Why is using `.map()` better than just creating the components
   manually by typing them out?
   It makes our code more "self-sustaining" - not requiring
   additional changes whenever the data changes.

**useState - Changing state with a callback function**

Note: if you ever need the old value of state
to help you determine the new value of state,
you should pass a callback function to your
state setter function instead of using
state directly. This callback function will
receive the old value of state as its parameter,
which you can then use to determine your new
value of state.

**state quiz (callBack function)**

1. You have 2 options for what you can pass in to a
   state setter function (e.g. `setCount`). What are they?

   a. New value of state (setCount(42))

   b. Callback function - whatever the callback function
   returns === new value of state

2. When would you want to pass the first option (from answer
   above) to the state setter function?

   Whenever you don't need the previous value of state to determine
   what the new value of state should be.

3. When would you want to pass the second option (from answer
   above) to the state setter function?

   Whenever you DO need the previous value to determine the new value

**Conditional Rendering Quiz**

1. What is "conditional rendering"?
   When we want to only sometimes display something on the page
   based on a condition of some sort

2. When would you use &&?
   When you want to either display something or NOT display it

3. When would you use a ternary?
   When you need to decide which thing among 2 options to display

4. What if you need to decide between > 2 options on
   what to display?
   Use an `if...else if... else` conditional or a `switch` statement

function App() {
let someVar
if () {
someVar = <SomeJSX />
} else if() {
...
} else {
...
}
return (

<div>{someVar}</div>
)
}

**form quiz**

1. In a vanilla JS app, at what point in the form submission
   process do you gather all the data from the filled-out form?
   Right before the form is submitted.

2. In a React app, when do you gather all the data from
   the filled-out form?
   As the form is being filled out. The data is all held in local state.

3. Which attribute in the form elements (value, name, onChange, etc.)
   should match the property name being held in state for that input?
   `name` property.

4. What's different about saving the data from a checkbox element
   vs. other form elements?
   A checkbox uses the `checked` property to determine what should
   be saved in state. Other form elements use the `value` property instead.

5. How do you watch for a form submit? How can you trigger
   a form submit?

- Can watch for the submit with an onSubmit handler on the `form` element.
- Can trigger the form submit with a button click.

**useEffect Quiz**

1. What is a "side effect" in React? What are some examples?

- Any code that affects an outside system.
- local storage, API, websockets, two states to keep in sync

2. What is NOT a "side effect" in React? Examples?

- Anything that React is in charge of.
- Maintaining state, keeping the UI in sync with the data,
  render DOM elements

3. When does React run your useEffect function? When does it NOT run
   the effect function?

- As soon as the component loads (first render)
- On every re-render of the component (assuming no dependencies array)
- Will NOT run the effect when the values of the dependencies in the
  array stay the same between renders

4. How would you explain what the "dependecies array" is?

- Second paramter to the useEffect function
- A way for React to know whether it should re-run the effect function
