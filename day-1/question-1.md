# Sqrt(x)
`Leetcode Easy`

[Problem Link](https://leetcode.com/problems/sqrtx/)

## Code

```cpp
class Solution {

    bool f(long long x, int n) {
        return x*x <= n;
    }

public:
    int mySqrt(int n) {
        long long l = 0, h = n;

        while(l <= h) {
            long long x = l+(h-l)/2;

            if(f(x, n)) {
                l = ++x;
            } else {
                h = --x;
            }
        }

        return h;
    }
};
```
