# w4-d5

## logarithm
* this is the inverse of an exponetial function on a graph. see [here](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.intmath.com%2Fblog%2Fmathematics%2Fhow-to-find-the-equation-of-a-logarithm-function-from-its-graph-11988&psig=AOvVaw2L38SRlMyH3Sk2XmP3hgzS&ust=1583028062731000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCMiZ6ZzV9ecCFQAAAAAdAAAAABAD)
* in computer science we use log with a base of 2. so what number exponent gives us the length of an array for example
```js
n     | log2n
===============
1     | 0
2     | 1 ... 2^1
4     | 2 ... 2^2
8     | 3 ... 2^3
16    | 4 ... 2^4
==================
"where n is the size of an array"
```

## algorithms
* algorithimic complexity is all about how fast or slow a particular algorithm is.
* since:
  1. running `num1 + num2` can be 0.001s on anew iphone or 0.5s on a raspberry pi we can't rely on time to measure this
  2. we measure the speed by counting the number of elemetray operations

## elementray operations
* these are some examples:
1. `let number = 0`
1. `number += 2`
1. `console.log(number)`
* elementrary operations is any operation that takes a fixed amount of the time to perform
* ex: `num1 + num2` no matter what these 2 variables are the run time will always be 1
  * `2+2` or `2222+2222` came thing
  * same thign for `console.log(value)` ... value can be anything so runtime is 1
* all elemntray operations are a fixed time

## time complexity
* this is estimated by counting the number of elementrary operations. 
* time complexity = run time
* when determinging the complexity of an algo we are only concerned with the worst case scenario

## algos and runtime
* algos that loop through array like a for loop takes `n` time because we say the data being looped over is n-size

## binary search
* this is when we need to search somethign in a set of ordered data (CS50 phonebook example)
* always cuttign the search in half until data is found
* to check how many guesses a binary search would take calculate `log2n` and add 1, then round down if its not a clean integer.
* example:
```js
//array size of 1000
// log(2)1000 = 9.97 + 1 = 10.97 ... 10
// so at most 10 guesses for array of 1000
```

## binary vs linear search
data = [1, 2, 3, 4, 5]
* linear search: 1, 2, 3, 4, 5
* binary search: 3, then (5 or 1), then (2 or 4)

## n^2 runtime
* when you see n^2 in your runtime it always means that the time complexity will be exponetially worse as n grows
* nested for loops cause n^2
```js
for loop {     // code here runs n-times
  for loop {    // code here runs n^2 times

  }
}
```
```js
for loop {     // code here runs n-times
  for loop {    // code here runs n^2 times
    for loop {
      // code here runs n^3 times
    }
  }
}
```
* the above assumes youa re looping through the same array. however if looping through 2 separate arrays its not:
  1. n * n ... but,
  2. a * b ... where a is length of arrayA and b is length of arrayB

## Big O
* as we increase the amount of data does the algo grow linearly, exponetially or logarithmically
* when evaluating an algo using big O:
  1. we only care about arbitrarily large output
  1. we drop the non-dominat terms
    * (n^2 + n)/2 ... the n^2 was hurting us not the n or the 2
    * we only care about the highest order term
  3. we drop constant terms (n^3/2) or (n^3*2) has the same graph as n^3 kinda so we drop the constant 2
    * 2n + 3 > linear so O(n)
    * 100n^2 > exponetial so O(n^2)
    * logN + 10000 > logarithm so O(logN)
* we dont care about 100 operations as a computer will spit out the results of 1 or 100 opertions at the same time-ish. Big O notation focuses on how an algo performs when its given a large input

## constant time
* constant time algos run in O(1)
example:
1. `arr[2] // is time 1`
1. `arr[1] + arr[2] + arr[3] // is time 1 + 1 + 1 ... so its still O(1)`