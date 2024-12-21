## Problem Statement
[D - Digital Logarithm](https://codeforces.com/contest/1728/problem/C)

## Solution
There is no need to perform operation if an element is present in both A and B. If it is present in only one, it has to be decreased to an element present in B or one element each from A and B should be reduced to 1 (the min possible).

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

int digitCount(int n) {
    int count = 0;
    while(n) {
        count++;
        n /= 10;
    }
    return count;
}

void solve() {
    int i, n, ele, count;
    cin >> n;
    priority_queue<int> a;
    priority_queue<int> b;
    count = 0;
    for(i = 0; i < n; i++) {
        cin >> ele;
        a.push(ele);
    }
    for(i = 0; i < n; i++) {
        cin >> ele;
        b.push(ele);
    }
    
    while(!a.empty()) {
        if(a.top() == b.top()) {
            a.pop();
            b.pop();
            continue;
        }
        else if(a.top() > b.top()) {
            a.push(digitCount(a.top()));
            a.pop();
        }
        else {
            b.push(digitCount(b.top()));
            b.pop();
        }
        count++;
    }
    cout << count << "\n";
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
Time Complexity: For each test case ~ <i>O(nlog(n))</i> 
<br>
Space Complexity: <i>O(n)</i>
