## Problem Statement
[F-Watering an Array](https://codeforces.com/problemset/problem/1917/C)

## Solution
Performing the second type operation on a zero array gives a non-decreasing array, hence &exist; atmost one element such that a<sub>i</sub> = i. Hence the score after the reset is `days left / 2` . Now when to perform the reset operation. This is bounded by min(2 * n, d). Hece checking till min of 2 * n and d is fine.
<br>

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, j;
    int n, k, d;
    int score, max_score;
    cin >> n >> k >> d;
    vector<int> a(n);
    vector<int> v(k);
    for(i = 0; i < n; i++)
        cin >> a[i];
    for(i = 0; i < k; i++)
        cin >> v[i];
    max_score = 0;
    for(i = 0; i < min(2 * n, d); i++) {
        score = 0;
        for(j = 0; j < n; j++) {
            score += (a[j] == j + 1);
        }
        score += (d - i - 1) / 2;
        for(j = 0; j < v[i % k]; j++) {
            a[j]++;
        }
        max_score = max(max_score, score);
    }
    cout << max_score << "\n";
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
Time Complexity: For each test case <i>O(n + k + min(2d, n)</i>
<br>
Space Complexity: <i>O(n + k)</i>
