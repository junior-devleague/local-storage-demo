# Teaching Local Storage

## Web Storage
- Data that is stored locally in a user's browser. There are 2 types of web storage:
  - **Local Storage** - data with no expiration date that will persist after browser window is closed
  - **Session Storage** - data that gets cleared after the browser window is closed. 

## Why we use web storage
- Saving user preferences
- remembering data for shopping cart/todo list
- Don't need to make HTTP request

## Local Storage Methods
Method | Description
-------|------------
`setItem()` | Add key and value to local storage
`getItem()` | Retrieve a value by the key
`removeItem()` | Remove an item by key
`clear()` | Clear all storage

## Live-Code 
#### Test methods in developer tools
- Have students type in `localStorage`

```Storage {length: 0}```

- Run `localStorage.setItem('key', 'value');`

```Storage {key: "value", length: 1}```

- Run `localStorage.getItem('key');`

```value```
- Run `localStorage.clear();`

```Storage {length: 0}```

#### Applying local storage in VSCode

- Have student walk you through building button id "increment" and div with id "total"
```html
<body>
    <button id="increment">increment</button>
    <div id="result"></div>
    <script src="app.js"></script>
</body>
```
- Use window.onload
- Set variables for elements on page
```js
window.onload = function() {
  let increment = document.getElementById('increment');
  let result = document.getElementById('result');
  let score = 0; 
```
- Add event listener that increments number and updates DOM
```js
window.onload = function() {
  let increment = document.getElementById('increment');
  let result = document.getElementById('result');
  let score = 0;

  increment.addEventListener('increment', function(event) {
    number++;
    result.innerHTML = score;
  });
};
```
- Integrate local storage in addEventListener
```js
window.onload = function() {
  let increment = document.getElementById('increment');
  let result = document.getElementById('result');
  let score = 0;

  increment.addEventListener('increment', function(event) {
    number++;
    result.innerHTML = score;
    localStorage.setItem('totalNum', score);
    result.innerHTML = localStorage.getItem('totalNum');
  });
};
```
- Update the number with setItem so we can continue increment from where we started before
```js
window.onload = function() {
  let increment = document.getElementById('increment');
  let result = document.getElementById('result');
  let score = localStorage.getItem('totalNum');

  increment.addEventListener('increment', function(event) {
    number++;
    result.innerHTML = number;
    localStorage.setItem('totalNum', score);
    result.innerHTML = localStorage.getItem('totalNum');
  });
};
```
- Set result innerHTML when page initially loads
```js
window.onload = function() {
  let increment = document.getElementById('increment');
  let result = document.getElementById('result');
  let score = localStorage.getItem('totalNum');
  
  result.innerHTML = localStorage.getItem('totalNum');

  increment.addEventListener('increment', function(event) {
    number++;
    result.innerHTML = number;
    localStorage.setItem('totalNum', score);
    result.innerHTML = localStorage.getItem('totalNum');
  });
};
```
- AddEventListener clear to clear all data in local storage

```js
window.onload = function() {
  let increment = document.getElementById('increment');
  let result = document.getElementById('result');
  let score = localStorage.getItem('totalNum');
  let clear = document.getElementById('clear');
  
  result.innerHTML = localStorage.getItem('totalNum');

  increment.addEventListener('increment', function(event) {
    number++;
    result.innerHTML = number;
    localStorage.setItem('totalNum', score);
    result.innerHTML = localStorage.getItem('totalNum');
  });
  
  clear.addEventListener('click', function() {
    localStorage.removeItem('localStorage');
    score = 0;
    result.innerHTML = score;
  });
};
```
