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
