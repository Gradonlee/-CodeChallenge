# Title: Roman Numeral Converter
Convert the given number into a roman numeral.

| Roman numerals | Arabic numerals |
|---|---|
| M | 1000 |
| CM | 900 |
| D | 500 |
| CD | 400 |
| C | 100 |
| XC | 90 |
| L | 50 |
| XL | 40 |
| X | 10 |
| IX | 9 |
| V | 5 |
| IV | 4 |
| I | 1 |
All roman numerals answers should be provided in upper-case.
### Before
  
``` Javascript
	  function convertToRoman(num) {
	   return num;
	  }
	  
	  convertToRoman(36);
```
### Answer
  
``` Javascript
	  function convertToRoman(num) {
	    let result = "";
	    let roman = {
	    M: 1000,
	    CM: 900,
	    D: 500,
	    CD: 400,
	    C: 100,
	    XC: 90,
	    L: 50,
	    XL: 40,
	    X: 10,
	    IX: 9,
	    V: 5,
	    IV: 4,
	    I: 1
	    }
	    for(var key in roman) {
	      while (num >= roman[key]) {
	        result += key;
	        console.log(result);
	        num -= roman[key];
	      }
	    }
	    return result;
	  }
	  
	  
	  convertToRoman(2);
```
### Thinking
想到了的话看懂还是挺简单的，问题是比较难想到。。