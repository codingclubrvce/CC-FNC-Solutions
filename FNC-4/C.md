## Problem Statement
[C - Equal Pairs (Easy)](https://www.codechef.com/problems/MAXEQEASY?tab=statement)

## Solution
The zeros should be converted to the element with maximum frequency this is because `n * (n - 1) / 2` is the number of pairs such that i < j ans a<sub>i</sub> == a<sub>j</sub>. Now for n, n + 1 will be larger for larger n. Implementation wise create a frequency table and pair zero frequecy with the largest frequency and do not alter others. U can even skip iterating through 0 and just add its frequency (code follows this).

## Code
```cpp
#include <bits/stdc++.h>
using namespace std;

void solve() {
    int i, n, max_freq, count, zeros;
    cin >> n;
    vector<int> arr(n);
    map<int, int> freq;
    zeros = 0;
    max_freq = count = 0;
    
    for(i = 0; i < n; i++)  cin >> arr[i];
    for(i = 0; i < n; i++) {
        if(arr[i] == 0)
            zeros++;
        else
            freq[arr[i]]++;
    }
    
    for(auto it = freq.begin(); it != freq.end(); it++) {
        if(it -> second > max_freq) {
            count += (max_freq - 1) * max_freq / 2;
            max_freq = it -> second;
        }
        else 
            count += ((it -> second - 1) * it -> second) / 2;
        // cout << it -> first << " " << it -> second << "\n";
    }
    cout << ((max_freq - 1 + zeros) * (max_freq + zeros) / 2) + count << "\n";
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
