# Drop it
Given the array arr, iterate through and remove each element starting from the first element (the 0 index) until the function func returns true when the iterated element is passed through it.

Then return the rest of the array once the condition is satisfied, otherwise, arr should be returned as an empty array.


### Before
```Javascript
function dropElements(arr, func) {
  return arr;
}

dropElements([1, 2, 3], function(n) {return n < 3; });
```
### Answer
```Javascript
function dropElements(arr, func) {
  let len = arr.length // 用 len 防止数组长度是动态的
  for (let i = 0; i < len; i++) { 
    if (func(arr[0])) {
      break;
    } else {
      arr.shift(); // 删掉一个，还得回来
    }
  }

  return arr;
}

dropElements([1, 2, 3], function(n) {return n < 3; });
```
### Thinking
```
```