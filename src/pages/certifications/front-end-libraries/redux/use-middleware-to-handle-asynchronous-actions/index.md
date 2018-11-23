---
title: Use Middleware to Handle Asynchronous Actions
---
## Use Middleware to Handle Asynchronous Actions

Let us walk through a little bit about some basic concepts about what is going on in this challenge:
  1. dispatch() : Dispatches an action. This is the only way to trigger a state change.
  2. middleWare : described as picture below:
    <img src='https://cdn-images-1.medium.com/max/1600/1*OmGfUWYWwfu_OW6q-afFFg.png' alt=''/>
    There are many middleWare's library, but 3 most popular are: Redux-Thunk ; Redux-Saga ;  Redux-Obsevable.
Let's take a deeper look into Redux-Thunk:
  - Thunk is a special function; when normal functions return a result, Thunk returns a function, which does some works firstly and afterthat, return the result (like example bellow).</br>
  ```javascript
  const addNumber= function(a){
    console.log('sum');
     return function(b){
      return a+b;
      }
     }
   ```

  - Redux-Thunk : return function which takes two args <b>dispatch()</b> and <b>getState()</b> (2 methods of <b>store</b>)
   Therefore, you can create side effects like fetch data or deplay request. Redux-Thunk already passed dispatch() function as a argument,
   so instead of typing 
   ```javascript
   store.dispatch()
   ```
   You just use it as normal function
   ```javascript
   dispatch()
   ```
Let's get back to this challenge. 
The challenge require you to dispatch received data (Jeff,Willam,Alice) so you have to pass data to receivedDtata() as a arg
Here is the answer:
```javascript
const handleAsync = () => {
  return function(dispatch) {
    // dispatch request action here
      dispatch(requestingData());
    setTimeout(function() {
      let data = {
        users: ['Jeff', 'William', 'Alice']
      }
      // dispatch received data action here
      dispatch(receivedData(data));
    }, 2500);
  }
};
```

  

<!-- The article goes here, in GitHub-flavored Markdown. Feel free to add YouTube videos, images, and CodePen/JSBin embeds  -->
