## Problem Statement
[B - Intercepted Inputs](https://codeforces.com/problemset/problem/2037/B)

## Solution
The whole string contains 2 numbers for order and `n - 2` for the elements in the matrix. Lets denote order as `M x N`. Then `M x N = n - 2` also `M` and `N` should belong to the sequence of elements given. Also check if `M` and `N` belong to the sequence taking into account the the edge case of `n - 2` being a perfect square.
<br>

## Code
```cpp
#include <bits/stdc++.h>
#define FAST_IO ios_base::sync_with_stdio(0), cin.tie(nullptr);
using namespace std;

void solve() {
    int i, n;
    cin >> n;
    vector<int> arr(n);
    map<int, int> occured;
    for(i = 0; i < n; i++) {
        cin >> arr[i];
        occured[arr[i]]++;
    }

    for(i = 0; i < n; i++) {
        if((n - 2) % arr[i] == 0 && occured[(n - 2) / arr[i]] - ((n - 2) / arr[i] == arr[i])) {
            cout << arr[i] << " " << (n - 2) / arr[i] << "\n";
            break;
        }
    }
}

int main()
{
    FAST_IO
    int t;
    cin >> t;
    while (t--)
    {
        solve();
    }
    return 0;
}
```

## Analysis
Time Complexity: For each test case <i>O(nlog(n))</i>
<br>
Space Complexity: <i>O(n)</i>
