# Title: Make a Person
Fill in the object constructor with the following methods below:
```
	  getFirstName()
	  getLastName()
	  getFullName()
	  setFirstName(first)
	  setLastName(last)
	  setFullName(firstAndLast)
```
Run the tests to see the expected output for each method. The methods that take an argument must accept only one argument and it has to be a string. These methods must be the only available means of interacting with the object.
### Before
  
``` Javascript
	  const Person = function(firstAndLast) {
	    // Only change code below this line
	    // Complete the method below and implement the others similarly
	    this.getFullName = function() {
	      return "";
	    };
	    return firstAndLast;
	  };
	  
	  const bob = new Person('Bob Ross');
	  bob.getFullName();
```
### Answer
  
``` Javascript
	  var Person = function(firstAndLast) {
	      var nameArr = firstAndLast.split(' ');
	      
	      this.getFirstName = function() {
	          return nameArr[0];
	      };
	      this.getLastName = function() {
	          return nameArr[1];
	      }
	      this.getFullName = function() {
	          return nameArr.join(' ');
	      }
	      
	      this.setLastName = function(lastName) {
	          nameArr[1] = lastName;
	      }
	      this.setFirstName = function(firstName) {
	          nameArr[0] = firstName;
	      }
	      this.setFullName = function(fullName) {
	          nameArr = fullName.split(' ');
	      }
	  }
	  
	  var bob = new Person('Bob Ross');
```
### Thinking
根据题意慢慢测试就好