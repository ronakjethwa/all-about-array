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