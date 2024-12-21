## Problem Statement
[F - Magical Girl and Colored Liquid Potions](https://www.codechef.com/problems/PRPOTION)

## Solution
The only important value is the gratest amount in each portion color. Use this and keep redusing by a factor of 2 for `m` operations.

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void getMax(int r, int g, int b, long long* pr, long long* pg, long long* pb) {
    r /= *pr;
    g /= *pg;
    b /= *pb;
    if(r >= g && r >= b)
        *pr *= 2;
    else if(g >= r && g >= b) 
        *pg *= 2;
    else
        *pb *= 2;
}

void solve() {
    int i, nr, ng, nb, m;
    long long pr, pg, pb;
    cin >> nr >> ng >> nb >> m;
    vector<int> r(nr);
    vector<int> g(ng);
    vector<int> b(nb);
    for(i = 0; i < nr; i++)  cin >> r[i];
    for(i = 0; i < ng; i++)  cin >> g[i];
    for(i = 0; i < nb; i++)  cin >> b[i];
    sort(r.rbegin(), r.rend());
    sort(g.rbegin(), g.rend());
    sort(b.rbegin(), b.rend());
    pr = pg = pb = 1;
    while(m--) {
        getMax(r[0], g[0], b[0], &pr, &pg, &pb);
    }
    cout << max(r[0] / pr, max(g[0] / pg, b[0] / pb)) << "\n";
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
Time Complexity: For each test case <i>O(nrlog(nr) + nglog(ng) + nblog(nb) + m)</i>  
<br>
Space Complexity: <i>O(n)</i>
