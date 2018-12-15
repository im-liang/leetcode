## Description

You are standing at position 0 on an infinite number line. There is a goal at position target.

On each move, you can either go left or right. During the n-th move (starting from 1), you take n steps.

Return the minimum number of steps required to reach the destination.

## Example

```
Input: target = 3
Output: 2
Explanation:
On the first move we step from 0 to 1.
On the second step we step from 1 to 3.
```

```
Input: target = 2
Output: 3
Explanation:
On the first move we step from 0 to 1.
On the second move we step  from 1 to -1.
On the third move we step from -1 to 2.
```

#### Note

target will be a non-zero integer in the range [-10^9, 10^9].


## Solution

``` Java
class Solution {
    public int reachNumber(int target) {
      target = Math.abs(target); // number symmetrical -2,-1,0,1,2
      int step = 0;
      while(target > 0) {
        target -= ++step;
      }
      
      // need to change sign at offset/2
      // if offset is even, just change at offset/2 since sign change -> change sum by even number, change sign at i lost 2i (ex: 4 => 0,-1,1,4)
      
      // offset is odd, keep going until you are over by even number since you can set the subset to 0 (ex: 5 => 0,1,3,0,5)
      return target % 2 == 0 ? step : step + 1 + step % 2;
    }
}
```

