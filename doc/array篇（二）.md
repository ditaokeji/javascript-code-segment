# array篇（二）

21. find the maximum item of an array by given key

```
const maxBy = (arr, key) => arr.reduce((a, b) => a[key] >= b[key] ? a : b, {});

//example
const people = [
    { name: 'Bar', age: 24},
    { name: 'Baz', age: 32},
    { name: 'Foo', age: 42},
    { name: 'Fuzz', age: 36},
]
maxBy(people, 'age'); // {name: 'foo', age: 42}
```

22. find the minimum item of an array

```
const min = arr => Math.min(...arr);
```

23. find the minimum item of an array by given key

```
const minBy = (arr, key) => arr.reduce((a, b) => a[key] < b[key] ? a : b, {});

//example
const people = [
    { name: 'Bar', age: 24},
    { name: 'Baz', age: 32},
    { name: 'Foo', age: 42},
    { name: 'Fuzz', age: 36},
]
maxBy(people, 'age'); // {name: 'bar', age: 24}
```

24. flatten an array

```
const flat = arr => [].concat.apply([], arr.map(a => Array.isArray(a) ? flat(a) : a));

//or
const flat = arr => arr.reduce((a, b) => Array.isArray(b) ? [...a, ...flat(b)] : [...a, b], []);

//or
const flat = arr => arr.flat();

//example
flat(['cat', ['lion', 'tiger']]); // ['cat', 'lion', 'tiger']
```

25. get all arrays of consecutive elements

```
const getConsecutiveArrays = (arr, size) => size > arr.length ? [] : arr.slice(size-1).map((_, i) => arr.slize(i, size+i))

//example
getConsecutiveArrays([1,2,3,4,5], 2); // [[1,2],[2,3],[3,4],[4,5]]
gieConsecutiveArrays([1,2,3,4,5], 3); // [[1,2,3],[2,3,4],[3,4,5]]
getConsecutiveArrays([1,2,3,4,5], 6); // []
```

26. get all n-th items of an array

```
const getNthItems = (arr, nth) => arr.filter((_, i) => i % nth === nth -1);

//examples
getNthItems([1,2,3,4,5,6,7,8,9], 2); // [2,4,6,8]
getNthItems([1,2,3,4,5,6,7,8,9], 3); // [3,6,9]
```

27. get all subsets of an array

```
const getSubsets = arr => arr.reduce((prev, curr) => prev.concat(prev.map(k => k.concat(curr))), [[]]);

//examples
getSubsets([1, 2]); // [[], [1], [2], [1,2]]
getSubsets([1,2,4]); // [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

28. get indices of a value in an array

```
const indices = (arr, value) => arr.reduce((acc,v,i) => (v === value ? [...acc, i]: acc), []);

// or 
const indices = (arr, value) => arr.map((v, i) => v ===value ? i : false).filter(Boolean);

//examples
indices(['h', 'e', 'l', 'l', 'o'], 'l'); // [2,3]
indices(['h', 'e', 'l', 'l', 'o'], 'w'); // []
```

29. get the average of an array

```
const average = arr => arr.reduce((a, b) => a+b,0) / arr.length;
```

30. get the intersection of arrays

```
const getIntersection = (a, ...arr) => [...new Set(a)].filter(v => arr.every(b => b.includes(v)));

//examples
getIntersection([1,2,3], [2,3,4,5]); // [2,3]
getIntersection([1,2,3],[2,3,4,5],[1,3,5]); // [3]
```

31. get the rank of an array of numbers

```
const ranking = (arr) => arr.map((x,y,z) => z.filter(w => w > x).length + 1);

//examples
ranking([80,65,90,50]); // [2,3,1,4]
ranking([80,80,70,50]); // [1,1,3,4]
ranking([80,80,80,50]); // [1,1,1,4]
```

32. get the sum of an array of numbers

```
const sum = arr => arr.reduce((a, b) => a + b, 0);
```

33. get the unique values of an array

```
const unique = arr => [...new Set(arr)];

//or
const unique = arr => arr.filter((el, i, array) => array.indexOf(el) === i);

//or
const unique = arr => arr.reduce((acc, el) => acc.includes(el)?acc:[...acc, el], []);
```

34. get union of arrays

```
const union = (...arr) => [...new Set(arr.flat())];

//example
union([1,2],[2,3],[3]); // [1,2,3]
```

35. group an array of objects by a key

```
const groupBy = (arr, key) => arr.reduce((acc, item) => ((acc[item[key]] = [...(acc[item[key]] || []), item]),acc),{});

// Example
groupBy([
    { branch: 'audi', model: 'q8', year: '2019' },
    { branch: 'audi', model: 'rs7', year: '2020' },
    { branch: 'ford', model: 'mustang', year: '2019' },
    { branch: 'ford', model: 'explorer', year: '2020' },
    { branch: 'bmw', model: 'x7', year: '2020' },
], 'branch');

/*
{
    audi: [
        { branch: 'audi', model: 'q8', year: '2019' },
        { branch: 'audi', model: 'rs7', year: '2020' }
    ],
    bmw: [
        { branch: 'bmw', model: 'x7', year: '2020' }
    ],
    ford: [
        { branch: 'ford', model: 'mustang', year: '2019' },
        { branch: 'ford', model: 'explorer', year: '2020' }
    ],
}
*/
```

36. merge two arrays

```
// merge but don't remove the duplications
const merge = (a, b) => a.concet(b);

//or
const merge = (a, b) => [...a, ...b];

// merge and remove the duplications
const merge = [...new Set(a.concet(b))];

//or 
const merge = [...new Set([...a, ...b])];
```

37. partition an array based on a condition

```
const partition = (arr, criteria) => arr.reduce((acc,i) => (acc[criteria(i) ? 0 : 1].push(i), acc), [[],[]]);

// example
partition([1,2,3,4,5],n=>n%2); //[[2,4],[1,3,5]]
```

38. remove duplicate values in an array

```
const removeDuplicate = arr => arr.filter(i=> arr.indexOf(i) === arr.lastIndexOf(i));

// example
removeDuplicate(['h', 'e', 'l', 'l', 'o', 'w', 'o', 'r', 'l', 'd']); // ['h', 'e', 'w', 'r', 'd']
```

39. remove falsy values from array

```
const removeFalsy = arr => arr.filter(Boolean);

// example
removeFalsy([0,'a string', '', NaN, true, 5, undefined, 'another string', false]); // ['a string', true, 5, 'another string']
```

40. shuffle an array

```
const shuffle = arr => arr.map(a => ({sort: Math.random(), value: a})).sort((a, b) => a.sort-b.sort).map(a=>a.value);

//or 
const shuffle = arr => arr.sort(() => .5-Math.random());

//example
shuffle([1,2,3,4,5,6,7,8,9,10]); // [9,10,1,6,8,5,2,7,4,3]
```
