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
