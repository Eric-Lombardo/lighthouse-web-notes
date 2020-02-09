# day 5

## troubleshooting guide
* pseudo-code
* google error message
* actually read error message
* double-check syntax
* lint your code
* pair program or perr-review
* rubber duck the problem

## recursion
``` javascript
1.| function countEvenToTwelve(number) {
2.|   if (number <= 12) { // Recursive Case
3.|     console.log(number);
4.|     // The function will call itself again and get closer to the base case
5.|     countEvenToTwelve(number+2);
6.|   }
7.|   // Base case, do nothing when number > 12
8.| }
9.| countEvenToTwelve(0);
```

* in recursion there us a base case and a recursion case.
  * base case: when the program should stop
  * recursion case: it repeatedly calls itself until base case is reached
* when a problem you are trying to solve is just a smaller function of the bigger problem you should consider recursion