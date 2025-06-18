# Add to get GCD

[Problem link](https://www.codechef.com/problems/ADDGCD)

# Code

```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(NULL);

    int t;
    cin >> t;
    while (t--) {
        int x, y;
        cin >> x >> y;

        if (gcd(x, y) > 1)
            cout << 0 << '\n';
        else if (gcd(x + 1, y) > 1 || gcd(x, y + 1) > 1)
            cout << 1 << '\n';
        else
            cout << 2 << '\n';
    }
    return 0;
}

```