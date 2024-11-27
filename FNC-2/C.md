## Problem Statement
[C - Meaning Mean](https://codeforces.com/problemset/problem/2021/A)

## Solution
Greedly selecting the smallest elements for the operation as they will have a smaller co-efficient in the final result hence minimizing contribution of the smaller numbers and maximizing contribution of the larger numbers.
<br>

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;


void solve() {
    int i, n;
    long long eval;
    vector<long long> arr;
    cin >> n;
    arr.resize(n);
    eval = 0;
    for(i = 0; i < n; i++)
        cin >> arr[i];
    sort(arr.begin(), arr.end());
    eval = (arr[0] + arr[1]) / 2;
    for(i = 2; i < n; i++) {
        eval = (eval + arr[i]) / 2;
    }
    cout << eval << "\n";
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
Time Complexity: For each test case <i>O(nlog(n))</i>
<br>
Space Complexity: <i>O(n)</i>
