1. Prototypes are a mechanism in Javascript to inherit common properties for an object.
  -Every object is linked to a prototype object through `__proto__` . If a property or method is called on an object, if the object doesn't contain it, then the lookup happens on the object property. 
  - This will continue upwards till the field is found - forming a prototype chain.
  - Example: A constructor when used to create an object, returns a new object whose prototype is the constructor function.
  ```
  function s(col,b) {
    this.col = col;
    this.b = b;
  }
  let sw = new sw('w','t');
  s.prototype.isYummy = () => true;
  ```

2. 
```

Array.prototype.myMap = function (callbackFn, thisArg) {
  const newArr = [];
  const curArr = this;

  curArr.forEach((item, idx) => {
    newArr.push(callbackFn.bind(thisArg)(item, idx, curArr));
  });

  return newArr;
};

// filter
Array.prototype.myFilter = function (callbackFn, thisArg) {
  const newArr = [];
  const curArr = this;

  curArr.forEach((item, idx) => {
    if (callbackFn.bind(thisArg)(item, idx, curArr)) {
      newArr.push(item);
    }
  });

  return newArr;
};

// reduce
Array.prototype.myReduce = function (callbackFn, initialVal) {
  let reducedVal = null;
  const curArr = this;

  if (curArr.length == 0 && typeof initialVal === "undefined") {
    throw new TypeError("Initial val ");
  }

  curArr.forEach((item, idx) => {
    if (idx === 0) {
      if (typeof initialVal === "undefined") {
        //         take the first item and skip this index.
        reducedVal = item;
      } else {
        reducedVal = callbackFn(initialVal, item, idx, curArr);
      }
    } else {
      reducedVal = callbackFn(reducedVal, item, idx, curArr);
    }
  });

  return reducedVal;
};

// every
Array.prototype.myEvery = function (callbackFn, thisArg) {
  let countFalse = 0;
  const curArr = this;

  curArr.forEach((item, idx) => {
    if (!callbackFn.bind(thisArg)(item, idx, curArr)) {
      countFalse++;
    }
  });

  return countFalse == 0;
};

// find
// every
Array.prototype.myFind = function (callbackFn, thisArg) {
  let found;
  const curArr = this;

  for (let idx = 0; idx < curArr.length; ++idx) {
    if (callbackFn.bind(thisArg)(curArr[idx], idx, curArr)) {
      found = curArr[idx];
      break;
    }
  }

  return found;
};

//join

Array.prototype.myJoin = function (delimiter = ",") {
  let res = "";
  const curArr = this;

  for (let idx = 0; idx < curArr.length; ++idx) {
    // const curt = typeof curArr[idx];
    if (curArr[idx] == null || curArr[idx] == undefined) {
      res += "" + delimiter ;
    } else {
      //       can simply use Stirng (ToString) as it does not use join.
      res +=  String(curArr[idx])+ delimiter;
    }
  }

  return res.slice(0,res.length-delimiter.length);
};

```
  
  
