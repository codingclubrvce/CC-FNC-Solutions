## Problem Statement
[C-Minimum Types](https://www.codechef.com/problems/MINBUY)

## Solution
Greedly select the coin whose total amount is maximum i.e. a<sub>i</sub> * b<sub>i</sub> is maximum.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

bool comp(pair<int, int>& a, pair<int, int>& b) {
    return a.first * a.second > b.first * b.second;
}

void solve() {
    
    int i, n, x;
    cin >> n >> x;
    vector<pair<int, int>> pocket(n);
    
    for(i = 0; i < n; i++) {
        cin >> pocket[i].first;
    }
    for(i = 0; i < n; i++) {
        cin >> pocket[i].second;
    }
    
    sort(pocket.begin(), pocket.end(), comp);
    
    for(i = 0; i < n; i++) {
        if(x <= pocket[i].first * pocket[i].second) {
            cout << i + 1 << "\n";
            return;
        }
        x -= pocket[i].first * pocket[i].second;
    }
    cout << -1 << "\n";
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
