# Seek and Destroy
You will be provided with an initial array (the first argument in the destroyer function), followed by one or more arguments. Remove all elements from the initial array that are of the same value as these arguments.

Note: You have to use the arguments object.
### Before
```Javascript
function destroyer(arr) {
  return arr;
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```
### Answer
```Javascript
function destroyer(arr) {
  let newArr = [];
  let arrNeedSeek = Object.values(arguments)[0];
  let seekNumArray = Object.values(arguments).slice(1);

  arrNeedSeek.forEach(seekNum => {
    if(seekNumArray.indexOf(seekNum) === -1) {
      newArr.push(seekNum)
    }
  })

  return newArr;
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```
### Thinking
1. let the out of array items into another array in destroyer
2. compare and indexOf push unbelong back

用 Object.values(arguments).slice(1) 将 2, 3 合并成[2, 3]
.forEach 指的是遍历 arrNeedSeek 这里面的所有函数
用 indexOf 寻找第二个数组里有没有第一个数组里没有的数字，如果没有则将第一个数组中遍历到的数字 push 到 newArr 中。