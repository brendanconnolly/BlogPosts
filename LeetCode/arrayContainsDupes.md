Working through these challenges on [LeetCode](https://leetcode.com) is an interesting experience. I try to solve the problems or at least think an approach through prior to hitting the docs and as a last result searching for solution specifics. Mostly to try and stretch my knowledge while working through the challenges. This was a fun one as the difficulty wasn't too frustrating and provided a few different possible solutions.

The challenge this time is:


> Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

> Example :
- Input: nums = [1,2,3,1]
- Output: true
> Constraints:
- 1 <= nums.length <= 10^5
- -10^9 <= nums[i] <= 10^9

I love the [MDN](https://developer.mozilla.org/en-US/) docs, I knew of [indexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) and I was curious if there were any parameters I could use to solve this challenge. What I discovered was [lastIndexOf](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf). Using these two methods, finding duplicates is only a matter of comparing the indices of the first and last instances of the value.

```js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    for(let i=0;i<nums.length;i++){
        let current= nums[i];
        let firstIndex= nums.indexOf(current);
        let lastIndex= nums.lastIndexOf(current);
        if(firstIndex!=lastIndex){
            return true;
        }
    }
    return false
};
```

## Alternatives
I was happy to see my solution was passing all tests but while *lastIndexOf* was useful it seemed like there were likely other more standard solutions. 

### Using Slice & Includes
I decided to try a combination of using *slice* and *includes*
- Use slice to create a new array with only the values after the current value
- Use includes to check for the current value inside the new array.

Initially I was concerned about duplicates present before the current position. Using the same logic of *slice* and *includes*, I checked both the array of values before after the current position. This failed the challenges time/performance constraint. Then I realized it wasn't even a necessary concern, since I was iterating through the whole array the before values has already been checked. 

When run without the before values checked this solution also was accepted. 

```js 
var containsDuplicate = function(nums) {
    for(let i=0;i<nums.length;i++){
        let current= nums[i];
        let arrayAfter= nums.slice(i+1, nums.length);
        if(arrayAfter.includes(current)){
            return true;
        }
    }
    return false
};
```
### Using a Set

I spent a little time after searching for other solutions to see how I felt mine fit in. I found this [post by Will Harris](https://dev.to/will_devs/javascript-how-to-check-if-an-array-has-duplicate-values-cha) and found his solution using the javascript [Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) object. I've looked at sets before but haven't had much chance to use them, since each value in a set need to be unique, its going to filter out any duplicates in the array. The solution worked and looked very clean.

```js 
var containsDuplicate = function(nums) {
    return new Set(nums).size!=nums.length
};
```

