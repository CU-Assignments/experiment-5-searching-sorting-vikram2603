[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/RMIP9yyr)
# 22BCS_IOT-634-A-Exp-5_AP

1. Merge Sorted Array	--	https://leetcode.com/problems/merge-sorted-array/
2. First Bad Version	--	https://leetcode.com/problems/first-bad-version/
3. Sort Colors	--	https://leetcode.com/problems/sort-colors/
4. Top K frequent elements	--	https://leetcode.com/problems/top-k-frequent-elements/
5. Kth Largest element in an array	--	https://leetcode.com/problems/kth-largest-element-in-an-array/
6. Find Peak Element	--	https://leetcode.com/problems/find-peak-element/
7. Search For a range	--	https://leetcode.com/problems/search-for-a-range/
8. Merge Intervals	--	https://leetcode.com/problems/merge-intervals/
9. Search in Rotated Sorted Array	--	https://leetcode.com/problems/search-in-rotated-sorted-array/
10. Search a 2D Matrix II	--	https://leetcode.com/problems/search-a-2d-matrix-ii/
11. Wiggle Sort 2	--	https://leetcode.com/problems/wiggle-sort-2/
12. Kth smallest element in a sorted matrix	--	https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/
13. Median of Two Sorted Arrays	--	https://leetcode.com/problems/median-of-two-sorted-arrays/





Quesrtion -1   (Merge Sorted Array)
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1;  // Pointer for nums1's last valid element
        int j = n - 1;  // Pointer for nums2's last element
        int k = m + n - 1;  // Pointer for the last position in nums1

        // Merge from the back to avoid overwriting elements in nums1
        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }

        // If elements in nums2 are left, copy them
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
};


Question 2 (First Bad Version)
// Forward declaration of isBadVersion API.
bool isBadVersion(int version);

class Solution {
public:
    int firstBadVersion(int n) {
        int left = 1, right = n;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (isBadVersion(mid)) {
                right = mid; // The first bad version is at mid or before mid.
            } else {
                left = mid + 1; // The first bad version is after mid.
            }
        }
        return left; // left should point to the first bad version.
    }
};

Question - 3 (Sort Colors)

class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low = 0, mid = 0, high = nums.size() - 1;
        
        while (mid <= high) {
            if (nums[mid] == 0) {
                swap(nums[low++], nums[mid++]);
            } else if (nums[mid] == 1) {
                mid++;
            } else {
                swap(nums[mid], nums[high--]);
            }
        }
    }
};


Question 4 (Top K frequent elements)
#include <vector>
#include <unordered_map>
#include <queue>

using namespace std;

class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        unordered_map<int, int> freqMap;  // Store frequency of each element
        for (int num : nums) {
            freqMap[num]++;
        }

        // Min-heap to store k most frequent elements
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> minHeap;

        for (auto& [num, freq] : freqMap) {
            minHeap.push({freq, num});
            if (minHeap.size() > k) {
                minHeap.pop();  // Remove least frequent element
            }
        }

        vector<int> result;
        while (!minHeap.empty()) {
            result.push_back(minHeap.top().second);
            minHeap.pop();
        }

        return result;
    }
};class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int m = matrix.size();
        if (m == 0) return false;
        int n = matrix[0].size();

        // Start from the top-right corner
        int row = 0, col = n - 1;

        while (row < m && col >= 0) {
            if (matrix[row][col] == target) {
                return true;  // Target found
            } else if (matrix[row][col] > target) {
                col--;  // Move left
            } else {
                row++;  // Move down
            }
        }

        return false;  // Target not found
    }
};



Question 5 (Search a 2D Matrix II)

