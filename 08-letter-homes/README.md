# Letter homes

[problem link](https://codeforces.com/contest/2121/problem/A)

# Code
```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
    int t;
    cin>>t;
    while(t--){
        int n,s;
        cin>>n>>s;
        int x[n];
        for(int i=0;i<n;i++){
            cin>>x[i];
        }
        if(s>=x[n-1])cout<<s-x[0]<<endl;
        else if(s<=x[0])cout<<x[n-1]-s<<endl;
        else{
        int d1 = x[n-1]-s;
        int d2 = s-x[0];
        int mindist = min(d1,d2);
        int maxdist = max(d1,d2);
        int res = 2*mindist+maxdist;
        cout<<res<<endl;
        }
    }
}
```