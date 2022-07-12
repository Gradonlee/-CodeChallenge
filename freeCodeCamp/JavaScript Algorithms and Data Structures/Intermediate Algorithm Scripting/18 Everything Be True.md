# Title: Everything Be True
Check if the predicate (second argument) is truthy on all elements of a collection (first argument).

In other words, you are given an array collection of objects. The predicate  `pre`  will be an object property and you need to return  `true`  if its value is  `truthy` . Otherwise, return  `false` .

In JavaScript,  `truthy`  values are values that translate to  `true`  when evaluated in a Boolean context.

Remember, you can access object properties through either dot notation or  `[]`  notation.
### Before
  
``` Javascript
	  function truthCheck(collection, pre) {
	    return pre;
	  }
	  
	  truthCheck([{name: "Quincy", role: "Founder", isBot: false}, {name: "Naomi", role: "", isBot: false}, {name: "Camperbot", role: "Bot", isBot: true}], "isBot");
```
### Answer
  
``` Javascript
	  function truthCheck(collection, pre) {
	    let result = true;
	    for (let i = 0; i < collection.length; i++) {
	      console.log(`collection[i][pre]: ${collection[i][pre]}`)
	      if(
	        collection[i][pre] === false ||
	        collection[i][pre] === '' ||
	        collection[i][pre] === 0 ||
	        Number.isNaN(collection[i][pre]) ||
	        collection[i][pre] === undefined ||
	        collection[i][pre] === null
	        ) {
	        result = false;
	      }
	    }
	    return result;
	  }
	  
	  let finalAnswer = truthCheck([{id: 1, data: {url: "https://freecodecamp.org", name: "freeCodeCamp"}}, {id: 2, data: {url: "https://coderadio.freecodecamp.org/", name: "CodeRadio"}}, {id: null, data: {}}], "id");
	  
	  console.log(`finalAnswer: ${finalAnswer}`)
```
### Thinking
挨个确认哪一个比较像无法通过的条件，然后 if 该条件然后 false 它，比较特殊的是 NaN 这一个，需要用 Number.isNaN() 来解决