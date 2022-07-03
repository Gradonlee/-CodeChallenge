# Sum All Numbers in a Range

We'll pass you an array of two numbers. Return the sum of those two numbers and all numbers between them.

The lowest number will not always come first.

### Before

```javascript
function sumAll(arr) {
  return 1;
}

sumAll([1, 4]);
```

### Answer

```javascript
function sumAll(arr) {

  const newSumAll = arr.sort((a, b) => a - b)
  console.log(newSumAll)
  for(let i = arr[0] + 1; i < arr[1]; i++) {
    newSumAll.push(i)
  }
  const sum = newSumAll.reduce((a, b) => a + b,0)
  console.log(newSumAll)
  return sum;
}

sumAll([5, 10]);

console.log(sumAll([5, 10]));
```

### Thinking

1. sort the arr by accending
2. if and for the arr to create a full number arr
3. sum the arr
