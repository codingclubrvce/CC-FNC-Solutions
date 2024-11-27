## Problem Statement
[D - Erase First or Second Letter](https://codeforces.com/problemset/problem/1917/B)

## Solution
Start by finding the pattern if we perform the second operation after performing the first operation only once. Take the sample `ababa`:
+ ababa -> aaba -> aba -> aa -> a
+ baba -> bba -> ba -> b
+ aba -> aa -> a
+ ba -> b
+ a

Notice that if we perform the second operations on two strings with same first element, the larger string will cover all the strings covered by the smaller. Hence only the strings formed by unique char are counted = the length of the sub-sequence.
<br>

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n;
    string s;
    cin >> n >> s;
    set<char> occured;
    long long count = 0;
    for(i = 0; i < n; i++) {
        if(!occured.count(s[i]))
            count += n - i;
        occured.insert(s[i]);
    }
    cout << count << "\n";
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
