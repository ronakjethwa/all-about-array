# All About Array
JavaScript Short Array Manipulations


## Find Unique Elements In Array

```javascript
function unique(arr) {
  return Array.from(new Set(arr));
}

let values = ["Hare", "Krishna", "Hare", "Krishna",
  "Krishna", "Krishna", "Hare", "Hare", ":-O"
];

console.log( unique(values) ); // Hare, Krishna, :-O
```

## Find Anagrams From Array

```javascript
// With Map
let arr = ["nap", "teachers", "cheaters", "PAN", "ear", "era", "hectares"];
function anagram(arr) {
  
  let map = new Map();

  for (let word of arr) {
    // split the word by letters, sort them and join back
    let sorted = word.toLowerCase().split('').sort().join(''); // (*)
    map.set(sorted, word);
  }
  return Array.from(map.values());
}
console.log( anagram(arr) );

// With Object
let arr = ["nap", "teachers", "cheaters", "PAN", "ear", "era", "hectares"];
function anagram(arr) {
  
  let obj = {};

  for (let i = 0; i < arr.length; i++) {
    let sorted = arr[i].toLowerCase().split("").sort().join("");
    obj[sorted] = arr[i];
  }
  return Object.values(obj);
}
console.log( anagram(arr) );
```

## Flaten Multidimensional Array

```js
let arrays = [ ["$6"],["$12"],["$25"],["$25"],["$18"],["$22"],["$10"] ];
let merged = arrays.flat();
console.log(merged);
```
#### Infinitely Nested Arrays

```js
let veryDeep = [[1, [2, 2, [3,[4,[5,[6]]]]], 1]];
let flattenArray = veryDeep.flat(Infinity);
console.log(flattenArray);
```

```js
let arrays = [ ["$6"],["$12"],["$25"],["$25"],["$18"],["$22"],["$10"] ];
let merged = [].concat.apply([],arrays);
console.log(merged);
```

## Map & Flat
```js
let animals = ['🐕', '🐈', '🐑', '🐮'];
let noises = ['woof', 'meow', 'baa', 'mooo'];

let mappedOnly = animals.map((animal, index) => [animal, noises[index]]);
let mappedAndFlatten = animals.flatMap((animal, index) => [animal, noises[index]]);

console.log(mappedOnly);
console.log(mappedAndFlatten);
```

## Sort Objects In Array
```js
const singers = [
  { name: 'Steven Tyler', band: 'Aerosmith', born: 1948 },
  { name: 'Karen Carpenter', band: 'The Carpenters', born: 1950 },
  { name: 'Kurt Cobain', band: 'Nirvana', born: 1967 },
  { name: 'Stevie Nicks', band: 'Fleetwood Mac', born: 1948 },
];

function compare(a, b) {
  // Use toUpperCase() to ignore character casing
  const bandA = a.name.toUpperCase();
  const bandB = b.name.toUpperCase();

  let comparison = 0;
  if (bandA > bandB) {
    comparison = 1;
  } else if (bandA < bandB) {
    comparison = -1;
  }
  return comparison;
}

singers.sort(compare);
```

## .every On Array
```js
// check if all elements are equal to a value in an array
let isEqual = (array, value) => array.every(item => item === value);
```

## .some On Array
```js
// check if all elements are equal to a value in an array
let isEqual = (array, value) => !array.some(item => item !== value);
```

## Array + Set
```js
// check if array has any duplicate elements
let areEqual = array => new Set(array).size === array.length;
areEqual([1,2,3,3]);
```

## Flattening Array With Reduce
```js
const numArray = [1, 2, [3, 10, [11, 12]], [1, 2, [3, 4]], 5, 6];

function flattenArray(data) {
  const initialValue = [];

  return data.reduce((result, value) => {
    return result.concat(Array.isArray(value) ? flattenArray(value) : value);
  }, initialValue);
}

console.log(flattenArray(numArray));
```