# Those who are with us

# [problem link](https://codeforces.com/contest/2121/problem/C)
# code

```c++
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
 
void solve(){
 
  ll n, m;
  cin >> n >> m;
  vector<vector<ll>> a(n, vector<ll>(m));
 
  ll mxElem = INT_MIN;
  for(ll i = 0 ; i <n; i++){
    for(ll j = 0; j < m; j++){
      cin >> a[i][j];
      mxElem = max(mxElem, a[i][j]);
    }
  }
 
  vector<ll> numOfMaxElemInRow(n, 0);
  vector<ll> numOfMaxElemInCol(m, 0);
  ll numOfMxElem = 0;
  
  for(ll i = 0 ; i <n; i++){
    for(ll j = 0; j < m; j++){
      ll curElem = a[i][j];
      if(curElem == mxElem){
 
        numOfMaxElemInCol[j]++;
        numOfMaxElemInRow[i]++;
        numOfMxElem++;
      }
    }
  }
  
  bool possible = false;
 
  for(ll i = 0 ; i <n; i++){
    for(ll j = 0; j < m; j++){
      ll curElem = a[i][j];
 
      if(curElem == mxElem){
        if(numOfMaxElemInCol[j] + numOfMaxElemInRow[i] - 1 == numOfMxElem){
          possible = true;
          break;
        } else{
          continue;
        }
      } else {
        if(numOfMaxElemInCol[j] + numOfMaxElemInRow[i]  == numOfMxElem){
          possible = true;
          break;
        } else{
          continue;
        }
      }
 
    }
  }
 
 
  if(possible){
    cout << mxElem-1 << endl;
  } else{
    cout << mxElem << endl;
  }
 
} 
 
 
int main()
{
 
 
  int t = 1;
  cin >> t;
  while (t--)
  {
    solve();
  }
 
  return 0;
}
```