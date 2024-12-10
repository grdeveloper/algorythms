# algorythms

1. New Sort Array algorythm with 0(2n) complexity.
The case of 2 numbers with the same value is ignored.

```javascript
var array = [1, 7, 3, 6, 11, 9];

function sortArray (arr) {
	var resultObject = {};
	var result = [];

	for (var item = 0; item < arr.length; item++) {

		resultObject[arr[item]] = true;

	}
	
	for (var prop in resultObject) {
		if (resultObject.hasOwnProperty(prop)) {
			result.push(+prop);
		}
	}

	return result;
}

// [1, 3, 6, 7, 9, 11]

console.log(sortArray(array));
```

2. Excel-like headers algorythm.

```javascript
function columnNames(n) {
  let result = [];

  const indexA = "A".charCodeAt(0);
  const indexZ = "Z".charCodeAt(0);

  let alphabetLength = indexZ - indexA + 1;
  const repeatNum = Math.floor(n / alphabetLength);

  let startIndex = 0;
  let startString = "";
  let string = "";

  while (startIndex <= repeatNum) {
    if (startIndex > 0) {
      startString = String.fromCharCode(indexA + startIndex - 1);
    }

    if (startIndex === repeatNum) {
        alphabetLength = n % alphabetLength;
      }

    for (var i = 0; i < alphabetLength; i++) {
      string = String.fromCharCode(indexA + i);

      result.push(startString + string);
    }
    startIndex++;
  }

  console.log(result, result.length);
  return result;
}

// ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "AA", "AB", "AC", "AD", "AE", "AF", "AG", "AH", "AI", "AJ", "AK", "AL", "AM", "AN", "AO", "AP", "AQ", "AR", "AS", "AT", "AU", "AV", "AW", "AX", "AY", "AZ", "BA", "BB", "BC"]

console.log(columnNames(55));
```

3. Spiral direction number algorythm.

```javascript
function sortN(quantity){
    var arr = new Array(quantity * quantity);
    var result = [];
    var start = false;

    for (var i = 0; i < arr.length; i++) {
      var step = i % quantity;

      if (step === 0) {
        result.push([]);

        start = !start;

      }

      if (start) {
        result[result.length - 1].push(i + 1);
      } else {
        result[result.length - 1].unshift(i + 1);
      }

    }

    return result;
}

/*
[1, 2, 3]
[6, 5, 4]
[7, 8, 9]
*/

console.log(sortN(3));
```

4. Find two maximum number's algorythm.

```javascript
var array = [1, 3, 5, 4, 9, 11, 7, 12, 105, 14, 11, 100];

function findGreatestNumsbers(arr) {
	var objMaxKeys = {
		max: 0,
		ltMax: 0
	};
	
	for (var item = 0; item < arr.length; item++) {

		if (objMaxKeys.max < arr[item]) {
			objMaxKeys.ltMax =  objMaxKeys.max;
			objMaxKeys.max = arr[item];
		}

		if (objMaxKeys.ltMax < arr[item] && arr[item] < objMaxKeys.max) {
			objMaxKeys.ltMax =  arr[item];
		}

	}

	return objMaxKeys;
}

// {max: 105, ltMax: 100}

findGreatestNumsbers(array);
```

5. Find all Mondays between the given dates' algorythm.

```javascript
var START_DATE = "1/11/2017";
var END_DATE = "5/15/2019";

function getAllMondays(startDate, endDate) {
	var monday = 1; // representation of Monday in Date object
	var oneDay = 1000 * 60 * 60 * 24; // milliseconds, seconds, minutes, hours

	var resultArray = [];

	for (var i = +new Date(startDate); i < +new Date(endDate); i += oneDay) {
		var newDay = new Date(i);
		
		if (newDay.getDay() === monday) {
			resultArray.push(newDay.toLocaleDateString());
		}
	}

	return resultArray;
}

// ["1/16/2017", "1/23/2017", "1/30/2017", ...]

getAllMondays(START_DATE, END_DATE);
```

6. GrandCandy's algorythm:
   There is an undefined quantity of candies and children.
   First the first child gets a candy, the second one two candies, the third one three candies, etc.
   Then the remaining candies are being shared between children, one candy per child.
   
```javascript
var CHILDREN = 3;
var CANDY = 7;

function grantCandy (children, candy) {
	var resultArray= [];
	var remainingCandies = candy;

	if (candy === 0) {
		return 0;
	}

	for (var item = 0; item < children; item++) {
		var currentCount = item + 1;
		
		if (remainingCandies > currentCount) {
			resultArray[item] = currentCount;
		} else {
			resultArray[item] = remainingCandies;
			remainingCandies = 0;
		}
		
		if (remainingCandies) {
			remainingCandies -= currentCount;
		}	
	}
	
	if (remainingCandies) {
		var currentChild = 0;
		for (var piece = 0; piece < remainingCandies; piece++) {

			if ((currentChild % children === 0) && currentChild !== 0) {
				currentChild = 0;
			}
			
			resultArray[currentChild]++;
			currentChild++;
		}
	}

	return resultArray;
}

// [2, 2, 3]

grantCandy(CHILDREN, CANDY);
```

7. Binary search algorythm.

```javascript
var array = [
	{prop: 1}, {prop: 2}, {prop: 3}, {prop: 4}, 
	{prop: 5}, {prop: 6}, {prop: 7}, {prop: 8}, 
	{prop: 9}, {prop: 10}, {prop: 11}
];

function findBinaryElem(arr, number){
	var midLengthElement = Math.floor(arr.length / 2);

	if (!arr.length) {
		return arr;
	}

	if (arr[midLengthElement]['prop'] === number) {
		return arr[midLengthElement];
	}

	if (arr[midLengthElement]['prop'] > number) {
		return findBinaryElem(arr.slice(0, midLengthElement), number);
	}

	if (arr[midLengthElement]['prop'] < number) {
		return findBinaryElem(arr.slice(midLengthElement), number);
	}
}

// {prop: 7}

findBinaryElem(array, 7);
```

8. Transform input collection into another group.

```javascript
let collection = [
      { field: 'type1', value: { dataLeft: 1, dataRight: 0 } }, 
      { field: 'type2', value: { dataLeft: 2, dataRight: 0 } }, 
      { field: 'type0', value: { dataLeft: 0, dataRight: 0 } }, 
      { field: 'type1', value: { dataLeft: 1, dataRight: 1 } }, 
      { field: 'type0', value: { dataLeft: 0, dataRight: 1 } }, 
      { field: 'type0', value: { dataLeft: 0, dataRight: 2 } }, 
      { field: 'type1', value: { dataLeft: 1, dataRight: 2 } }
    ];
    
/*
	Imperative way
*/

function group(collection) {
  	let object = {};
    	let resultArray = [];
  
  	loop: for (let item = 0; item < collection.length; item++) {
    	      let currentItem = collection[item];
    
	      if (!object[currentItem.field]) {
		object[currentItem.field] = {
		  groupName: currentItem.field,
		  groupSource: [currentItem.value]
		};

	      } else {

		object[currentItem.field]
		.groupSource
		.push(currentItem.value);

	      }
      
	      let groupSource = object[currentItem.field].groupSource;
	      groupSource[groupSource.length - 1].field = currentItem.field;
    	}
    
	    for (let prop in object) {
		if (object.hasOwnProperty(prop)) {
			resultArray.push(object[prop]);
	      }
	    }
    
    return resultArray;
  }

/*
	Declarative way
*/

function group(collection) {
	const sortedTypes = [...new Set(
		collection
			.map(item => item.field)
			.sort()
			)].map(item => ({
				groupName: item,
				groupSource: []
	}));
      
	collection
		.forEach(item => {
			return sortedTypes
			  .find(entity => entity.groupName === item.field)
			  .groupSource
			  .push({...item.value, 'field': item.field});
	});
      
        return sortedTypes;
  }

/*
   [ 
      {
        "groupName": "type0",
        "groupSource": [
          { "dataLeft": 0, "dataRight": 0, "field": "type0" }, 
          { "dataLeft": 0, "dataRight": 1, "field": "type0" }, 
          { "dataLeft": 0, "dataRight": 2, "field": "type0" }
        ]
      },
      { 
      	"groupName": "type1", 
      	"groupSource": [
          { "dataLeft": 1, "dataRight": 0, "field": "type1" }, 
          { "dataLeft": 1, "dataRight": 1, "field": "type1" }, 
          { "dataLeft": 1, "dataRight": 2, "field": "type1" }
        ]
      }, 
      {
        "groupName": "type2",
        "groupSource": [
        	{ "dataLeft": 2, "dataRight": 0, "field": "type2" }
        ]
      }
    ]
*/

group(collection);
```

9. Select the text as an array between the given letters.

```javascript
const str = 'This Javascript was born to love you';

function match(str, left, right) {
	let leftIndex;
	let rightIndex;
	let [opening, closing] = ['[', ']'];

	for (let i = 0; i < str.length; i++) {
		if (str[i] === left && !leftIndex && !!~leftIndex) {
			leftIndex = i;
		}

		if (str[i] === right && (leftIndex || leftIndex === 0)) {
			rightIndex = i;
		}
	}
    
    	if (!(leftIndex && rightIndex)) {
		return str;
	}

	return `${str.substr(0, leftIndex)}${opening}${str.substr(leftIndex, rightIndex - opening.length)}${closing}${str.substr(rightIndex + [opening, closing].length)}`;
}

// "Thi[s Javascript was born to] love you"

match(str, 's', 't');
```

10. Observable - observer logic.

```javascript
function Observable(subscribe) {
  this.subscribe = subscribe;                               // =  PUBLIC PROPERTY  <==
}                                                           // =                     =
                                                            // =                     =
const one$ = new Observable(observer => {                   // =                     =
  observer.next(1);                                         // =                     =
  // observer.complete();                                   // =                     =
});                                                         // =                     =
                                                            // =                     =
one$.subscribe({                                            // =                     =
  next: value => console.log(value)                         // =                     =
});                                                         // =                     =
                                                            // =                     =
Observable.fromEvent = (element, name) => {                 // =  STATIC METHOD    <==
  return new Observable(observer => {                       // =                     =
    const callback = event => observer.next(event);         // =                     =
    element.addEventListener(name, callback, false);        // =                     =
    return () => element.removeEventListener(name, callback, false); //              =
  });                                                       // =                     =
};                                                          // =                     =
                                                            // =                     =
Observable.prototype.map = function(mapFn) {                // =  PROTOTYPE METHOD <==
  const input = this;
  return new Observable(observer => {
    return input.subscribe({
      next: value => observer.next(mapFn(value)),
      error: error => observer.error(error),
      complete: () => observer.complete()
    });
  });
};

const node = document.querySelector('input');
const p = document.querySelector('p');

const input$ = Observable
  .fromEvent(node, 'input')
  .map(event => event.target.value);

const unsubscribe = input$.subscribe({
  next: value => p.innerHTML = value
});

setTimeout(unsubscribe, 5000);
```

11. Redux (NgRx, NgXs) custom store logic.

```javascript
export class Store {
  private state: {[key: string]: any};
  private readonly reducers: {[key: string]: () => {[key: string]: any}};
  private subscribers: ((value: any) => any)[];

  constructor(reducersObject = {}, initialStateObject = {}) {
    this.state = this.reduce(initialStateObject, {});
    this.reducers = reducersObject;
    this.subscribers = [];
  }

  get value() {
    return this.state;
  }

  dispatch(action) {
    this.state = this.reduce(this.state, action);
    this.subscribers.forEach(fn => fn(this.value));
  }

  subscribe(fn) {
    this.subscribers = [...this.subscribers, fn];
    fn(this.value);
    return () => {this.subscribers.filter(sub => sub !== fn); };
  }

  private reduce(state, action) {
    const newState: {[key: string]: any} = {};

    for (const prop in this.reducers) {
      if (this.reducers.hasOwnProperty(prop)) {
        const fn: (state: {[key: string]: any}, action: {type: string; payload?: any}) => any
          = this.reducers[prop];
        newState[prop] = fn(state[prop], action);
      }
    }

    return newState;
  }
}
```

12. Custom Promise

```javascript
var d = new Deferred();
d.then(function(res){
    console.log("1 ", res);
    var d1 = new Deferred();
    setTimeout(function(){ d1.resolve("a"); }, 2000);
    return d1;
});
d.then(function(res){ console.log("2 ", res); return "b"; });
d.then(function(res){ console.log("3 ", res); return "c"; });
d.resolve("hello");

// 1 hello     
// 2 a
// 3 b

class Deferred {

  constructor() {
    this.ctx = null;
    this.fns = [];
  }

  then(cb) {
    this.fns.push(cb);
  }

  resolve(param) {
    thix.ctx = param;
    for (let i=0; i<this.fns.length; i++) {
      this.ctx = this.fns[i](this.ctx);
      if (this.ctx instanceof Deferred) {
	const remainingFns = this.fns.slice(i+1);
	this.ctx.fns.push(...remainingFns);
        break;
    }
  }

}

```

13. React Input Debounce
```javascript
import * as React from 'react';

function debounce<T>(cb: (...args: Array<T>) => void, delay = 1000) {
  let timeout = 0;

  return (...args: Array<T>) => {
    timeout && clearTimeout(timeout);
    timeout = setTimeout((): void => {
      cb(...args);
    }, delay);
  };
}

function App() {
  const [input, setInput] = React.useState<string>();

  const debounceInputChange = debounce<React.ChangeEvent<HTMLInputElement>>(
    (event): void => {
      const { target } = event;
      const { value } = target as HTMLInputElement;

      setInput(value);
    }
  );

  return (
    <>
      <input onChange={debounceInputChange} />
      <span>{input}</span>
    </>
  );
}

export default App;

```


