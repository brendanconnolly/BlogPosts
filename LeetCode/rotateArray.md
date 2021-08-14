![js coding challenge](http://www.brendanconnolly.net/wp-content/uploads/2021/07/JavaScript-Coding-Challenge.png)

This the 3rd challenge and I came in with high confidence after getting through the first and second challenges on [LeetCode](https://leetcode.com). I had higher confidence after completing the last challenge to [find the best time to buy and sell stock]() but this one really was definitely tougher.

The challenge was:

> Given an array, rotate the array to the right by k steps, where k is non-negative.

> Example 1:
- Input: nums = [1,2,3,4,5,6,7], k = 3
- Output: [5,6,7,1,2,3,4]

> Explanation:
- rotate 1 steps to the right: [7,1,2,3,4,5,6]
- rotate 2 steps to the right: [6,7,1,2,3,4,5]
- rotate 3 steps to the right: [5,6,7,1,2,3,4]

## Using Splice
I was looking to pop the last value off the array, then push it onto the front of the array. My first thought was to pop the last value then use the spread (...) operator and re-assign the new array to *nums*.

```js
nums= [nums.pop(),...nums]
```
This works, but probably isn't the most efficient, the challenge also expects you to do the operation on the array in place and blocks the re-assignment. 

Rather than spread, I turned to [splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice). Splice accepts the start position, the number of items in the array to remove and the item(s) to add to the array. 

For the challenge, again I used pop to remove the last item in the array. Then use *splice* to insert the value popped off the array at the beginning.

```js

/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    for(let i=0; i<k;i++){
        let lastValue=nums.pop();
        nums.splice(0,0, lastValue)
    }
    
};
```

This worked, but did not pass the performance criteria on the challenge. It felt like I was on the right track but I thought perhaps there might be another similar array method that might be more optimized. 

## Using Unshift

[Unshift](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) looked like a solid choice. It provided similar functionality to *splice* but more specialized since it is meant to add items to the beginning of an array. 

The implementation looks pretty similar, and being concise it felt and looked like a good solution. Unfortunately, it passed all tests but the last and largest input array, failing due to performance constraints. 

```js
var rotate = function(nums, k) {
    for(let i=0;i<k;i++){
        const lastVal=nums.pop();
        nums.unshift(lastVal)
    }
};
```

## Searching for the Answer
At this point I decided to turn to a google search to see other solutions to meet the performance standards of this challenge. However, it took a bit pf time searching to actually find [s solution](https://dev.to/urfan/leetcode-rotate-array-with-javascript-3j5h). I found many more instances of solutions similar to my previous iterations, this gave me some sense of validation that I wasn't alone on this one. 

```js
var rotate = function(nums, k) {
   
    var reverse = function(nums, start, end) {
        while (start < end) {
            var temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start ++;
            end --;
        }
    }
    //reduce 
    k = k % nums.length
    console
    reverse(nums, 0, nums.length - 1)
    reverse(nums, 0, k-1)
    reverse(nums, k, nums.length - 1)
};

```

I had to visualize this for it to click for me, essentially what we are doing is a twisting values as we step through the contents of the array stepping towards the center. 
This is done in 3 passes through the *reverse* function:
- reverse the full contents of the array
- reverse the first third contents
- reverse the last third contents

```
nums=[1,2,3,4,5,6,7],k=3
0-6 => [7,2,3,4,5,6,1]=>[7,6,3,4,5,2,1]=>[7,6,5,4,3,2,1]
0-2 => [7,6,5,4,3,2,1]=>[5,6,7,4,3,2,1]
3-6 => [5,6,7,4,3,2,1]=>[5,6,7,1,3,2,4]=>[5,6,7,1,2,3,4]

```
It's an elegant solution. Efficiently reverse everything one time, then only manipulate the head and tail sections to get teh final desired state. I feel smarter having worked through this challenge, my brain took on a new wrinkle or 2. That said, this was tough, and looking at the code I'd be pretty suspicious if I saw a solution like this when reviewing a change request. I've read that this (or in similar forms) is a common challenge in interviews, which I find a bit concerning. I can see why it would be helpful to know, but in my opinion this is library code. Code that is heavily optimized, efficient by default, so people don't attempt to recreate the wheel and shoot themselves in the foot. 

This is why I struggled to accept that solutions that concisely used javascript built in methods on *Array* were not ideal. I can see how that difference in recognition may give insight into my experience level as a developer, but I also fail to see its predictive power for most general cases. 

