# Smallest Common Multiple
Find the smallest common multiple of the provided parameters that can be evenly divided by both, as well as by all sequential numbers in the range between these parameters.

The range will be an array of two numbers that will not necessarily be in numerical order.

For example, if given 1 and 3, find the smallest common multiple of both 1 and 3 that is also evenly divisible by all numbers between 1 and 3. The answer here would be 6.
### Before
```Javascript
function smallestCommons(arr) {
  return arr;
}

smallestCommons([1,5]);
```
### Answer
```Javascript

```
### Thinking
```
我感觉是一个
```
找较大的数 不是一次一次去写而是提取出大的再比较
```js
function smallestCommons(arr) {
  let smaller = Math.min(...arr);
  let larger = Math.max(...arr);
  let numArr = [], res = 1;

  for (let i = smaller; i <= larger; i++) {
    numArr.push(i);
  }
  //let smaller = arr[0] > arr[1] ? arr[1] : arr[0];//Math.min.apply(null, [1, 5, 8])用 apply or Math.min(...[10, 5, 8]) 打散

  for (let i = 0; i < numArr.length; i++) {
        res = getSCM(numArr[i], res);
  }

  return res;
}

smallestCommons([1,5]);

function getSCM(left, right) {
    if (left === 0|| right === 0) {
        return 0;
    }
    if (left === right) {
        return left;
    }

    let res = right;
    while (res <= left * right) {
        if(res % left === 0) {
            return res;
        }
        res += right;
    }
}
```


2, 3: 6, 9, 12,
x, y: y, 2y ,3y ... 直到 xy 因为能被 x 整除也能被 y 整除