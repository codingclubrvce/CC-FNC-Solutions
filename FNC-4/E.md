## Problem Statement
[E - One To Three](https://www.codechef.com/problems/ONETOTHREE)

## Solution
The only possible operation which reduces the sum if if we have a subarray of 2, 3, 2 or 1, 3, 3 or 3, 3, 1. This can be performed till we have such a subarray existing. One way to tackle is to iterate throught front and keep changing the middle 3 to 1. Then iterate from end to use the newly updated 1s to get more such subarrays.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, k, n, sum;
    cin >> n;
    vector<int> arr(n);
    for(i = 0; i < n; i++)  
        cin >> arr[i];
    sum = accumulate(arr.begin(), arr.end(), 0);
        
    for(i = 1; i < n - 1; i++) {
        if(arr[i] == 3 && arr[i - 1] + arr[i + 1] == 4) {
            sum -= 2;
            arr[i] = 1;
        
        }
    }
    for(i = n - 2; i >= 0; i--) {
        if(arr[i] == 3 && arr[i - 1] + arr[i + 1] == 4) {
            sum -= 2;
            arr[i] = 1;
        }
    }    
    cout << sum << "\n";
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
Time Complexity: For each test case <i>O(n)</i> 
<br>
Space Complexity: <i>O(n)</i>
