# [875\. Koko Eating Bananas](https://leetcode.cn/problems/koko-eating-bananas/)

## Description

Difficulty: **中等**  

Related Topics: [Array](https://leetcode.cn/tag/array/), [Binary Search](https://leetcode.cn/tag/binary-search/)


Koko loves to eat bananas. There are `n` piles of bananas, the i<sup>th</sup> pile has `piles[i]` bananas. The guards have gone and will come back in `h` hours.

Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return _the minimum integer_ `k` _such that she can eat all the bananas within_ `h` _hours_.

**Example 1:**

```
Input: piles = [3,6,7,11], h = 8
Output: 4
```

**Example 2:**

```
Input: piles = [30,11,23,4,20], h = 5
Output: 30
```

**Example 3:**

```
Input: piles = [30,11,23,4,20], h = 6
Output: 23
```

**Constraints:**

*   1 <= piles.length <= 10<sup>4</sup>
*   piles.length <= h <= 10<sup>9</sup>
*   1 <= piles[i] <= 10<sup>9</sup>


## Solution

Language: Java

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int left = 1, right = 1000000000;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (check(piles, mid, h)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }     
        return left;
    }
    public boolean check(int[] piles, int speed, int h) {
        int cost = 0;
        for (int i = 0; i < piles.length; i++) {
           int quotient = piles[i] % speed;
           cost = cost + (piles[i] / speed);
           cost = quotient >= 1 ? cost + 1 : cost; 
        }
        return cost <= h;
    }
}
```
