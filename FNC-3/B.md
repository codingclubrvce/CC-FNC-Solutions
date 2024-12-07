## Problem Statement
[B-Mahmoud and a Triangle](https://codeforces.com/problemset/problem/766/B)

## Solution
Check if there is any triplet of numbers where the greatest number is lesser than the sum of the 2 smallest numbers. If yes, we have a degenerate triangle else no.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n;
    cin >> n;
    vector<int> arr(n);
    for(i = 0 ; i < n; i++) {
        cin >> arr[i];
    }
    sort(arr.begin(), arr.end());
    for(i = 0; i < n - 2; i++) {
        if(arr[i] + arr[i + 1] > arr[i + 2])
            break;
    }
    cout << ((i == n - 2)? "NO" : "YES") << "\n";
}

int main()
{
    int t;
    t = 1;
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
