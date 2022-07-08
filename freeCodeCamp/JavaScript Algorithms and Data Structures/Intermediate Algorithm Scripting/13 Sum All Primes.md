# Sum All Primes
A prime number is a whole number greater than 1 with exactly two divisors: 1 and itself. For example, 2 is a prime number because it is only divisible by 1 and 2. In contrast, 4 is not prime since it is divisible by 1, 2 and 4.

Rewrite sumPrimes so it returns the sum of all prime numbers that are less than or equal to num.
### Before
```Javascript
function sumPrimes(num) {
  return num;
}

sumPrimes(10);
```
### Answer
```Javascript
function sumPrimes(num) {
  let currNumber = 2;
  let res = 0;
  
  const isPrime = num => {
    for(let i = 2, s = Math.sqrt(num); i <= s; i++)
        if(num % i === 0) return false; 
    return num > 1;
  }

  while (currNumber <= num) {
    if (isPrime(currNumber)) {
      res += currNumber;
    }
    currNumber ++;
  }
  return res;
}

sumPrimes(10);
```
### Thinking
```
先思考一下假设说 num = 10 ，那么存在的质数有
2，3，5，7
那么我们的思路之一是，用while（i <= 10)
则判断每个 i 是否为质数
const isPrime = num => {
    for(let i = 2, s = Math.sqrt(num); i <= s; i++)
        if(num % i === 0) return false; 
    return num > 1;
}
是的话则加起来
```