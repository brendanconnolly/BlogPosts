![js coding challenge](http://www.brendanconnolly.net/wp-content/uploads/2021/07/JavaScript-Coding-Challenge.png)

Working through these challenges on [LeetCode](https://leetcode.com) is an interesting experience. This challenge took more code than I expected. It could be that I missed a more simple or elegant solution. However, like the [Plus One Challenge](http://www.brendanconnolly.net/code-challenge-plus-one/), I felt I had a decent approach to start but I still ended up learning a few things along the way.

The challenge this time is:

> Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:
- Each row must contain the digits 1-9 without repetition.
- Each column must contain the digits 1-9 without repetition.
- Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.

>Note:
- A Sudoku board (partially filled) could be valid but is not necessarily solvable.
- Only the filled cells need to be validated according to the mentioned rules.

> Example:

![board example](http://www.brendanconnolly.net/wp-content/uploads/2021/09/leetcode-sudoku.webp)
```js
Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
```
- Output: true

The trick here is realizing that the validation is the same for rows, columns and sub boards. Each case is still an array of 9 values that should not contain any duplicate values. The validation of each array is independent, if any row, column or sub board has a duplicate then the board is invalid. 

## Handling Columns
The first step was pivoting the values so each column on the board was captured in its own array. To do this I iterated over the rows of the board and each member within the row array populating a new empty board object swapping the row index with the current position in the row array. 
```js
var getEmptyBoard=function(){
    return [[],[],[],[],[],[],[],[],[]];
}

var getColumnValues=function(board){
    let columnsAsRowsBoard=getEmptyBoard();
    board.forEach((row,index)=>{
        for(let i=0; i<row.length; i++){
            columnsAsRowsBoard[i][index]=row[i];
        }
    })
    return columnsAsRowsBoard;
};
```

## Handling Sub Boards

Next I needed to parse each 3x3 sub board into a single array of values. I opted to walk each row and then each value again, pushing each value to the appropriate position on a new empty board.

Each row would need to be split into groups of 3, then those values pushed to different arrays based on their position in the row. The first 3 values going to row 0, the next 3 going to row 1, and the last 3 to row 2. 

This works fine for the first 3 sub boxes, but beyond that I needed to map the rows index to the correct set of sub box arrays. I handled this by creating a `getBoxStartPosition` that would return the correct first position for any set of the 3 rows of sub boxes.

I decided at this point to start purposefully skipping the empty positions with the placeholder value (`.`) by passing the current value to the [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#constructor) constructor. If a placeholder value was encountered it would result in `NaN` and be skipped.

```js
var getSubBoardValues=function( board){
    let subBoardAsRowsBoard=getEmptyBoard();
    
    board.forEach((row,index)=>{
        let startBox=getBoxStartPosition(index)

        for(let i=0;i<row.length;i++){
            const currentValue=row[i]
            if(Number(currentValue)){
                if(i<3){
                    subBoardAsRowsBoard[startBox].push(currentValue)
                }
                if(i>=3 && i<6){
                   subBoardAsRowsBoard[startBox+1].push(currentValue)
                }
                if(i>=6){
                   subBoardAsRowsBoard[startBox+2].push(currentValue)
                }
            }
        }
           
    })
    return subBoardAsRowsBoard;
}

var getBoxStartPosition = function(rowIndex){
    if(rowIndex<3){return 0;}
    if(rowIndex<=5){return 3;} 
    if(rowIndex>5){return 6;}
}
```
## Checking for Duplicates
Now that each set of values is parsed into the same format, I used the spread operator (`...`) to merge the 3 sets of values into one array that I could loop over and check for duplicate values. 

I had already code challenge to check if an [array contains duplicates](http://www.brendanconnolly.net/code-challenge-contains-duplicate) however I opted for a different approach using a for loop and the array [filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) function. 

This worked out since I had inconsistently handled the placeholder values and needed to ignore the `.` values. 

All that is left is looping over the rows and returning *false* at the first row containing a duplicate numeric value.

```js
var isValidSudoku = function(board) {
    const rowsToCheck=[...board,...getColumnValues(board),...getSubBoardValues(board)]
    rowsToCheck.forEach(row=>{
        if(rowHasDupes(row)){
           return false; 
        }
    })
    return true;
}
var rowHasDupes = function(row){
    for(let i=0;i<row.length; i++){
        const currentValue=row[i];
        if(Number(currentValue) && row.filter(x=>x==currentValue).length>1){
            return true;
        }
    }
    return false;
}

var getEmptyBoard=function(){
    return [[],[],[],[],[],[],[],[],[]];
}

var getColumnValues=function(board){
    let columnsAsRowsBoard=getEmptyBoard();
    board.forEach((row,index)=>{
        for(let i=0; i<row.length; i++){
            columnsAsRowsBoard[i][index]=row[i];
        }
    })
    return columnsAsRowsBoard;
};

var getSubBoardValues=function( board){
    let subBoardAsRowsBoard=getEmptyBoard();
    board.forEach((row,index)=>{
        let startBox=getBoxStartPosition(index)

        for(let i=0;i<row.length;i++){
            const currentValue=row[i]
            if(Number(currentValue)){
                if(i<3){
                    subBoardAsRowsBoard[startBox].push(currentValue)
                }
                if(i>=3 && i<6){
                   subBoardAsRowsBoard[startBox+1].push(currentValue)
                }
                if(i>=6){
                   subBoardAsRowsBoard[startBox+2].push(currentValue)
                }
            }
        }
           
    })
    return subBoardAsRowsBoard;
}

var getBoxStartPosition = function(rowIndex){
    if(rowIndex<3){return 0;}
    if(rowIndex<=5){return 3;} 
    if(rowIndex>5){return 6;}
}
```

## Replacing forEach

This all appeared to be fine, however it was failing the submission tests. This is when I learned a new fact about the array
[forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) function.

I was using `forEach` to loop over all the row data and attempting to return early if any row had duplicates. To quote the MDN Docs the problem is: 
> `forEach()` executes the callbackFn function once for each array element; unlike map() or reduce() it always returns the value undefined and is not chainable. 

This meant my early exit was ignored, once I replaced it with a regular for loop the submission passed tests and was accepted.

```js
var isValidSudoku = function(board) {

    const rowsToCheck=[...board,...getColumnsAsRows(board),...getSubBoardAsRows(board)]
    for(let r=0; r<rowsToCheck.length;r++){
        let row=rowsToCheck[r]
        if(rowHasDupes(row)){
           return false; 
        }
    }
    return true;
}
var rowHasDupes = function(row){
    for(let i=0;i<row.length; i++){
        const currentValue=row[i];
        if(Number(currentValue) && row.filter(x=>x==currentValue).length>1){
            return true;
        }
    }
    return false;
}

var getEmptyBoard=function(){
    return [[],[],[],[],[],[],[],[],[]];
}

var getColumnsAsRows=function(board){
    let columnsAsRowsBoard=getEmptyBoard();
    board.forEach((row,index)=>{
        for(let i=0; i<row.length; i++){
            columnsAsRowsBoard[i][index]=row[i];
        }
    })
    return columnsAsRowsBoard;
};

var getSubBoardAsRows=function( board){
    let subBoardAsRowsBoard=getEmptyBoard();
    board.forEach((row,index)=>{
        let startBox=getBoxStartPosition(index)

        for(let i=0;i<row.length;i++){
            const currentValue=row[i]
            if(Number(currentValue)){
                if(i<3){
                    subBoardAsRowsBoard[startBox].push(currentValue)
                }
                if(i>=3 && i<6){
                   subBoardAsRowsBoard[startBox+1].push(currentValue)
                }
                if(i>=6){
                   subBoardAsRowsBoard[startBox+2].push(currentValue)
                }
            }
        }
    })
    return subBoardAsRowsBoard;
}

var getBoxStartPosition = function(rowIndex){
    if(rowIndex<3){return 0;}
    if(rowIndex<=5){return 3;} 
    if(rowIndex>5){return 6;}
}
```

I could continue to refine and optimize this solution. Including amongst other things consolidating the parsing of the board object. Handling pivoting the rows into columns and the sub boards inside one pass, as well as removing the need to handle the placeholder values(`.`) in the `hasDupes` function. However, since this passes the challenge and each function reads reasonably well I'm not going to spend the time continuing to work the problem.
