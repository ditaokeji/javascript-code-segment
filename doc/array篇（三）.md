# array篇（三）

41. sort an array of items by given key

```
const sortBy = (arr, k) => arr.concat().sort((a, b) => (a[k] > b[k]) ? 1 : ((a[k] < b[k]) ? -1 : 0));

// example
const people = [
    { name: 'foo', age: 42 },
    { name: 'bar', age: 24 },
    { name: 'fuzz', age: 36 },
    { name: 'baz', age: 32 },
];
sortBy(people, 'age');

// returns
//  [
//      { name: 'Bar', age: 24 },
//      { name: 'Baz', age: 32 },
//      { name: 'Fuzz', age: 36 },
//      { name: 'Foo', age: 42 },
//  ]
```

42. sort an array of numbers

```
const sort = arr => arr.sort((a, b) => a-b);

//example
sort([1,5,2,4,3]); // [1,2,3,4,5]
```

43. split an array into chunks

```
const chunk = (arr, size) => arr.reduce((acc, e, i) => (i % size ? acc[acc.length -1].push(e):acc.push([e]),acc), []);

// examples
chunk([1,2,3,4,5,6,7,8],3); // [[1,2,3],[4,5,6],[7,8]]
chunk([1,2,3,4,5,6,7,8],4); // [[1,2,3,4],[5,6,7,8]]
```

44. swap the rows and columns of a matrix

```
const transpose = matrix => matrix[0].map((col, i) => matrix.map(row => row[i]));

//or 
const transpose = matrix => matrix[0].map((col, c) => matrix.map((row, r) => matrix[r][c]));

//or 
const transpose = matrix => matrix.reduce((prev, next) => next.map((item, i) => (prev[i] || []).concat(next[i]), []);

// Example
transpose([             // [
    [1, 2, 3],          //      [1, 4, 7],
    [4, 5, 6],          //      [2, 5, 8],
    [7, 8, 9],          //      [3, 6, 9],
]);                     //  ]
```

45. swap two array items

```
const swapItems = (a, i, j) => a[i] && a[j] && [...a.slice(0,i), a[j],...a.slice(i+1,j),a[i],...a.slice(j+1)] || a;

// example
swapItems([1,2,3,4,5],1,4); // [1,5,3,4,2]
```