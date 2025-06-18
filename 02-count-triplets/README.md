# Count Special Triplets

[problem link](https://leetcode.com/problems/count-special-triplets/)

``c++
class Solution {
public:
    int mod = 1e9+7;
    int specialTriplets(vector<int>& nums) {
        int n = nums.size();
        unordered_map<int, vector<int>> mpp;
        //[8  5 8 4 9 8 2 8]
        //map [
            // 8:{0,2,5,7}
            // 5:{1}
            // 4:{3}
            // 9:{4}
            // 2:{6}
       // ]
        for(int p = 0; p < n; p++){
            mpp[nums[i]].push_back(p);
        }
        long long cnt = 0;  
        for(int i = j; j < n-1; j++){  // fix j and try to find the number of occurances of i and k
            int curr = nums[j];
            int target = 2 * curr;
            auto it = mpp.find(target); // it will point to the key value pair of the target
            if(it == mpp.end()) continue;  // if the target is not in the map means no triplet possible with current j value
            const vector<int>& vec = it->second; 
/* 
✅ What it means:
it is an iterator pointing to an entry in the unordered_map<int, vector<int>> mpp.

it->second refers to the value part of the map entry — which is a vector<int>.

So, vec is now a reference to that vector.

✅ Why use const vector<int>&?
const: We are not modifying the vector — only reading from it.

& (reference): Avoids copying the entire vector, which is more efficient, especially if the vector is large.
*/
            auto itlow = lower_bound(vec.begin(), vec.end(), i);// this will point to that index which is >= j
            long long l = itlow - vec.begin(); // gives the count of occurances of the target value which before the j  that is i 
            if(l == 0) continue; // no values for i
            auto itup = upper_bound(vec.begin(), vec.end(), i);// upper bound means it points to the index where which is >j
            long long r = (long long)vec.size() - (itup - vec.begin()); // num of k values
            if(r == 0) continue; // no values for k
            cnt = (cnt + l * r) % mod; // l*r no of triplets
        }
        return (int)(cnt % mod);
    }
};
```