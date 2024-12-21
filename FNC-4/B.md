## Problem Statement
[B - Best Permutation](https://codeforces.com/problemset/problem/1728/B)

## Solution
The maximum value that can be achielve for `n >= 4` is `2 * n - 1` this is because the next element should be grater than the current x. The only way possible is when n and n - 1 are the last two elements. Before this, the value of x should be zero. For odds, this can be done by switching positions of 2, 3 then 4, 5 so on in the std permutation. For evens switch positions of 1, 2 then 3, 4 so on.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;


void solve() {
    int i, n;
    cin >> n;
    
    if(n & 1) {
        cout << 1 << " ";
        for(i = 1; i < n - 2; i += 2) {
            cout << i + 2 << " " << i + 1 << " ";
        }
        cout << n - 1 << " " << n << "\n";
    }
    else {
        for(i = 0; i < n - 2; i += 2) {
            cout << i + 2 << " " << i + 1 << " ";
        } 
        cout << n - 1 << " " << n << "\n";
    }
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
Space Complexity: <i>O(1)</i>
