# **Regex in Javascript**

## `expr.test()`

- The `.test()` function is used to test if a string matches a regex expression

```js
const sentence = "This is a cat";
const expr = /cat/;
console.log(expr.test(sentence)); // Prints true
```

## **Piping | OR**

- You can match a given sentence against multiple expressions

```js
const sentence = "I have a cat and a dog";
const expr = /cat|dog/;
console.log(expr.test(sentence)); // Prints true
```

## **Ignore Cases**

- Regex is case sensitive
- Add the `i` flag so as to ignore case

```js
const str = "Maxwell";
const expr = /maxwell/i;
console.log(expr.test(str)); // Prints true
```

## `str.match(expr)`

- You can extract the matched value using the `.match()` function

```js
const str = "Chickens lay eggs";
const expr = "kens";
console.log(str.match(expr)); // Prints [ 'kens', index: 4, input: 'Chickens lay eggs', groups: undefined ]
```

- You can get all the matching values using the `g` flag

```js
const str = "John John Doe John";
const expr = /John/g;
console.log(str.match(expr)); // Prints [ 'John', 'John', 'John' ]
```

## **Period**

- You can use the `.` symbol to represent anything
  - `/.abc/` - Anythings that ends with abc
  - `/abc./` - Anything that starts with abc

```js
const str = "I love mangoes";
const expr = /lo./; // Represents anything that starts with lo and ends in any character
console.log(str.test(expr)); // Prints [ 'lov', index: 2, input: 'I love Mangoes', groups: undefined ]
```

## **Multiple Possibilities**

- You can test for multiple possibilities using `[]`

```js
const str = "boy biy bay";
const expr = /b[oia]y/; // Starts with b ends with y , Middle is either o,i,a
console.log(str.match(expr)); // Prints [ 'big', 'bog', 'bug' ]
```

## **Ranges**

- You can match a range of letters

```js
const expr = /[a-z]/gi; // All letters a->z
const expr = /[2-6]/g; // All numbers 2->6
const expr = /[a-z0-9]/g; // All numbers 0->9 and letters a->z
```

## **Negated Characters**

- You can ignore certain characters while testing using the `^` char

```js
const str = "This is epic";
const expr = /[^is]/gi;
console.log(str.match(expr)); // Prints ['T', 'h', ' ',' ', 'e', 'p','c']
```

## **Multiple Occurrences**

- You can test if a character appears one or more times using `+`

```js
const name = "Mississipi";
const expr = /s+/g;
console.log(str.match(expr)); // Prints ["ss","ss"]

// Test for 0 or more time
const str = "Aaaaaaargh";
const expr = /Aa*/; // Test for A then for a appearing zero or more times
console.log(str.match(expr)); // Prints Aaaaaaa
```

## Greedy and lazy Matching

