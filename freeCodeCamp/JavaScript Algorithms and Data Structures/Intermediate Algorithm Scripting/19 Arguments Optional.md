# Title: Arguments Optional
Create a function that sums two arguments together. If only one argument is provided, then return a function that expects one argument and returns the sum.

For example,  `addTogether(2, 3)`  should return  `5` , and  `addTogether(2)`  should return a function.

Calling this returned function with a single argument will then return the sum:
```
	  var sumTwoAnd = addTogether(2);
```
`sumTwoAnd(3)`  returns  `5` .
If either argument isn't a valid number, return undefined.
### Before
  
``` Javascript
	  function addTogether() {
	    return false;
	  }
	  
	  addTogether(2,3);
```
### Answer
  
``` Javascript
	  function addTogether() {
	    const [first, second] = arguments;
	    console.log(`second: ${second}`)
	    if (typeof(first) !== "number")
	      return undefined;
	    if (second === undefined)
	  
	      return (second) => addTogether(first, second);
	    if (typeof(second) !== "number")
	      return undefined;
	    return first + second;
	  }
	  
	  console.log(addTogether(5)(7))
```
### Thinking
用arguments 来解决这道题，其中要是没有 second 的参数，则是处于 undefined 的状态，然后将其再返回的 addTogether 里去分析，也就是最下面我所举例的(5)(7)的例子，再去查看第二个是否为数字，如果是的话，就返回回来一起加起来