---
title: LeetCode 第一題：使用 C++
---

# LeetCode 第一題：使用 C++
> [題目連結](https://leetcode.com/problems/two-sum)

## 第一次嘗試
第一次解題的思路是使用相當直觀的方式，假設 input 為 [1, 2, 3]，那麼我可以用這樣的方式：
1. 第 1 個 + 第 2 個
2. 第 1 個 + 第 3 個
3. 第 2 個 + 第 3 個

> 結果
> - Runtime: 328ms
> - Memory: 10MB

不過這樣的時間複雜度是 $O(n^2)$，所以還需要再改進一些

```cpp
class Solution {
    public:
        vector<int> twoSum(vector<int>& nums, int target) {
            for (int index_1 = 0; index_1 < nums.size(); index_1++) {
                for (int index_2 = index_1 + 1; index_2 < nums.size(); index_2++) {
                    if (nums[index_1] + nums[index_2] == target) {
                        return {index_1, index_2};
                    }
                }
            }

            return {};
        }
};
```

> 如果你不知道 C++ 的 Vector 是什麼，可以參考以下這篇：
> - [C/C++ - Vector (STL) 用法與心得完全攻略 ](https://mropengate.blogspot.com/2015/07/cc-vector-stl.html)

---

## 第二次嘗試
而我試著將 `nums.size()` 改存放至一變數中，就減少了 60ms

> 結果
> - Runtime: 268ms
> - Memory: 10.1MB

```cpp
class Solution {
    public:
        vector<int> twoSum(vector<int>& nums, int target) {
            int input_size = nums.size();
            
			for (int index_1 = 0; index_1 < input_size; index_1++) {
                for (int index_2 = index_1 + 1; index_2 < input_size; index_2++) {
                    if (nums[index_1] + nums[index_2] == target) {
                        return {index_1, index_2};
                    }
                }
            }

            return {};
        }
};
```



## 第三次嘗試：使用古人的 $O(n)$ 演算法
> 參考自 [C++ Solution using Hashmap  time complexity-O(n)  and space complexity-O(n)](https://leetcode.com/problems/two-sum/discuss/1278342/C%2B%2B-Solution-using-Hashmap-time-complexity-O(n)-and-space-complexity-O(n))

由於這一題並不需要有順序性的來排列元素，所以這位作者使用了 unordered_map（而不是使用 map）來實現 $O(n)$

> 如果你不知道 C++ 的 `map`、`unordered_map` 是什麼，建議先閱讀以下兩篇資料
> - [C/C++ - Map (STL) 用法與心得完全攻略 ](https://mropengate.blogspot.com/2015/12/cc-map-stl.html)
> - [C++ STL 之哈希表 | unordered_map ]([https://xzchsia.github.io/2020/04/09/cpp-map-unordered_map/](https://www.sczyh30.com/posts/C-C/cpp-stl-hashmap/)) 

解題思路：
1. 透過 `unordered_map` 的快速查詢特性，來有效降低 Runtime
2. 將 input vector 放入 `unordered_map` 中
3. 利用 `target - input_1 = input_2` 原理，將 target 與 input 的數值相減，如果相減的數值包含在 `unordered_map` 中，那麼...
	- 為避免計算重複的 index，因此，相減後的數值（`input_2`）不能等於 `input_1` 的 index
4. return `unordered_map[input_1]` 和 `unordered_map[input_2]`

> 結果：
> - Runtime: 12ms
> - memory: 11.9 MB

```cpp
class Solution {
    public:
        vector<int> twoSum(vector<int>& nums, int target) {
            unordered_map<int, int> searchMap;
            int inputSize = nums.size();
            
            for (int index = 0; index < inputSize; index++) {
               searchMap[nums[index]] = index;
            }
            
            for (int index = 0; index < inputSize; index++) {
                if (searchMap.find(target - nums[index]) != searchMap.end()) {
                    if (index != searchMap[target - nums[index]]) {
                        return {index, searchMap[target- nums[index]]};
                    }
                }
            }
            
            return {};
        }
};
```