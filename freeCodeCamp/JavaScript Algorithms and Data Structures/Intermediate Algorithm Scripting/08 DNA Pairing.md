# DNA Pairing
Pairs of DNA strands consist of nucleobase pairs. Base pairs are represented by the characters AT and CG, which form building blocks of the DNA double helix.

The DNA strand is missing the pairing element. Write a function to match the missing base pairs for the provided DNA strand. For each character in the provided string, find the base pair character. Return the results as a 2d array.

For example, for the input GCG, return [["G", "C"], ["C","G"], ["G", "C"]]

The character and its pair are paired up in an array, and all the arrays are grouped into one encapsulating array.
### Before
```Javascript
function pairElement(str) {
  return str;
}

pairElement("GCG");
```
### Answer
```Javascript
function pairElement(str) {
  let newStr = str.split('');
  let dnaStrands = [];
  for(let i = 0; i < newStr.length; i++){
    switch(newStr[i]) {
      case "G":
        dnaStrands.push(["G","C"]);
        break;
      case "C":
        dnaStrands.push(["C","G"]);
        break;
      case "A":
        dnaStrands.push(["A","T"]);
        break;
      case "T":
        dnaStrands.push(["T","A"]);
        break;
    }
  }


  console.log(dnaStrands);
  return dnaStrands;
}

pairElement("GCG");
```
### Thinking
```
拆分字符串再 Switch push 回去
```