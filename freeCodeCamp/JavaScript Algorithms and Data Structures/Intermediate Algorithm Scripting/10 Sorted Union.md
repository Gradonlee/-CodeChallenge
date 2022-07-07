# Sorted Union
Write a function that takes two or more arrays and returns a new array of unique values in the order of the original provided arrays.

In other words, all values present from all arrays should be included in their original order, but with no duplicates in the final array.

The unique numbers should be sorted by their original order, but the final array should not be sorted in numerical order.

Check the assertion tests for examples.
### Before
```Javascript
function uniteUnique(arr) {
  return arr;
}

uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);
```
### Answer
```Javascript
function uniteUnique(...arr) {
  return [...new Set([...arguments].flat())]
}

uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);
```
### Thinking
```
[...new Set()]:Set 属于是构造函数，new 一个新的然后放进一个数组里，然后用 Set 去除所有的重复 element
[...arguments]:扩展语法将[1, 3, 2], [5, 2, 1, 4], [2, 1]抓取到一个数组里
.flat():再将其中里面所有二位数组打平成一维数组
```