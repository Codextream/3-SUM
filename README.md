# 3 SUM

Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

### Note:

The solution set must not contain duplicate triplets.

### Example:
<pre>
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
</pre>

### Solution:

```cpp


class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int n = nums.size();
        vector<vector<int>> ans;
        for(int i=0;i<n-2;i++){
               if(i>0 && (nums[i]==nums[i-1]) )continue;
               int l=i+1, r= n-1;
               while(l<r){
                   int sum =nums[i]+nums[l]+nums[r];
                   if(sum<0) l++;
                   else if(sum>0)r--;
                   else {
                       ans.push_back(vector<int>{nums[i],nums[l],nums[r]});
                       while(l+1<r && nums[l]==nums[l+1])l++;
                       while(l<r-1 && nums[r]==nums[r-1]) r--;
                       l++; r--;
                   }
               }
        }
        return ans;
    }
};

```
