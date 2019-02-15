# algorythms

New Sort Array algorythm with 0(2n) complexity.
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

console.log(sortArray(array));
```

Excel-like headers algorythm.

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

console.log(columnNames(55));
```

Spiral direction number algorythm.

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

console.log(sortN(3));
```

