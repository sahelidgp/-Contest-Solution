# 📖 Maximum Product of First and Last Elements of a Subsequence

# [problem link](https://leetcode.com/contest/weekly-contest-454/problems/maximum-product-of-first-and-last-elements-of-a-subsequence/)◀️

### Code
```c++
class Solution {
public:
    long long maximumProduct(vector<int>& nums, int m) {
        int n = nums.size();
        vector<long long> preMax(n), preMin(n);
        preMax[0] = nums[0];
        preMin[0] = nums[0];
        for(int i = 1;i<n;i++){
            preMax[i] = max(preMax[i-1], (long long)nums[i]);
            preMin[i] = min(preMin[i-1], (long long)nums[i]);
            
        }
        long long ans = LLONG_MIN;
        for(int j = m-1;j<n;j++){
            int lim = j-(m-1);
            long long t;
            if(nums[j] > 0)
             t = nums[j]*preMax[lim];
            else 
             t = nums[j]*preMin[lim];
            ans = max(ans, t);
        }
        return ans;
    }
};
```