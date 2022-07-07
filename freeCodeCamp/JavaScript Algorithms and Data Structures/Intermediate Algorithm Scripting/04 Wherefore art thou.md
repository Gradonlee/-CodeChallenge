# Wherefore art thou
Make a function that looks through an array of objects (first argument) and returns an array of all objects that have matching name and value pairs (second argument). Each name and value pair of the source object has to be present in the object from the collection if it is to be included in the returned array.

For example, if the first argument is [{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }], and the second argument is { last: "Capulet" }, then you must return the third object from the array (the first argument), because it contains the name and its value, that was passed on as the second argument.
### Before
```Javascript
function whatIsInAName(collection, source) {
  const arr = [];
  // Only change code below this line


  // Only change code above this line
  return arr;
}

whatIsInAName([{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }], { last: "Capulet" });
```
### Answer
```Javascript
function whatIsInAName(collection, source) {
  const arr = [];
  // Only change code below this line
  for (let i = 0; i < collection.length; i++){
    let shouldPush = true;
    let current = collection[i];
    console.log(collection[i])
    for (let key in source) {
      if (current[key] !== source[key]) {
        console.log(current[key])
        shouldPush = false;
      }
    }
    if (shouldPush) {
      arr.push(current);
    }
  }

  // Only change code above this line
  return arr;
}

whatIsInAName([{ first: "Romeo", last: "Montague" },
  { first: "Mercutio", last: null },
  { first: "Tybalt", last: "Capulet" }
],

  { last: "Capulet" }
);

whatIsInAName([{ "apple": 1, "bat": 2 },
  { "bat": 2 },
  { "apple": 1, "bat": 2, "cookie": 2 }
    ],
    
     { "apple": 1, "bat": 2 })
```
### Thinking
~~遍历键值对吗？这一看就不是我会写的~~
```
遍历 collection，如在第一次遍历中{ first: "Romeo", last: "Montague" }：
    默认一个 shouldPush 的状态为 true
    遍历 source 里的每一个 key 如第一次遍历 last：
        如果 last 中的 value 不等于 current 中存在 last 的 key 中的 value（如果 current 中不存在对应的的 key 则会返回 undefined 同样也是不等于）：
        则将 shouldPush 的状态改为 false
    如果 shouldPush 的状态还为 true：
        push current 所对应的键值对给 arr
```