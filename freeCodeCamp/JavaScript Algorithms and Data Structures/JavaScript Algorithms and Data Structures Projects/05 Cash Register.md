# Title: Cash Register
Design a cash register drawer function  `checkCashRegister()`  that accepts purchase price as the first argument ( `price` ), payment as the second argument ( `cash` ), and cash-in-drawer ( `cid` ) as the third argument.
`cid`  is a 2D array listing available currency.
The  `checkCashRegister()`  function should always return an object with a  `status`  key and a  `change`  key.
Return  `{status: "INSUFFICIENT_FUNDS", change: []}`  if cash-in-drawer is less than the change due, or if you cannot return the exact change.
Return  `{status: "CLOSED", change: [...]}`  with cash-in-drawer as the value for the key  `change`  if it is equal to the change due.
Otherwise, return  `{status: "OPEN", change: [...]}` , with the change due in coins and bills, sorted in highest to lowest order, as the value of the  `change`  key.

| Currency Unit | Amount |
|---|---|
| Penny | $0.01 (PENNY) |
| Nickel | $0.05 (NICKEL) |
| Dime | $0.1 (DIME) |
| Quarter | $0.25 (QUARTER) |
| Dollar | $1 (ONE) |
| Five Dollars | $5 (FIVE) |
| Ten Dollars | $10 (TEN) |
| Twenty Dollars | $20 (TWENTY) |
| One-hundred Dollars | $100 (ONE HUNDRED) |
See below for an example of a cash-in-drawer array:
```
	  [
	  ["PENNY", 1.01],
	  ["NICKEL", 2.05],
	  ["DIME", 3.1],
	  ["QUARTER", 4.25],
	  ["ONE", 90],
	  ["FIVE", 55],
	  ["TEN", 20],
	  ["TWENTY", 60],
	  ["ONE HUNDRED", 100]
	  ]
```
### Before
  
``` Javascript
	  function checkCashRegister(price, cash, cid) {
	    let change;
	    return change;
	  }
	  
	  checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);
```
### Answer
  
``` Javascript
	  function checkCashRegister(price, cash, cid) {
	    let change = cash * 100 - price * 100;
	    let cidTotal = 0;
	    for (let elem of cid) {
	      cidTotal += elem[1]*100;
	    }
	  
	    if (change > cidTotal) {
	      return {status: "INSUFFICIENT_FUNDS", change: []};
	    } else if (change === cidTotal) {
	      return {status: "CLOSED", change: cid};
	    } else {
	      let answer = [];
	      cid = cid.reverse()
	      let moneyUnits = {
	      TWENTY: 2000,
	      TEN: 1000,
	      FIVE: 500,
	      ONE: 100,
	      QUARTER: 25,
	      DIME: 10,
	      NICKEL: 5,
	      PENNY: 1
	      }
	      for (let elem of cid) {
	        let holder = [elem[0], 0];
	        elem[1] = elem[1] * 100;
	        while (change >= moneyUnits[elem[0]] && elem[1] > 0) {
	          change -= moneyUnits[elem[0]];
	          elem[1] -= moneyUnits[elem[0]];
	          holder[1] += moneyUnits[elem[0]] / 100;
	        }
	        if (holder [1] > 0) {
	          answer.push(holder); //返回所有 算出来得找钱的面额的数，没找那个面额就别拿出来
	        }
	      }
	      if (change > 0) { //用于判断第五种条件，收银台有 1.01 了，但是要找回 0.5，找不开
	        return {status: "INSUFFICIENT_FUNDS", change: []};
	      }
	      return {status: "OPEN", change: answer}
	    }
	  }
	  
```
### Thinking
YouTube 这个视频很有帮助：https://www.youtube.com/watch?v=7uyZ8pBXmqs&t=106s&ab_channel=MattLambert
尝试
有两个参数加一个收银台 object 传进来
首先先算出要找零要找多少，然后对应去用之前学的罗马计数的那里，将对应的单位先用 key，value 储存成键值对
从大到小将键值对选出来，还不清楚用什么方式传递到收银台里，先测试一下 currencyChange 会出什么吧
``` js
function checkCashRegister(price, cash, cid) { //cid是个数组啊，是不是应该先打成对象啊？直接用扩展运算符转,oh no 不行
  const cidObject = {...cid};
  console.log(cidObject);
  let change = cash - price;
  let currencyChange = {};
  const currencyUnit = { //写的时候从大到小写，方便到时候 for in
    TWENTY: 20,
    TEN: 10,
    FIVE: 5,
    ONE: 1,
    QUARTER: 0.25,
    DIME: 0.1,
    NICKEL: 0.05,
    PENNY: 0.01,
  }
  console.log(`change: ${change}`);
  //循环一个 currencyUnit 再 while 一个单位组合出来瞅瞅，每取出一次就先从提款机里减去
  for (let currency in currencyUnit) {
    while (change >= currencyUnit[currency]) { //从大到小判断合适的货币出来
      currencyChange += currency + " ";
      console.log(cid[QUARTER]); 
      change -= currencyUnit[currency];
    }
    //现在我们知道要从提款机 Object 里取出两个 Quarter 了，接着想办法看看要怎么取
  }
  return change;
}

let check = checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]);

console.log(check);
```