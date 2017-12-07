.. _topics-3-longest-substring-without-repeating-characters:

==============================================
Longest Substring Without Repeating Characters
==============================================

Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.

**Example:** ::

    Given nums = [2, 7, 11, 15], target = 9,
    
    Because nums[0] + nums[1] = 2 + 7 = 9,
    return [0, 1].

**Solution**

方法1：暴力

遍历每个元素x并找出是否有另一个值等于target-x。 ::

    class Solution {
    public:
        vector<int> twoSum(vector<int>& nums, int target) {
            vector<int> result;
            for (int i = 0; i < nums.size() && !result.size(); i++) {
                for (int j = i + 1; j < nums.size(); j++) {
                    if (nums[j] == target - nums[i]) {
                        result = { i, j };
                        break;
                    }
                }
        }
            return result;
        }
    };

复杂度分析：

* 时间复杂度： :math:`\mathrm{O}(n^{2})`，对于每个元素x，
  我们试图通过循环其余的数组来找到他的(target-x)的复杂度为 :math:`\mathrm{O}(n)`，
  所以时间复杂度是 :math:`\mathrm{O}(n^{2})`。
* 空间复杂度： :math:`\mathrm{O}(1)`。









