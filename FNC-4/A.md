## Problem Statement
[A - Colored Balls: Revisited](https://codeforces.com/problemset/problem/1728/A)

## Solution
We can pair each ball of differnt colors, assume that we pair all balls except the max_count color balls, we will be left with either 0 or few balls of the different color, that can be paired with the max_count color. So finally the maximum count remains.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n, idx;
    cin >> n;
    vector<int> arr(n);
    for(i = 0 ; i < n; i++) {
        cin >> arr[i];
    }
    idx = 0;
    for(i = 1; i < n; i++) {
        if(arr[i] > arr[idx])
            idx = i;
    }
    cout << idx + 1 << "\n";
}

int main()
{
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
