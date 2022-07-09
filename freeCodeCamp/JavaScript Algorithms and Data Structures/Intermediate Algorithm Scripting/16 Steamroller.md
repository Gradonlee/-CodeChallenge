# Steamroller
Flatten a nested array. You must account for varying levels of nesting.
### Before
```Javascript

```
### Answer
```Javascript

```
### Thinking
```
```
Flatten a nested 二维的三维的都有可能 array. You must account for /考虑到 varying levels of nesting.
``` javascript
  function steamrollArray(arr) {
    return arr;
  }
  
  steamrollArray([1, [2], [3, [[4]]]]);
```
steamrollArray([1, [2], [3, [4]]]); 转成 1 维数组

.flat() 可以直接实现，但是最好别用

[1, 2, [3, [4]]] 将 3, 4提出来，取决于这个数组有多少层，用递归
``` javascript
function steamrollArray(arr) {
  let res = [];
  
  for (let val of arr) {
    if (!Array.isArray()) {
    	res.push(val);
    } else {
      res = res.concat(steamrollArray(val))
    }
  }
  
  return res;
}

steamrollArray([1, [2], [3, [[4]]]]);
```
调用一个一维数组，得到的结果就是 3 和 4

res: [1, 2].concat([3, 4]) => [1, 2, 3, 4]
