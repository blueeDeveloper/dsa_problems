# dsa_problems

1. Move Zeros at the end of array

```
 const moveZeros = (arr) => {
  let currentCheck = 0;
  for (let i=0; i < arr.length; i++) {
    if(arr[i] !== 0) {
      let val = arr[currentCheck];
      arr[currentCheck] = arr[i]
      arr[i]= val
      
      currentCheck++;
    }
    
  }
  return arr
}

console.log(moveZeros([0,1,0, 3])) // Result --- [1,3,0,0]
```


2. find majority element in the array

The Boyer-Moore Voting Algorithm is one of the most elegant solutions in computer science because it solves a problem that usually requires a lot of memory ($O(n)$) using almost zero extra memory (O(1)).🎯 
The Goal--- Find the Majority Element in an array—an element that appears more than n/2 times.


```
const findMajorityElement = (arr) => {
    let candidate = -1;
    let count = 0;

    for(let i=0; i < arr.length; i++) {
      if(count === 0) {
        candidate = arr[i];
        count++;
      } 
      else if(candidate === arr[i]) {
        count++
      }
      else {
        count--
      }
    }
    
    
    let actualCount = 0;
    for(let i=0; i< arr.length; i++) {
      if(arr[i] === candidate) {
        actualCount++
      }
    }
    
    if(actualCount > Math.floor(arr.length/2)) {
      return candidate
    }  else {
      return -1
    }
}

// Test Cases
console.log(findMajorityElement([1, 1, 2, 3, 3, 5, 3, 3, 3])); // Output: 3
console.log(findMajorityElement([7]));                   // Output: 7
console.log(findMajorityElement([2, 13]));               // Output: -1
```


Same examople can be solved with Hash Map but there is a catch. space complexity increases O(n)

```
const findMajorityElement = (arr) => {
    let counts = new Map();
    for (let num of arr) {
      counts.set(num, (counts.get(num) || 0) + 1)
      if(counts.get(num) > arr.length/2) {
        return num
      }
    }
    
    return -1
    
}

// Test Cases
console.log(findMajorityElement([1, 1, 2, 3, 3, 5, 3, 3, 3])); // Output: 3
console.log(findMajorityElement([7]));                   // Output: 7
console.log(findMajorityElement([2, 13]));               // Output: -1

```



3. Remove duplicates from sorted array

```
const removeDuplicates = (arr) => {
    if(arr.length === 0) return arr;
    let i = 0;
    for (let j=1; j< arr.length; j++) {
      if(arr[j] !== arr[i]) {
        i++
        arr[i] = arr[j]
      }
    }
    return i+1
}

let myArr = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4];
let k = removeDuplicates(myArr);

console.log(k); // Output: 5
console.log(myArr.slice(0, k)); // Output: [0, 1, 2, 3, 4]
```

4. The Best Time to Buy and Sell Stock- It is a classic interview question. The goal is to find the maximum profit you can make by buying a stock on one day and selling it on a future day.

```
const maxProfit = (prices) => {
    let minNumber = Infinity;
    let maxProfit = 0;
    for (let i=0; i< prices.length; i++) {
      if(prices[i] < minNumber) {
        minNumber = prices[i]
      }
      else if(prices[i] - minNumber > maxProfit) {
        maxProfit = prices[i] - minNumber
      }
    }
    
    return maxProfit
};

// Example Usage:
const dailyPrices = [7, 1, 5, 3, 6, 4];
console.log(maxProfit(dailyPrices)); // Output: 5 (Buy at 1, Sell at 6)
```
