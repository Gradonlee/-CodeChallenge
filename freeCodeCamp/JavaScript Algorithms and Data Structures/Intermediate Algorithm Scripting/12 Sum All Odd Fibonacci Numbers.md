# Sum All Odd Fibonacci Numbers
Given a positive integer num, return the sum of all odd Fibonacci numbers that are less than or equal to num.

The first two numbers in the Fibonacci sequence are 1 and 1. Every additional number in the sequence is the sum of the two previous numbers. The first six numbers of the Fibonacci sequence are 1, 1, 2, 3, 5 and 8.

For example, sumFibs(10) should return 10 because all odd Fibonacci numbers less than or equal to 10 are 1, 1, 3, and 5.

### Before
```Javascript
function sumFibs(num) {
  return num;
}

sumFibs(4);
```
### Answer
```Javascript
function sumFibs(num) {
  let prevNumber = 0;
  let currNumber = 1;
  let result = 0;
  while (currNumber <= num) {
    if (currNumber % 2 !== 0) {
      result += currNumber;
    }
    currNumber += prevNumber;
    prevNumber = currNumber - prevNumber;
  }

  return result;
}

// test here
sumFibs(4);

//console.log(sumFibs(4)) = 5
//console.log(sumFibs(5)) = 10
```
### Thinking
```
设置三个变量，之前变量，当前变量和结果变量
当 当前的数字小于等于 num 时
  在结果上累加当前值

  当前值再累加之前值
  之前的值等于当前值减去之前的值


图示
p   c   r
0   1   1
1   1   2
1   2   2
2   3   5
3   5   10

```