# 【LeetCode】001.Two Sum

---

### Description：
Given an array of integers, return indices of the two numbers such that they add up to a specific target.
给定一个整数数组，返回两个数的索引，使它们相加为一个特定的目标。

You may assume that each input would have exactly one solution, and you may not use the same element twice.
可以假设每个输入都有一个解决方案，但是同一个元素不能使用两次。

Example:
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

暴力方法，时间复杂度O(n^{2}),可能会超时：
（直接在整个数组中进行查找是否包含）
```
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] res = new int[2];
        for (int i = 0; i < nums.length; i++) {
            for (int j = i+1; j < nums.length; j++) {
                if (target-nums[i]==nums[j]) {
                    res[0] = i;
                    res[1] = j;
                    break;
                }
            }
        }
        return res;
    }
}
```
用一个哈希表，存储每个数对应的下标，复杂度O(n);
（1、将数组中所有值存到一个HashMap中，对应的数组值为HashMap下标；
  2、查找HashMap下标中是否包含(目标值-nums[i])的数；）
```
public class Solution {
    public int[] twoSum(int[] numbers, int target) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            hashMap.put(nums[i], i);
        }
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (hashMap.containsKey(complement) && hashMap.get(complement) != i) {
                return new int[]{i, hashMap.get(complement)};
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
```




