
Problem Statement: Given an array return the total number of pairs such that i < j and nums[i] > 2*nums[j]

Difficulty: Hard

Topics: Merge Sort

Constraints: - `1 <= nums.length <= 5 * 10^4`
- `-2^31 <= nums[i] <= 2^31 - 1`

Approach: Apply merge sort algorithm

Time Complexity:  O(n log n)

Space Complexity: O(1)

Pattern Learned: Merge Sort application

---

Code:

class Solution {
public:
    void merge(vector<int>& arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        vector<int> L(n1), R(n2);

        for (int i = 0; i < n1; i++)
            L[i] = arr[left + i];
        for (int j = 0; j < n2; j++)
            R[j] = arr[mid + 1 + j];

        int i = 0, j = 0;
        int k = left;

        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    void check(vector<int>& arr, int l, int r, int m, int& count){
        int left = l;
        int right = m + 1;
        while (left <= m && right <= r) {
            if ((long long)arr[left] > 2LL * (long long)arr[right]) {
                count += (m - left + 1);
                right++;
            } else {
                left++;
            }
        }
    }

    void mergeSort(vector<int>& arr, int left, int right, int& count) {
        if (left >= right)
            return;

        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid, count);
        mergeSort(arr, mid + 1, right, count);
        check(arr, left, right, mid, count);
        merge(arr, left, mid, right);
    }

    int reversePairs(vector<int>& nums) {
        int n = nums.size();
        int cnt = 0;
        mergeSort(nums, 0, n - 1, cnt);
        return cnt;
    }
};