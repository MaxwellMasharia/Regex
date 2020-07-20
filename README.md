# **Regex in Javascript**

## `expr.test()`

- The `.test()` function is used to test if a string matches a regex expression

```js
const sentence = "This is a cat";
const expr = /cat/;
console.log(expr.test(sentence)); // Prints : true
```

## **Piping | OR**

- You can match a given sentence against multiple expressions

```js
const sentence = "I have a cat and a dog";
const expr = /cat|dog/;
console.log(expr.test(sentence)); // Prints : true
```

## **Ignore Cases**

- Regex is case sensitive
- Add the `i` flag so as to ignore case

```js
const str = "Maxwell";
const expr = /maxwell/i;
console.log(expr.test(str)); // Prints : true
```

## `str.match(expr)`

- You can extract the matched value using the `.match()` function

```js
const str = "Chickens lay eggs";
const expr = "kens";
console.log(str.match(expr)); // Prints : [ 'kens', index: 4, input: 'Chickens lay eggs', groups: undefined ]
```

- You can get all the matching values using the `g` flag

```js
const str = "John John Doe John";
const expr = /John/g;
console.log(str.match(expr)); // Prints : [ 'John', 'John', 'John' ]
```

## **Period**

- You can use the `.` symbol to represent anything
  - `/.abc/` - Anythings that ends with abc
  - `/abc./` - Anything that starts with abc

```js
const str = "I love mangoes";
const expr = /lo./; // Represents anything that starts with lo and ends in any character
console.log(str.test(expr)); // Prints : [ 'lov', index: 2, input: 'I love Mangoes', groups: undefined ]
```

## **Multiple Possibilities**

- You can test for multiple possibilities using `[]`

```js
const str = "boy biy bay";
const expr = /b[oia]y/; // Starts with b ends with y , Middle is either o,i,a
console.log(str.match(expr)); // Prints : [ 'big', 'bog', 'bug' ]
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
console.log(str.match(expr)); // Prints : ['T', 'h', ' ',' ', 'e', 'p','c']
```

## **Multiple Occurrences**

- You can test if a character appears one or more times using `+`

```js
const name = "Mississipi";
const expr = /s+/g;
console.log(str.match(expr)); // Prints : ["ss","ss"]

// Test for 0 or more time
const str = "Aaaaaaargh";
const expr = /Aa*/; // Test for A then for a appearing zero or more times
console.log(str.match(expr)); // Prints : Aaaaaaa
```

## **Greedy and Lazy Matching**

- A `greedy` match finds the longest possible match while a `lazy` match finds the shortest match

```js
/**
 * @Example of a greedy match - Finds the longest match
 */
const str = "Titanic";
const expr = /t[a-z]*i/gi; // Test for a word that starts with t, has any number of chars (a-z)between ,ends with i
console.log(str.match(expr)); // Prints : "Titani"

/**
 * @Example of a lazy match - Finds the shortest match
 */
const str = "Titanic";
const expr = /t[a-z]*?i/gi; // Test for a word that starts with t, has the least number of chars (a-z)between ,ends with i
console.log(str.match(expr)); // Prints : [ 'Ti', 'tani' ]
```

## **Matching Beginning String Patterns**

- Use the `^` char without brackets to test for the beginning of a string

```js
const str = "This is epic";
const expr = /^This/;
console.log(expr.test(str)); // Prints : true
```

## **Matching Ending String Patterns**

- Use the `$` char to test for the ending of a string

```js
const str = "This is a dog";
const expr = /dog$/;
console.log(expr.test(str)); // Prints : true
```

## **Matching All Letters And Numbers**

- Use `\w` to test for any character a-z/i, 0-9,and `_`

```js
const str = "<h1>This is _ ebic</h1>";
const expr = /\w/g;
console.log(str.match(expr)); // Prints : ['h', '1', 'T', 'h','i', 's', 'i', 's','_', 'e', 'b', 'i','c', 'h', '1']
```

- Use`\W` to test for the opposite

## **Math All The Numbers**

- _Use `\d` to test for all the numbers_

```js
const str = "<h1>Thi0s is 4_ eb4i6c</h1>";
const expr = /\d/g;
console.log(str.match(expr)); // Prints : [ '1', '0', '4', '4', '6', '1' ]
```

- _Use `\D` to test for the opposite_

## _@Example Username Validator_

```js
/**
 * @example Username validator
 *  If there are numbers they must be at the end
 *  Letters can be uppercase or Lowercase
 *  The name should be at least two letters long, Two letter names cant have numbers
 */

const name = "JackOfTrades00";
const expr = /^[a-zA-Z]{2,}\d*$/; // {n,m} : This represents the min and the max number of matches

console.log(expr.test(name));
console.log(name.match(expr));
```
