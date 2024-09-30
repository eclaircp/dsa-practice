# Frodo and Pillows
`Div.2 B` `1500`

[Problem Link](https://codeforces.com/problemset/problem/760/B)

## Solution



## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

#define int long long

/* --------------------------------------------------------------------------------------------------------------------------------- */
/* --------------------------------------------------------------------------------------------------------------------------------- */

int n, m, k;

bool f(int x) {
	
	int leftPillows = m-x;
	
	// left
	// case 1 (x-1 > k-1) : (x-1) + (x-2) + ... + (x - (k-1)) = (k-1)((x-1) + (x - (k-1)))/2 = (k-1)(2x-k)/2
	// case 2 (x-1 <= k-1) : (x-1) + (x-2) + ... + 1 + ... + 1 = x(x-1)/2 + (k-1 - (x-1)) = x(x-1)/2 + (k-x)
	
	int left;
	
	if(x-1 > k-1) {
		left = (k-1)*(2*x-k)/2;
	} else {
		left = x*(x-1)/2 + (k-x);
	}
	
	// right
	// case 1 (x-1 > n-k) : (x-1) + (x-2) + ... + (x - (n-k)) = (n-k)(x-1 + x-n+k)/2 = (n-k)(2x-n+k-1)/2
	// case 2 (x-1 <= n-k) : (x-1) + (x-2) + ... + 1 + ... + 1 = x(x-1)/2 + (n-k-(x-1)) = x(x-1)/2 + (n-k-x+1)
	
	int right;
	
	if(x-1 > n-k) {
		right = (n-k)*(2*x-n+k-1)/2;
	} else {
		right = x*(x-1)/2 + (n-k-x+1);
	}
	
	return leftPillows >= (left+right);
	
}

void solve() {
 
	cin >> n >> m >> k;
	
	int l = 1, h = m;
	
	while(l <= h) {
		int x = l + (h-l)/2;
		
		if(f(x)) {
			// check for higher values
			l = ++x;
		} else {
			// check for lower values
			h = --x;
		}
	}
	
	cout << h;
	
}

 
int32_t main() {
    
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
    
    int t = 1;
    // cin >> t;
    
    while(t--) solve();
    
    return 0;

}
```
