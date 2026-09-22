---
tags:
  - slidingWindow
Difficulty Level: Hard
Rating: 
Need Review: false
Origin: LC 239
First: April 23, 2025 6:58 PM
Watch Solution: false
---

# 239. Sliding Window Maximum

[Link](https://leetcode.com/problems/sliding-window-maximum/)

**Topics**: Sliding Window

## Notes

Sliding windows: 入→ 出→ 紀錄答案

```C++
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        deque <int> dq;
        vector <int> ans;
        for (int i = 0; i < nums.size(); i++){
            while (!dq.empty() and nums[i] >= nums[dq.back()]){
                dq.pop_back();
            }
            dq.push_back(i);
            if (i - dq.front() >= k) {
                dq.pop_front();
            }
            if (i >= k - 1){
                ans.push_back(nums[dq.front()]);
            }
        }
        return ans;
    }
};
```