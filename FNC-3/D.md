## Problem Statement
[D - LuoTianyi and the Table](https://codeforces.com/problemset/problem/1825/B)

## Solution
We want to maximize the number of subsquares where the maximum and minimum number appear, this will be along the largest side i.e. `max(n, m)`, the other number we want to maximize will be the one with the largest difference i.e. either the largest and second smallest or the second largest and smallest. Computing both and taking maximum shiuld give us the result.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n, m;
    long long max_1, max_2;
    cin >> n >> m;
    vector<int> b(n * m);
    
    for(i = 0; i < n * m; i++) {
        cin >> b[i];
    }
    sort(b.begin(), b.end());
    if(n < m)   swap(n, m);
    max_1 = (b[n * m - 1] - b[0]) * (m * (n - 1)) + (b[n * m - 1] - b[1]) * (m - 1);
    max_2 = (b[n * m - 1] - b[0]) * (m * (n - 1)) + (b[n * m - 2] - b[0]) * (m - 1);
    cout << max(max_1, max_2) << "\n";
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
Time Complexity: For each test case <i>O(nmlog(nm))</i>
<br>
Space Complexity: <i>O(nm)</i>
