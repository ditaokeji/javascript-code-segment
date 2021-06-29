# array篇（一）

1. cast a value as array

```
    const castArray = Array.isArray(value) ? value : [value];

    // examples
    castArray(1); // [1]
    castArray([1,2,3]); //[1,2,3]
```

2. check if an array is empty

```
    const isEmpty = arr => !Array.isArray(arr) || arr.length ===0;

    //examples
    isEmpty([]); //true;
    isEmpty([1,2,3]); //false
```

3. clone an array

```
    const clone = arr => arr.slice(0);

    //or 
    const clone = arr => [...arr];

    //or 
    const clone = arr => Array.from(arr);

    //or 
    const clone = arr => arr.map(x=>x);

    //or 
    const clone = arr => JSON.parse(JSON.stringify(arr));

    //or 
    const clone = arr => arr.concat([]);
```

4. compare two arrays

```
    const isEqual = (a,b) => JSON.stringify(a) === JSON.stringify(b);

    //or
    const isEqual = (a, b) => a.length === b.length && a.every((v, i) => v===b[i]);

    //examples
    isEqual([1,2,3], [1,2,3]); //true
    isEqual([1,2,3], [1,'2',3]); //false
```

5. compare two arrays regardless of order

```
    const isEqual = (a, b) => JSON.stringify(a.sort()) === JSON.stringify(b.sort());

    //examples
    isEqual([1,2,3], [1,2,3]); //true
    isEqual([1,2,3], [1,3,2]); //true
    isEqual([1,2,3], [1,'2',3]); //false
```

6. convert an array of objects to a single object

```
   const toObject = (arr, key) => arr.reduce((a, b) => ({...a, [b[key]]:b}), {});

   //example
   toObject(
       [
           {id:'1',name:'alpha', gender:'male'},
           {id:'2',name:'bravo', gender:'male'},
           {id:'3',name:'charlie', gender:'male'},
       ],
       'id'
   );
   /**
    {
        '1':{id:'1',name:'alpha', gender:'male'},
        '2':{id:'2',name:'bravo', gender:'male'},
        '3':{id:'3',name:'charlie', gender:'male'},
    }
   */
```

7. convert an array of string to numbers

```
    const toNumbers = arr => arr.map(Number);

    //or 
    const toNumbers = arr => arr.map(x => +x);

    //example
    toNumbers(['2', '3', '4']); // [2,3,4]
```

8. count by the properties of an array of objects

```
    const countBy = (arr, prop) => arr.reduce((prev, curr) => (prev[curr[prop]] = ++prev[curr[prop]] || 1, prev), {});

    //example
    countBy([
        { branch: 'audi', model: 'q8', year: '2019' },
        { branch: 'audi', model: 'rs7', year: '2020' },
        { branch: 'ford', model: 'mustang', year: '2019' },
        { branch: 'ford', model: 'explorer', year: '2020' },
        { branch: 'bmw', model: 'x7', year: '2020' },
    ], 'branch');

    //{ 'audi': 2, 'ford': 2, 'bmw': 1 }
```

9. count the occurrences of a value in an array

```
    const countOccurrences = (arr, val) => arr.reduce((a, v) => (v===val?a+1:a),0);

    //or 
    const countOccurrences = (arr, val) => arr.filter(item => item===val).length;

    //examples
    countOccurrences([2,1,3,3,2,3],2); // 2
    countOccurrences(['a','b','a','c','a','b'],'a'); // 3
```

10. count the occurrences of array elements

```
    const countOccurrences = arr => arr.reduce((prev, curr) => (prev[curr] = ++prev[curr] || 1, prev),{});

    //examples
    countOccurrences([2,1,3,3,2,3]); // { '1': 1, '2': 2, '3': 3 }
    countOccurrences(['a','b','a','c','a','b']); // { 'a': 3, 'b': 2, 'c': 1 }
```

11. create an array of cumulative sum

```
    const accumulate = arr => arr.map((sum => value => sum += value)(0));

    //or 
    const accumulate = arr => arr.reduce((a, b, i) => i===0?[b]:[...a,b+a[i-1]],[]);

    //or
    const accumulate = arr => arr.reduce((a,b,i)=> i===0?[b]:[...a,b+a[i-1]],0);

    //example
    accumulate([1,2,3,4]); // [1,3,6,10]
```

12. create an array of numbers in the given range

```
    const range = (min, max) => [...Array(max - min +1).keys()].map(i=>i+min);

    //or
    const range = (min, max) => Array(max - min +1).fill(0).map((_,i)=>min+i);

    //or 
    const range = (min, max) => Array.from({length:max-min+1},(_,i)=>min+i);

    //example
    range(5,10); // [5, 6, 7, 8, 9, 10]
```

13. create cartesian product

```
    const cartesian = (...sets) => sets.reduce((acc, set) => acc.flatMap(x => set.map(y=>[...x,y])),[[]]);

    // example
    cartesian([1,2],[3,4]); // [[1,3],[1,4],[2,3],[2,4]]
```

14. empty an array

```
    const empty = arr => arr.length = 0;

    //or 
    arr = [];
```

15. find the closest number from an array

```
    const closest = (arr, n) => arr.reduce((prev, curr) => Math.abs(curr - n) < Math.abs(prev - n) ? curr : prev);

    //or 
    const closest = (arr, n) => arr.sort((a,b)=>Math.abs(a-n)-Math.abs(b-n))[0];

    //example
    closest([29,87,8,78,97,20,75,33,24,17], 50); // 33
```

16. find the index of the last matching item of an array

```
    const lastIndex = (arr, predicate) => arr.reduce((prev, curr, index) => predicate(curr) ? index:prev, -1);

    //or
    const lastIndex = (arr, predicate) => arr.map(item => predicate(item)).lastIndexOf(true);

    //example
    lastIndex([1,3,5,7,9,2,4,6,8],i => i%2===1); // 4
    lastIndex([1,3,5,7,9,8,6,4,2],i => i > 6); // 5
```

17. find the index of the maximum item of an array

```
    const indexOfMax = arr => arr.reduce((prev, curr, i, a) => curr > a[prev] ? i : prev, 0);

    //example
    indexOfMax([1,3,9,7,5]); // 2
    indexOfMax([1,3,7,7,5]); // 2
```

18. find the index of the minimum item of an array

```
    const indexOfMin = arr => arr.reduce((prev, curr, i, a) => curr < a[prev] ? i : prev, 0);

    //examples
    indexOfMin([6,4,8,2,10]); // 3
    indexOfMin([6,4,2,2,10]); // 2
```

19. find the length of the longest string in an array

```
    const findLongest = words => Math.max(...(words.map(el => el.length)));

    //example
    findLongest(['always', 'look', 'on', 'the', 'bright', 'side', 'of', 'life']); // 6
```

20. find the maximum item of an array

```
    const max = arr => Math.max(...arr);
```