# algorythms

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

console.log(sortArray(array));
```
