## Problem Statement
[A-Alice's Adventures in "Chess"](https://codeforces.com/problemset/problem/2028/A)

## Solution
Since the constraints are `n , a, b <= 10`, The maximum number of iterations that need to be done until it is sure that Alice does not reach the queen is 21. Consider the case where queen is at (x, y). If alice cannot reach her in 1 iteration, she can further repeat the pattern only when she is within the boundary of y = 10, y = -10, x = 10, x = -10. But after she leaves, it is yet possible for her to come inside the boundary and meet queen. However, if atleast one of the coordinates reaches `21`, it is not possible as the length of `n` is 10 only.
<br>

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve()
 {
    
    int i, j;
    int n, a, b, x, y;
    string s;
    
    cin >> n >> a >> b >> s;
    x = y = 0;
    for(i = 0; i < 20 + 1; i++) {
        for(j = 0; j < n; j++) {
            y += (s[j] == 'N') - (s[j] == 'S');
            x += (s[j] == 'E') - (s[j] == 'W');
            if(x == a && y == b) {
                cout << "YES\n";
                return;
            }
        }
    }
    cout << "NO\n";
 }

int main()
{
    int t;
    cin >> t;
    while(t--) {
        solve();
    }
}
```

## Analysis
Time Complexity: For each test case <i>O(n)</i>
<br>
Space Complexity: <i>O(1)</i>
