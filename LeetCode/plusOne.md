![js coding challenge](http://www.brendanconnolly.net/wp-content/uploads/2021/07/JavaScript-Coding-Challenge.png)

Working through these challenges on [LeetCode](https://leetcode.com) is an interesting experience. Some have been pretty challenging like [rotating an array](http://www.brendanconnolly.net/code-challenge-rotate-an-array/) and some have felt more relatable and straight-forward to solve like finding[the best time to buy and sell stock](http://www.brendanconnolly.net/code-challenge-best-time-to-buy-and-sell-stock/). The range of feelings has been interesting, progress hasn't been linear but I am enjoying working through them and do believe its helping me level up in javascript.  

The challenge this time is:


> You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

> Increment the large integer by one and return the resulting array of digits.

> Example
- Input: digits = [1,2,3]
- Output: [1,2,4]

> Constraints:
- 1 <= digits.length <= 100
- 0 <= digits[i] <= 9
- digits does not contain any leading 0's.

## Using Join and Split

I felt like I had a pretty good approach in mind after reading the problem. I would use [join](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) to convert the elements of the array into a single string with all the values. Then I can cast that string into a numeric form using the constructor on [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/Number) and add 1 to it. 

Now, that I had the new number, I cast it to a string. Then using [split](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split) with an empty string as the separator, I have an array of the individual characters that I can then return.

```js
var plusOne = function(digits) {
    let digitsJoined=digits.join('');
    let digitsNumber=Number(digitsJoined)+1;
    return digitsNumber.toString().split('');
};
```

This worked for most cases but failed when the numeric value represented by the string exceeded the integer max value. 

## Handling Numbers Beyond Integer Max 
To handle these larger values, I needed to replace *Number* with an object that can handle numbers larger than the [Number.MAX_SAFE_INTEGER](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER) *9007199254740991*.

This took 2 small changes:
- use the [BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt/BigInt) constructor instead of Number
- Replace `1` with `1n` so it would be treated as a BigInt literal value

```js
var plusOne = function(digits) {
    let digitsJoined=digits.join('');
    let digitsNumber=BigInt(digitsJoined)+1n;
    return digitsNumber.toString().split('');
};
```

This passed the test suite but technically the members of the array were strings in the last example. To clean that up, I mapped over the array and cast each value to a number. 

```js
var plusOne = function(digits) {
    let digitsJoined=digits.join('');
    let digitsNumber=BigInt(digitsJoined)+1n;
    return digitsNumber.toString().split('').map(x=>Number(x));
};
```

Something I am noticing in doing these challenges is that the style of code needed to complete them effects my ability to solve them. 

This challenge and some others have been fairly intuitive although I suppose knowing [join](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) and [split](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split) helps. However, when solutions require using creating separate loops and manipulating the index positions within the loops I hit a wall. Code like that is something I've grown to be suspicious of, and having a background in testing I'd have some questions about implementation choices.

Through this process, what I am learning is a deeper understanding of the javascript built in objects and functions. Not just what exists and how I can use them, but what those methods are doing under the hood. It's helping me question how well I understand the code I am writing at a deeper level. 
