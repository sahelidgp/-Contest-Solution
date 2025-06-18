# [Problem link](https://www.codechef.com/problems/LTALL)


# 🔍 Problem Recap
You are given a binary string S where:

'1' = working light (can face left or right),

'0' = no light.

You need to decide if it's possible to choose directions for all the working lights such that every cell gets lit by at least one working light.

A working light at index i can:

Light cell i and i+1 if it faces right

Light cell i and i-1 if it faces left

✅ Your Code Summary

for (int i = 0; i < S.length();) {
    if (S[i] == '0') {
        if (i != 0 && S[i - 1] == '1') {
            i++;
        }
        else if (i != N - 1 && S[i + 1] == '1') {
            S[i + 1] = '0';
            i += 2;
        }
        else {
            t = false;
            break;
        }
    } else {
        i++;
    }
}
This loop processes each character of the string S, and for every '0', it checks:

🧠 Logic in Detail
Case 1: S[i] == '0'
We need this cell to be lit. So we check neighbors.

🔸 Check Left (i > 0)

if (i != 0 && S[i - 1] == '1')
If the left light is working, it can face right to light i. We move to next character (i++).

🔸 Check Right (i < N-1)

else if (i != N - 1 && S[i + 1] == '1')
If the right light is working, it can face left to light i.

Then you mark S[i + 1] = '0' so that this right light is not reused again to light anything else.

Then move to i + 2 (skip both cells).

❌ If neither neighbor is working

else {
    t = false;
    break;
}
Then it’s impossible to light cell i, so you fail.

Case 2: S[i] == '1'
cpp
Copy
Edit
else {
    i++;
}
If current light is working ('1'), move on — this cell will be lit by itself or will be considered while processing adjacent cells.

📌 Example Walkthrough
Input:
ini
Copy
Edit
N = 5  
S = "10011"
i = 0: '1' → skip

i = 1: '0' → left = '1' → OK → i++

i = 2: '0' → left = '0', right = '1' → mark right as '0', i += 2

i = 4: '1' → skip

All cells are processed successfully ⇒ Yes

🟩 Output
cpp
Copy
Edit
cout << (t ? "yes" : "no") << endl;
Outputs lowercase "yes" or "no" based on whether all 0s could be lit.

✅ Pros
Efficient, only O(n)

Marks '1' as used if already assigned

⚠️ Caution
Directly modifying S with S[i + 1] = '0' might not be best in some cases (could change logic if multiple 0s are close).

# code
```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
    int T;
    cin >> T;

    while (T--) {
        int N;
        string S;
        cin >> N >> S;

        bool t = true;

        for (int i = 0; i < S.length();) {
            if (S[i] == '0') {
                if (i != 0 && S[i - 1] == '1') {
                    i++;
                }
                else if (i != N - 1 && S[i + 1] == '1') {
                    S[i + 1] = '0';
                    i += 2;
                }
                else {
                    t = false;
                    break;
                }
            } else {
                i++;
            }
        }

        cout << (t ? "yes" : "no") << endl;
    }

    return 0;
}
```