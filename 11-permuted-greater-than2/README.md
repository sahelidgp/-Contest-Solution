# permuted-greater-than2

[Problem link](https://www.codechef.com/problems/PERMGE2)

```c++
#include <bits/stdc++.h>
using namespace std;

int main() {
	// your code goes here
	int T;
	cin>>T;
	while(T--)
	{
	    int X,Y,Z;
	    cin>>X;
	    cin>>Y;
	    cin>>Z;
	     int need = max(X - 1 + (Y > 0 ? 1 : 0), 0);
	     if(Z>=need) cout<<"yes"<<endl;
	     else cout<<"no"<<endl;
	}

}
```