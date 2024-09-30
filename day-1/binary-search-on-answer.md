# Binary Search on Answer

## When is it used?
Used when we have to find the minimum or maximum value of some parameter for which a given condition is satisfied. <br>
In mathematical terms, it's used in cases when we need to find the minimum or maximum value of variable _x_ for which the function _f(x)_ is satisfied. <br>
But, there is a condition, the _f(x)_ should be monotonic.

## What do you mean by the term monotonic?
It means a function is either increasing or decreasing. For performing binary search on answer, we can always convert _f(x)_ to a form where it only returns _true_ or _false_. And since this function is monotonic, the range of the function will be either of the following {..., false, false, true, true, ...} or {..., true, true, false, false, ...}.

## Code Structure
```cpp
#include <bits/stdc++.h>
using namespace std;

bool f(int x) {
    // conditons check
}

int main() {

    int l = someValue; // the smallest number in the range of x
    int h = someValue; // the largest number in the range of x

    while(l<=h) {
        int m = l + (h-l)/2;

        if(f(m) == true) {
            // do something
        } else {
            // do something
        }
    }

    // answer will either be l or h, depending upon the function f(x)

}
```
