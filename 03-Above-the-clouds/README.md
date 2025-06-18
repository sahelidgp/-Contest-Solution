# Above The  Clouds
[Problem link](https://codeforces.com/contest/2121/problem/B)

# Code
```c++
#include<bits/stdc++.h>
using namespace std;
#include<unordered_map>
int main(){
    int t;
    cin>>t;
    while (t--)
    {
        int n;
        cin>>n;
        string s;
        cin>>s;
        char a = s[0];
        char b = s[n-1];
        unordered_map<char,int>mp;
        for(int i=1;i<n-1;i++){
            mp[s[i]]++;
        }
        
        bool ispos = false;
        for(auto &[key,val]: mp){
            if(val >=2 || key == a || key == b){ispos = true;break;}
        }
        if(ispos)cout<<"Yes"<<endl;
        else cout<<"No"<<endl;
    } 
    
}

```