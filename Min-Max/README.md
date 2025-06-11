# [problem link](https://www.codechef.com/problems/MNMXDEL)

```c++
#include <iostream>
#include <vector>
using namespace std;

int main() {
   
    int tc;
    cin >> tc;

    while (tc--) {
        
        int n, q;
        cin >> n >> q;

        vector<int> arr(n);
        for (int i = 0; i < n; ++i) {
            cin >> arr[i];
        }

       
        long long score = 0;
        for (int i = 0; i < n - 1; ++i) {
            score += min(arr[i], arr[i + 1]);
        }

        while (q--) {
            int i, val;
            cin >> i >> val;
            --i; 

            if (i > 0) score -= min(arr[i - 1], arr[i]);
            if (i < n - 1) score -= min(arr[i], arr[i + 1]);

            arr[i] = val;

            if (i > 0) score += min(arr[i - 1], arr[i]);
            if (i < n - 1) score += min(arr[i], arr[i + 1]);

            cout << score << '\n';
        }
    }

    return 0;
}

```