## Problem Statement
[A-LuoTianyi and the Palindrome String](https://codeforces.com/problemset/problem/1825/A)

## Solution
Since `s` is a palindrome, s<sub>1</sub>s<sub>2</sub>s<sub>3</sub>....s<sub>n</sub>, we have s<sub><i>i</i></sub> = s<sub><i>n - 1 - i</i></sub> where 0 <= i <= n / 2. We now consider the case where removing a character yet maintains the string as palindrome. This is possible only when all the characters are equal. If there is one charater which does not match it's n - 1 - i<sup>th</sup> character, it is possible to get a string of length n - 1 which will not be a palindrome.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;


void solve() {
    int i, n;
    string s;
    cin >> s;
    s.pop_back();
    n = s.length();
    if(n <= 1) {
        cout << -1 << "\n";
        return;
    }
    for(i = 0; i < n / 2; i++) {
        if(s[i] != s[n - 1 - i]) {
            cout << n << "\n";
            return;
        }
    }
    cout << -1 << "\n";
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
Time Complexity: For each test case <i>O(n)</i> where n is length of string
<br>
Space Complexity: <i>O(n)</i>
