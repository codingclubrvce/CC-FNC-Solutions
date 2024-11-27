## Problem Statement
[E - Two Cards](https://www.codechef.com/problems/TWOCARD)

## Solution
The only two cards of importance are the ones with the maximum and second maximum A values. Sort the cards in non-increasing order of A's values. If alice chooses the card with max A, Bob chooses the card with second max A. In that case compare the max value on either sides of the two cards. Else if Alice has choosen another card, Bob chooses card with max A, compare max value on either side of each car with max value of Bob choosen card.
<br>

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n;
    cin >> n;
    vector<pair<int, int>> arr(n);
    
    for(i = 0; i < n; i++)  cin >> arr[i].first;
    for(i = 0; i < n; i++)  cin >> arr[i].second;
    sort(arr.rbegin(), arr.rend());
    if(max(arr[0].first, arr[0].second) > max(arr[1].first, arr[1].second)) {
        cout << "Yes\n";
        return;
    }
    else {
        for(i = 1; i < n; i++) {
            if(max(arr[0].first, arr[0].second) < max(arr[i].first, arr[i].second)) {
                cout << "Yes\n";
                return;
            }
        }
    }
    cout << "No\n";
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
