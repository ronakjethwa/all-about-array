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
let arrays = [
  ["$6"],
  ["$12"],
  ["$25"],
  ["$25"],
  ["$18"],
  ["$22"],
  ["$10"]
];
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