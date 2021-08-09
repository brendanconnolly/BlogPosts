![js coding challenge](http://www.brendanconnolly.net/wp-content/uploads/2021/07/JavaScript-Coding-Challenge.png)

As someone that has jumped stacks a couple times in the last few years, I'm productive in multiple languages but I miss the level of mastery I felt when I had focused effort on a single language for an extended period of time. I work in javascript these days and I love it, and would like to level up so I decided to work through challenges on [LeetCode](https://leetcode.com). 

To help solidify learnings I'll be blogging my progress through the challenges. This the second challenge and I felt like I hit the groove pretty quickly.  

> You are given an array prices where prices[i] is the price of a given stock on the ith day.

> Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

> Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

> Constraints:
- 1 <= prices.length <= 3 * 10^4
- 0 <= prices[i] <= 10^4


I took a bit more time upfront looking at a few of the test cases the solution would be run through. This helped me spot a pattern that I thought would get me pretty close. This is another example of using a [2 pointer technique](https://algodaily.com/lessons/using-the-two-pointer-technique), the current price and the next price. It can be easy to get in your head a bit and over think things though.

I started with variables for what i knew I would need to store:
- **profit** to hold the accumulated earnings
- **buyPrice** to capture the last price bought at
- **sellingTime** a flag to indicate whether I was in buy or sell mode.

For buying the logic is pretty simple, only buy when the current price is lower than the next price. This guarantees a sale for profit in future iterations. 

For selling, its all about profit, comparing the last buy price with current and next days price. If there's more profit selling today than selling tomorrow then sell, otherwise wait until tomorrow and check the future again. Since profit of some sort was determined before buying, future iterations will only increase the profit. 

```js
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    let profit=0;
    let buyPrice;
    let sellingTime=false;   

    for(let i=0;i<prices.length;i++){       
        if(i<prices.length-1){
            let currentPrice =prices[i];
            let nextPrice =prices[i+1];
            if(!sellingTime){ //buy mode
                if(currentPrice<nextPrice){
                    buyPrice=currentPrice;
                    sellingTime=true;
                    console.log("bought at ",buyPrice)
                }
            }else{ // selling time
                    // if profit today > tomorrow 
                    const profitToday=currentPrice-buyPrice
                    const profitTomorrow=nextPrice-buyPrice
                    if(profitToday>profitTomorrow){
                        profit+=profitToday;
                        console.log("sold at ",currentPrice)
                        sellingTime=false;
                    }
            }
        }
    }
    return profit;
};
```

That got me pretty close, but I ran into an issue with *nextPrice* being set incorrectly on the last iteration. To solve this, I default *nextPrice* to the current price and overwrite it the rest of the time. It may be more clear, to invert that logic and only overwrite *nextPrice* in the specific case it needed to be different than usual. 

```js
var maxProfit = function(prices) {
    let profit=0;
    let buyPrice;
    let sellingTime=false;

    for(let i=0;i<prices.length;i++){
        let currentPrice =prices[i];
        let nextPrice =prices[i];
        if(i<prices.length-1){
            nextPrice =prices[i+1];
        } 
            if(!sellingTime){ //buying time
                if(currentPrice<nextPrice){
                    buyPrice=currentPrice;
                    sellingTime=true;
                }
            } else{ // selling time
                    const profitToday=currentPrice-buyPrice
                    const profitTomorrow=nextPrice-buyPrice
                    if(profitToday>=profitTomorrow){
                        profit+=profitToday;
                        sellingTime=false;
                    }
            }
        }
    return profit;
};
```
This successfully completed the challenge. I was happier with my performance this time than in the last challenge, but it still feels solidly in riddle territory. The challenge was simple once I solved the bulk of the problem, but given more pressure I can see how folks could get stuck. Once again I am grateful for the test suite to help guide my progress. 
