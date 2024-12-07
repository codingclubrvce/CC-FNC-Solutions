## Problem Statement
[F-TWINGFT](https://www.codechef.com/problems/TWINGFT?tab=submissions)

## Solution
Implementation sed, just calculate the sum of the alternate elements and make sure to add the last element to the twin who goes second. Return the maximum of the two twins as the answer.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n, k;
    long long twin_1, twin_2;
    cin >> n >> k;
    vector<long long> arr(n);
    for(i = 0; i < n; i++) {
        cin >> arr[i];
    }
    sort(arr.rbegin(), arr.rend());
    twin_1 = twin_2 = 0;
    for(i = 0; i < 2 * k + 1; i++) {
        if((i & 1) || i == 2 * k)
            twin_2 += arr[i];
        else 
            twin_1 += arr[i];
    }
    
    cout << max(twin_1, twin_2) << "\n";
}

int main() {
	int t;
	cin >> t;
	while(t--) {
	    solve();
	}
	return 0;
}
```

## Analysis
Time Complexity: For each test case <i>O(nlog(n))</i>
<br>
Space Complexity: <i>O(n)</i>
