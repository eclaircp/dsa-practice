# Array Division
`CSES` `Searching and Sorting`

[Problem Link](https://cses.fi/problemset/task/1085)

## Code

```cpp
#include <bits/stdc++.h>
using namespace std;

#define int long long
#define vi vector<int>

/* --------------------------------------------------------------------------------------------------------------------------------- */
/* --------------------------------------------------------------------------------------------------------------------------------- */

int n, k;
vi a;

bool f(int x) {
	
	int sum = 0; // sum of a subarray
	int count = 0; // number of subarrays formed
	
	for(int i=0; i<n; i++) {
		if(a[i] > x) {
			return false;
		}
		
		if(sum + a[i] > x) {
			count++;
			sum = 0;
		}
		
		sum += a[i];
	}
	
	if(sum > 0) {
		count++;
	}
	
	if(count <= k){
		return true;
	}
	
	return false;
	
}

void solve() {
 
	cin >> n >> k;
	
	a.resize(n);
	
	int SUM = 0;
	
	for(auto &i : a) {
		cin >> i;
		SUM += i;
	}
	
	int l = 1, h = SUM;
	
	while(l <= h) {
		int x = l + (h-l)/2;
		
		if(f(x)) {
			h = --x;
		} else {
			l = ++x;
		}
	}
	
	cout << l;
	
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
