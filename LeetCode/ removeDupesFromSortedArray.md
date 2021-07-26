![js coding challenge](http://www.brendanconnolly.net/wp-content/uploads/2021/07/JavaScript-Coding-Challenge.png)

As someone that has jumped stacks a couple times in the last few years, I'm productive in multiple languages but I miss the level of mastery I felt when I had focused effort on a single language for an extended period of time. I work in javascript these days and I love it, and would like to level up so I decided to work through challenges on [LeetCode](https://leetcode.com). 

To help solidify learnings I'll be blogging my progress through the challenges.

This was the first challenge question:
> Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

> Since it is impossible to change the length of the array in some languages,
you must instead have the result be placed in the first part of the array nums.
More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result.

> It does not matter what you leave beyond the first k elements.
 Return k after placing the final result in the first k slots of nums.

>Do not allocate extra space for another array. 
You must do this by modifying the input array in-place with O(1) extra memory.

>Constraints:
- 0 <= nums.length <= 3 * 104
- -100 <= nums[i] <= 100
- nums is sorted in non-decreasing order.


```js
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

```
Example :
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
```

## Getting Started

I knew I'd need to iterate through the array, taking the current index value as well as peek ahead one position to compare against. If the 2 values matched:
- set the look ahead value to a control value ("_")
- increment a count of the duplicates to return

Then sort the array and return the count of duplicates. I knew this wouldn't be perfect but it helps to get something in place and iterate. I'm learning this may be a flawed approach, but its how I tend to start since that blank editor can be a real hurdle to get over.

```js
var removeDuplicates = function(nums) {
    let dupeCount=0;
    for(let i=0;i<nums.length;i++){
        let currentVal= nums[i];
        let nextVal= nums[i+1];
        if(currentVal==nextVal){
            nums[i+1]="_"
            dupeCount+=1;
        }
    }
    nums.sort()
    return dupeCount;
};
```

## Iterating Towards a Solution
This was failing, and I realized I was misunderstanding the requirements. This function is meant to mutate the array and return the count of unique numbers or essentialy how far into the mutated array to compare. 

Realizing this, rather than increment a count of duplicates and I decided to start with the length of the array and subtract 1 each time I found a duplicate. 

When a duplicate was detected I would:
-  Replaced it with the control character 
-  Use the default sort method on the array to shift the control characters to the end of the array. 
-  Decrement the loops index to compare the current value with the next array value
-  Decrement the non duplicate count

```js
var removeDuplicates = function(nums) {
    let nonDuplicateCount=nums.length;
    for(let i=0;i<nums.length;i++){
        // get the current value for this position
        let currentVal= nums[i];
        //peek ahead 1 to compare
        let nextVal= nums[i+1];
        // if position underscore skip checking
        if(currentVal!="_") {
            if(currentVal==nextVal){
                nums[i+1]="_"
                //shift the `_` postions to the end of the array
                nums.sort()
                // reset the index position to account for moving dupe
                i-=1;
                nonDuplicateCount-=1;
            } 
        }
    } 
    return nonDuplicateCount;
};
```

## Close But Not Performant

This got me closer, but I ran into issues with negative numbers being sorted incorrectly. This is because while the default behavior of [Array.prototype.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) is ascending, it uses a string based comparison.

I thought the easiest step forward to be a numeric control value rather than a string. I chose **999** since since it is outside the 100 max defined in the challenge constraints. 

Now that all values inside the array are numeric, I could pass a custom compare function to sort by to get the numbers sorted in ascending order:
```js
 nums.sort((a,b) =>a-b); 
``` 
I thought I had this challenge beat, however it was failing because it was exceeding the time limit. The reason was due to  sorting on each iteration. 

## Success!

I knew sorting like that was a cheat, basically using brute force to accomplish the task. 

I set about a changing my implementation so that I would only need to sort the array one time when I was finished iterating the array. 

The resulting solution is much cleaner:
- Track the last non-duplicate value to use to compare the next value with.
- Update the *non-duplicate* value when the current iteration value is not the control value
- When the next value and the *non-duplicate* value match
    -  mark postion as a duplicate
    -  decrement the non duplicate count
- Sort the array using a numeric sort

``` js
var removeDuplicates = function(nums) {
    let nonDupes=nums.length;
    let lastNonDupe=nums[0];
    
    for(let i=0;i<nums.length;i++){
        const currentVal= nums[i];
        const nextVal= nums[i+1];

        if(currentVal!=999){
            //not a dupe so update and use for compare
            lastNonDupe=currentVal;  
        }
        if(lastNonDupe==nextVal){
            nums[i+1]=999;
            nonDupes-=1;
        }
    }
    nums.sort((a,b) =>a-b);
    return nonDupes;  
};
```

I could say this was an *aha moment*, but I don't think thats really true. This is undeniably a better solution, its easier to read and explain as well as being more performant. That said, like many code challenge type problems, I think there is a *riddle* feel to this. Once you know the answer it seems simple, but if you are new to it or don't spend much time manipulating arrays in place it seems more of a difficult challenge. 

Looking back I think one of my main take aways would be to take a more test driven approach, identifying a few test cases even if LeetCode doesn't really have the environment set up for tests. This would have made the feedback cycles faster and made reasoning about the changes easier.

