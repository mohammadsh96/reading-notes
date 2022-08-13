# react-hooks-useEffect
[back to main](./README.md)

- WHAT IS useEffect ?

useEffect () is a react hook which you will use most besides useState (). You’ll often use this hook whenever you need to run some side effects (like sending http requests) in your component. 


- when to use the useEffect () hook and how to write the syntax ? 
useEffect runs after the rendering/re-rendering of the component but only if any of the dependencies is changed. Remember it runs after the component is rendered(or mounted) not before, not along with but only after the component is rendered. Let me show you this with an example.

```js
import React, { useEffect } from "react";
export const Test = () => {
useEffect(() => {
  console.log("Effect");
}, []);
console.log(“rendered”);
return <>{console.log("UI rendered")}</>;

```
Syntax :- useEffect( ()=>{} , [dependencies] ). It takes two arguments separated with a comma, first — a function that you want to execute whenever useEffect runs.


**We will see three cases to understand use of dependencies in useEffect hook**


- Case I. Array with few dependencies 

```js
import React, { useState, useEffect } from "react";
export const Test = () => {
  const [value1, setValue1] = useState("VALUE 1");
  const [value2, setValue2] = useState("VALUE 2");
  const [value3, setValue3] = useState("VALUE 3");
 
  useEffect(() => {
    console.log("effect");
  }, [value1, value2]);
 
  const clickHandler1 = () => {
    setValue1((prevState) => prevState + "VALUE 1");
  };
  const clickHandler2 = () => {
    setValue2((prevState) => prevState + "VALUE 2");
  };
  const clickHandler3 = () => {
    setValue3((prevState) => prevState + "VALUE 3");
  };
  return (
    <div>
      <p onClick={clickHandler1}>{value1}</p>
      <p onClick={clickHandler2}>{value2}</p>
      <p onClick={clickHandler3}>{value3}</p>
    </div>
  );
};

```
The “effect” will log in the console —

For the very first time when the component is rendered (because for the very first time value of dependencies value1 and value2 seem to be changed to react).
Again if any of the states of value1 or value2 will be changed but not if the state of value3 is changed.


- CASE II. Array with no dependencies (empty array).

```js
import React, { useState, useEffect } from "react";
 
export const Test = () => {
  const [value, setValue] = useState("VALUE");
 
  useEffect(() => {
    console.log("effect");
  }, []);
 
  const clickHandler = () => {
   setValue((prevState) => prevState + "VALUE");
  };
  
  return (
    <div>
      <p onClick={clickHandler}>{value}</p>
    </div>
  );
};
```
Here useEffect has the 2nd argument of empty array.

The “effect” will be logged only when the component is rendered very first time. It will not run if “the state of value” is changed (the component will re-render but still the useEffect won’t run).

Now, the question comes why did the effect run only once. Here is answer to your question —

For the very first time useEffect runs after component evaluation because you had no dependencies before. But once it ran for the very first time, now it has no dependencies but also they didn’t change compared to the first execution cycle.

- Case III. Without the 2nd argument [ useEffect( ()=> {} ) ]

Can we have useEffect without the 2nd argument ? Yes, and here is our third and last case. You will use this case very rarely. In this case useEffect runs after every render and re — render of the component.

```js
import React, { useEffect, useState } from "react";
 
export const Test = () => {
  const [value, setValue] = useState(false);
 
  useEffect(() => {
    console.log("effect");
  });
 
  const clickHandler = () => {
    setValue((prevState) => !prevState);
  };
 
  return (
    <div>
      <h1>{value ? "hello" : "hey"}</h1>
      <button onClick={clickHandler}>Click me</button>
    </div>
  )};
  ```
  The “effect” text will be logged every time after component renders or re-renders. Here comes one more interesting question — what will be the difference if instead of

```js
useEffect(() => {
console.log(“effect”);
});
```
We directly write —
```js
console.log(“effect”)

```
The difference is that the first one will run ( “effect” will be logged ) after the component is evaluated or re — evaluated while the second one will run (“effect” will be logged) during / along with the component evaluation/re-evaluation


