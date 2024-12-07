## Problem Statement
[E-Break Free](https://www.codechef.com/problems/REMOSET)

## Solution
Instead of finding the number of good removals, lets find the number of good arrays, it is the set of all even numbers, the total possible number of subsets of the even numbers of `arr` will give us the number of sets of even numbers. Edge case is when all numbers are even, in that case we cannot have choose all the even numbers to be a part of the array after removal as the array to be removed should be non-empty. Hence subtract 1 if `even_count == n`.

## Code

```cpp
#include <bits/stdc++.h>
#define MOD (int)(1e9 + 7)
using namespace std;

long long binpow(long long a, long long b) {
    long long result;
    result = 1;
    while(b) {
        if(b & 1) 
            result = (result * a) % MOD;
        a = (a * a) % MOD;
        b >>= 1;
    }
    return result;
}

void solve() {
    int i, n, even_count;
    cin >> n;
    vector<int> arr(n);
    even_count = 0;
    for(i = 0; i < n; i++) {
        cin >> arr[i];
        if(!(arr[i] & 1))
            even_count++;
    }
    cout << binpow(2, even_count) - (even_count == n) << "\n";
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
Time Complexity: For each test case <i>O(n + log(n))</i>
<br>
Space Complexity: <i>O(n)</i>
