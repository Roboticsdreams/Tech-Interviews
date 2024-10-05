# DSA Patterns

[Tech-Interviews](../../../README.md) -> [References](../../References.md) -> [Online Tutorials](../../Online%20Tutorials/OnlineTutorials.md) -> [DSA Patterns](../DSA%20Patterns/DSAPatterns.md)

1. Graphs (DFS/BFS)

1.1. Number of Islands (Medium)

Given a 2D grid of 1s (land) and 0s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically.
Pattern: Apply DFS/BFS for graph traversal.

```java
public int numIslands(char[][] grid) {
    int count = 0;
    for (int i = 0; i < grid.length; i++) {
        for (int j = 0; j < grid[0].length; j++) {
            if (grid[i][j] == '1') {
                dfs(grid, i, j);
                count++;
            }
        }
    }
    return count;
}

private void dfs(char[][] grid, int i, int j) {
    if (i < 0 || i >= grid.length || j < 0 || j >= grid[0].length || grid[i][j] == '0') {
        return;
    }
    grid[i][j] = '0'; // Mark as visited
    dfs(grid, i + 1, j); // Down
    dfs(grid, i - 1, j); // Up
    dfs(grid, i, j + 1); // Right
    dfs(grid, i, j - 1); // Left
}
```

1.2. Course Schedule (Medium)
Given a list of course prerequisites, determine if you can finish all courses.
Pattern: Detect cycles in a directed graph using DFS.

1.3. Clone Graph (Medium)
Clone an undirected graph where each node points to its neighbors.
Pattern: Use DFS/BFS to traverse and clone each node.

1.4. Word Ladder (Medium)
Transform one word into another by changing a single character each time. Find the shortest transformation sequence.
Pattern: BFS for shortest path in word transformations.

1.5. Cycle in Directed Graph (Medium)
Given a directed graph, detect if there is a cycle.
Pattern: Use DFS with visited array and recursion stack.

2. Sliding Window
2.1. Maximum Sum Subarray of Size K (Easy)
Find the maximum sum of a subarray with size k.
Pattern: Sliding window with two pointers.

java
Copy code
public int maxSumSubArray(int[] nums, int k) {
    int maxSum = 0, windowSum = 0;
    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }
    maxSum = windowSum;
    for (int i = k; i < nums.length; i++) {
        windowSum += nums[i] - nums[i - k];
        maxSum = Math.max(maxSum, windowSum);
    }
    return maxSum;
}
2.2. Longest Substring Without Repeating Characters (Medium)
Find the length of the longest substring without repeating characters.
Pattern: Sliding window with a map to track characters.

2.3. Minimum Window Substring (Medium)
Find the smallest substring in s that contains all the characters of string t.
Pattern: Use two pointers and dynamic window size adjustment.

2.4. Longest Subarray of 1's after K Flips (Medium)
Given a binary array, flip at most k zeroes to get the longest subarray of 1s.
Pattern: Sliding window with count tracking.

2.5. Find All Anagrams in a String (Medium)
Given a string s and p, return all start indices of p's anagrams in s.
Pattern: Sliding window and frequency counting.

3. Linked Lists
3.1. Merge Two Sorted Lists (Easy)
Merge two sorted linked lists and return it as a single sorted list.
Pattern: Linked list manipulation with pointers.

java
Copy code
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    if (l1 == null) return l2;
    if (l2 == null) return l1;
    if (l1.val < l2.val) {
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    } else {
        l2.next = mergeTwoLists(l1, l2.next);
        return l2;
    }
}
3.2. Linked List Cycle (Easy)
Detect if a linked list has a cycle using the two-pointer (fast/slow) technique.
Pattern: Use two pointers to detect cycles.

3.3. Reverse Linked List (Easy)
Reverse a singly linked list in-place.
Pattern: Use pointers to reverse.

3.4. Find the Middle of a Linked List (Easy)
Return the middle node of a singly linked list.
Pattern: Use two pointers (slow/fast) to find the middle node.

3.5. Remove N-th Node from End of List (Medium)
Given a linked list, remove the n-th node from the end and return the head.
Pattern: Two pointer approach to find the nth node.

4. Dynamic Programming (Maximum/Minimum Subarrays)
4.1. Maximum Subarray (Easy)
Find the contiguous subarray with the largest sum.
Pattern: Use dynamic programming to track the current and maximum subarray sum.

java
Copy code
public int maxSubArray(int[] nums) {
    int maxSoFar = nums[0], maxEndingHere = nums[0];
    for (int i = 1; i < nums.length; i++) {
        maxEndingHere = Math.max(nums[i], maxEndingHere + nums[i]);
        maxSoFar = Math.max(maxSoFar, maxEndingHere);
    }
    return maxSoFar;
}
4.2. Longest Increasing Subsequence (Medium)
Find the length of the longest increasing subsequence.
Pattern: DP array to store lengths of increasing subsequences.

4.3. Coin Change (Medium)
Given an array of coins, find the fewest number of coins to make a given amount.
Pattern: DP to track the minimum number of coins for each amount.

4.4. House Robber (Medium)
You cannot rob two adjacent houses; maximize the amount robbed.
Pattern: DP with maximum sum.

4.5. Maximum Product Subarray (Medium)
Find the contiguous subarray within an array that has the largest product.
Pattern: Track both minimum and maximum product for each subarray.

5. Tree Problems
5.1. Maximum Depth of Binary Tree (Easy)
Find the maximum depth of a binary tree.
Pattern: DFS traversal to compute depth.

java
Copy code
public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
}
5.2. Symmetric Tree (Easy)
Check if a binary tree is symmetric around its center.
Pattern: DFS to check mirror symmetry.

5.3. Binary Tree Level Order Traversal (Medium)
Return the level order traversal of its nodes' values.
Pattern: BFS traversal.

5.4. Validate Binary Search Tree (Medium)
Determine if a binary tree is a valid binary search tree (BST).
Pattern: In-order traversal to verify BST properties.

5.5. Lowest Common Ancestor (Medium)
Find the lowest common ancestor of two given nodes in a binary tree.
Pattern: DFS to locate the LCA.

This set of problems is designed to cover common patterns in coding interviews and can help with mastering the techniques needed to solve LeetCode problems efficiently.






You said:
Continue 
ChatGPT said:
ChatGPT
Here’s a continuation with questions from the remaining categories.

6. In-Place Operations
6.1. Remove Duplicates from Sorted Array (Easy)
Given a sorted array, remove the duplicates in-place such that each element appears only once and return the new length.
Pattern: Use two pointers to overwrite duplicates.

java
Copy code
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) return 0;
    int i = 0;
    for (int j = 1; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    return i + 1;
}
6.2. Move Zeroes (Easy)
Move all zeroes to the end of an array while maintaining the relative order of the non-zero elements.
Pattern: Use two pointers for in-place swapping.

6.3. Rotate Array (Medium)
Rotate an array to the right by k steps.
Pattern: Reverse sections of the array in-place.

6.4. Reverse String (Easy)
Write a function that reverses a string. The input string is given as an array of characters, and you must do this by modifying the input array in-place.
Pattern: Swap characters at each end.

6.5. Next Permutation (Medium)
Find the next lexicographical permutation of the array of numbers. If it is the highest possible permutation, rearrange it into the lowest possible order (i.e., sorted in ascending order).
Pattern: Rearrange elements in-place using swapping.

7. Top/Least K Elements
7.1. Kth Largest Element in an Array (Medium)
Find the Kth largest element in an unsorted array.
Pattern: Use a min-heap or quickselect algorithm.

java
Copy code
public int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int num : nums) {
        minHeap.offer(num);
        if (minHeap.size() > k) {
            minHeap.poll();
        }
    }
    return minHeap.peek();
}
7.2. Top K Frequent Elements (Medium)
Given an integer array, return the k most frequent elements.
Pattern: Use a hashmap to count frequencies and a heap for sorting.

7.3. K Closest Points to Origin (Medium)
Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane, find the k closest points to the origin.
Pattern: Use a max-heap to track the closest points.

7.4. Find K-th Smallest Element in a Matrix (Medium)
Given an n x n matrix where each row and column is sorted, find the kth smallest element.
Pattern: Use a heap or binary search for efficient searching.

7.5. Kth Smallest Element in a Sorted Matrix (Medium)
Find the k-th smallest element in a sorted matrix.
Pattern: Use a min-heap to extract elements efficiently.

8. Permutations/Subsets
8.1. Subsets (Medium)
Given an integer array, generate all possible subsets (the power set).
Pattern: Use backtracking to generate all combinations.

java
Copy code
public List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> res = new ArrayList<>();
    backtrack(res, new ArrayList<>(), nums, 0);
    return res;
}

private void backtrack(List<List<Integer>> res, List<Integer> tempList, int[] nums, int start) {
    res.add(new ArrayList<>(tempList));
    for (int i = start; i < nums.length; i++) {
        tempList.add(nums[i]);
        backtrack(res, tempList, nums, i + 1);
        tempList.remove(tempList.size() - 1);
    }
}
8.2. Permutations (Medium)
Given an array of distinct integers, return all possible permutations.
Pattern: Use backtracking to generate permutations.

8.3. Combination Sum (Medium)
Given a set of candidate numbers and a target number, find all unique combinations where the candidate numbers sum to the target.
Pattern: Use backtracking and prune invalid paths early.

8.4. Generate Parentheses (Medium)
Generate all combinations of well-formed parentheses.
Pattern: Backtracking to explore valid combinations of parentheses.

8.5. Letter Combinations of a Phone Number (Medium)
Given a string containing digits from 2-9, return all possible letter combinations that the number could represent.
Pattern: Use backtracking to explore combinations of letters.

9. Common Strings Problems
9.1. Longest Common Prefix (Easy)
Write a function to find the longest common prefix string amongst an array of strings.
Pattern: Use a vertical scan to find the longest matching prefix.

java
Copy code
public String longestCommonPrefix(String[] strs) {
    if (strs.length == 0) return "";
    String prefix = strs[0];
    for (int i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(prefix) != 0) {
            prefix = prefix.substring(0, prefix.length() - 1);
            if (prefix.isEmpty()) return "";
        }
    }
    return prefix;
}
9.2. Valid Anagram (Easy)
Given two strings, determine if they are anagrams of each other.
Pattern: Use a map to count character frequencies.

9.3. Group Anagrams (Medium)
Group anagrams from a list of strings.
Pattern: Sort the characters of each string and use a map to group anagrams.

9.4. Longest Palindromic Substring (Medium)
Find the longest palindromic substring in a string.
Pattern: Use dynamic programming or expand around centers.

9.5. Implement Trie (Prefix Tree) (Medium)
Implement a Trie (Prefix Tree) with insert, search, and startsWith operations.
Pattern: Use a tree-like structure to store prefixes.

10. Recursion-Banned Problems
10.1. Binary Tree Inorder Traversal (Easy)
Implement the inorder traversal of a binary tree without recursion.
Pattern: Use a stack to simulate recursion.

java
Copy code
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> res = new ArrayList<>();
    Stack<TreeNode> stack = new Stack<>();
    TreeNode curr = root;
    while (curr != null || !stack.isEmpty()) {
        while (curr != null) {
            stack.push(curr);
            curr = curr.left;
        }
        curr = stack.pop();
        res.add(curr.val);
        curr = curr.right;
    }
    return res;
}
10.2. Evaluate Reverse Polish Notation (Medium)
Evaluate the value of an arithmetic expression in Reverse Polish Notation.
Pattern: Use a stack to simulate the recursive evaluation process.

10.3. Flatten Binary Tree to Linked List (Medium)
Flatten a binary tree to a linked list without using recursion.
Pattern: Use a stack to simulate recursive calls.

10.4. Decode String (Medium)
Decode a string encoded with numbers and brackets without recursion.
Pattern: Use a stack to manage the recursive-like behavior.

10.5. Binary Tree Preorder Traversal (Easy)
Implement the preorder traversal of a binary tree without recursion.
Pattern: Use a stack to simulate the traversal.

11. Sorted Arrays
11.1. Search in Rotated Sorted Array (Medium)
Search for a target value in a rotated sorted array.
Pattern: Use binary search, adapting for the rotated array.

java
Copy code
public int search(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] == target) return mid;
        if (nums[left] <= nums[mid]) {
            if (target >= nums[left] && target < nums[mid]) right = mid - 1;
            else left = mid + 1;
        } else {
            if (target > nums[mid] && target <= nums[right]) left = mid + 1;
            else right = mid - 1;
        }
    }
    return -1;
}
11.2. Find First and Last Position of Element in Sorted Array (Medium)
Find the starting and ending position of a given target value in a sorted array.
Pattern: Binary search to find bounds.

11.3. Median of Two Sorted Arrays (Hard)
Find the median of two sorted arrays.
Pattern: Binary search across arrays.

11.4. Two Sum II - Input Array Is Sorted (Medium)
Find two numbers such that they add up to a specific target number in a sorted array.
Pattern: Use two pointers to find the sum efficiently.

11.5. Search a 2D Matrix (Medium)
Search for a target in a matrix where each row is sorted and the first integer of each row is greater than the last integer of the previous row.
Pattern: Use binary search.

This extended set of problems will give you further practice on a wide range






You said:
Continue 
ChatGPT said:
ChatGPT
Sure! Let's continue with the remaining categories.

12. Tree Problems
12.1. Invert Binary Tree (Easy)
Invert a binary tree, where the left and right children of all nodes are swapped.
Pattern: Use DFS or BFS to swap children at each node.

java
Copy code
public TreeNode invertTree(TreeNode root) {
    if (root == null) return null;
    TreeNode temp = root.left;
    root.left = root.right;
    root.right = temp;
    invertTree(root.left);
    invertTree(root.right);
    return root;
}
12.2. Path Sum (Easy)
Given a binary tree and a target sum, determine if the tree has a root-to-leaf path such that the sum of the node values equals the target sum.
Pattern: DFS to explore all root-to-leaf paths.

12.3. Construct Binary Tree from Preorder and Inorder Traversal (Medium)
Construct a binary tree from its preorder and inorder traversal sequences.
Pattern: Recursively split preorder and inorder arrays to rebuild the tree.

12.4. Binary Tree Maximum Path Sum (Hard)
Find the maximum path sum in a binary tree where the path can start and end at any node.
Pattern: DFS to explore all possible paths and track maximum sum.

12.5. Serialize and Deserialize Binary Tree (Hard)
Design an algorithm to serialize and deserialize a binary tree.
Pattern: Use BFS for serialization and deserialization.

13. Greedy Algorithms
13.1. Jump Game (Medium)
Given an array of non-negative integers, where each number represents the maximum jump length at that position, determine if you can reach the last index.
Pattern: Greedy approach by tracking the furthest reachable index.

java
Copy code
public boolean canJump(int[] nums) {
    int reachable = 0;
    for (int i = 0; i < nums.length; i++) {
        if (i > reachable) return false;
        reachable = Math.max(reachable, i + nums[i]);
    }
    return true;
}
13.2. Gas Station (Medium)
Given a circular route of gas stations, determine if you can complete the circuit starting at any gas station.
Pattern: Greedily track the cumulative gas surplus/deficit.

13.3. Candy (Hard)
There are n children standing in a line, each with a rating. You must distribute candies such that each child has at least one candy and children with a higher rating get more candies than their neighbors.
Pattern: Greedy approach with two passes through the array.

13.4. Task Scheduler (Medium)
Given a list of tasks and a cooldown period, determine the minimum time needed to execute all tasks while respecting the cooldown period between similar tasks.
Pattern: Greedy scheduling by maximizing task frequency.

13.5. Minimum Number of Arrows to Burst Balloons (Medium)
Given a list of intervals representing balloon positions, find the minimum number of arrows required to burst all balloons.
Pattern: Greedy algorithm based on sorting intervals.

14. Bit Manipulation
14.1. Single Number (Easy)
Given a non-empty array of integers where every element appears twice except for one, find the single element.
Pattern: Use XOR to cancel out duplicate numbers.

java
Copy code
public int singleNumber(int[] nums) {
    int result = 0;
    for (int num : nums) {
        result ^= num;
    }
    return result;
}
14.2. Reverse Bits (Easy)
Reverse the bits of a given 32-bit unsigned integer.
Pattern: Use bitwise operations to reverse the bits one by one.

14.3. Power of Two (Easy)
Given an integer, write a function to determine if it is a power of two.
Pattern: Use bitwise manipulation to check for the condition.

14.4. Counting Bits (Medium)
Given a number n, return an array of integers representing the number of 1s in the binary representation of each number from 0 to n.
Pattern: Use bitwise operations to count bits efficiently.

14.5. Subsets Using Bitmask (Medium)
Generate all subsets of a set using a bitmask approach.
Pattern: Use bitmasking to generate all possible subsets.

15. Two Pointers
15.1. Container With Most Water (Medium)
Given n non-negative integers representing an elevation map where the width of each bar is 1, find the two lines that can contain the most water.
Pattern: Use two pointers to maximize the area by adjusting both ends.

java
Copy code
public int maxArea(int[] height) {
    int left = 0, right = height.length - 1;
    int maxArea = 0;
    while (left < right) {
        int area = Math.min(height[left], height[right]) * (right - left);
        maxArea = Math.max(maxArea, area);
        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }
    return maxArea;
}
15.2. Two Sum II (Easy)
Find two numbers such that they add up to a specific target, given that the input array is sorted.
Pattern: Use two pointers to find the sum efficiently.

15.3. 3Sum (Medium)
Given an array of integers, find all unique triplets such that the sum of the three integers is zero.
Pattern: Use two pointers to reduce the complexity of the three-sum search.

15.4. Remove Duplicates from Sorted Array II (Medium)
Remove duplicates from a sorted array such that each element appears at most twice.
Pattern: Use two pointers to manage duplicates.

15.5. Sort Colors (Medium)
Given an array with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.
Pattern: Use the two-pointer approach (Dutch National Flag problem).

16. Intervals
16.1. Merge Intervals (Medium)
Given a collection of intervals, merge all overlapping intervals.
Pattern: Sort intervals and then merge overlapping intervals.

java
Copy code
public int[][] merge(int[][] intervals) {
    if (intervals.length == 0) return new int[0][];
    Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
    List<int[]> merged = new ArrayList<>();
    int[] current = intervals[0];
    merged.add(current);
    for (int[] interval : intervals) {
        if (interval[0] <= current[1]) {
            current[1] = Math.max(current[1], interval[1]);
        } else {
            current = interval;
            merged.add(current);
        }
    }
    return merged.toArray(new int[merged.size()][]);
}
16.2. Insert Interval (Medium)
Given a set of non-overlapping intervals, insert a new interval into the set (merge if necessary).
Pattern: Handle the merge based on overlapping conditions.

16.3. Meeting Rooms (Easy)
Given an array of meeting time intervals, determine if a person could attend all meetings.
Pattern: Check for overlapping intervals.

16.4. Meeting Rooms II (Medium)
Find the minimum number of meeting rooms required, given meeting intervals.
Pattern: Sort intervals and track the maximum overlapping intervals.

16.5. Non-overlapping Intervals (Medium)
Given a set of intervals, find the minimum number of intervals you need to remove to make the rest non-overlapping.
Pattern: Greedily remove intervals that overlap the most.

This completes the DSA patterns-based question set. The problems cover a range of difficulties and are designed to help you master common patterns used in coding interviews, particularly in languages like Java.






You said:
Continue 
ChatGPT said:
ChatGPT
You’ve reached the conclusion of the pattern-based problem sets. All key patterns have been covered, each accompanied by a set of sample questions designed to help you practice and recognize these patterns in interviews.

To summarize the covered categories:

Graph Problems
Sliding Window
Linked Lists
Maximum/Minimum Subarrays
In-Place Operations
Top/Least K Elements
Permutations/Subsets
Common String Problems
Recursion-Banned Problems
Sorted Arrays
Tree Problems
Greedy Algorithms
Bit Manipulation
Two Pointers
Intervals
If you're seeking additional problem sets in more advanced or specialized areas like dynamic programming, segment trees, or matrices, feel free to ask. You can also consider building a custom study plan based on your target companies or areas of weakness.

Would you like to explore any specific pattern further or dive into advanced concepts? Let me know how I can assist you next!






You said:

Screenshot_2024-10-05-07-35-17-452_com.linkedin.android.jpg
Image
ChatGPT said:
ChatGPT
It looks like you've uploaded a screenshot. However, I currently can't view image files directly. Could you describe the content of the screenshot, or let me know how you'd like me to assist with it?






You said:
Rearrange the above 15 topics in priority order
ChatGPT said:
ChatGPT
Here’s a priority order for the 15 data structure and algorithm topics, tailored for coding interviews, especially for companies like FAANG, based on the frequency and versatility of the patterns:

Priority Order for Interview Preparation:
Two Pointers
Commonly used for problems involving arrays and linked lists. Essential for problems like searching, sorting, and finding pairs or triplets.

Sliding Window
Very useful for array and string problems involving subarrays or substrings, where you need to optimize space and time complexity.

Graph Problems
Fundamental for solving problems related to traversal (DFS/BFS), shortest paths, and cycles, which frequently appear in interviews.

Greedy Algorithms
Frequently tested due to their ability to simplify complex optimization problems (e.g., intervals, scheduling, and greedy selections).

Tree Problems
Understanding tree traversal, binary search trees, and balanced trees is essential. Problems involving DFS/BFS are common.

Intervals
Interval problems are frequent in interviews, particularly in scenarios involving scheduling, merging intervals, and meeting rooms.

Top/Least K Elements
Important for heap-based problems and selection algorithms. Kth largest/smallest elements are frequently tested.

In-Place Operations
Often seen in array-based questions, where optimizing space complexity is critical.

Permutations/Subsets
Backtracking problems often come up for problems that involve permutations, combinations, and subsets.

Recursion-Banned Problems
These include recursion-converted-to-iteration, which is useful when recursion exceeds limits or for optimizing recursion space complexity.

Maximum/Minimum Subarrays
Subarrays and dynamic programming problems, such as Kadane’s algorithm, are important for optimizing sums and finding extremes in arrays.

Linked Lists
Key operations such as reversing, cycle detection, and merging lists appear frequently in interviews, though they are more specific than arrays.

Sorted Arrays
Binary search is crucial but may be easier to master compared to other more versatile patterns like two pointers or sliding windows.

Common String Problems
Problems on strings can involve various techniques, but typically require understanding basic data structures like hashmaps or tries.

Bit Manipulation
This is useful but tends to be a niche area. Bit manipulation problems appear less frequently but can be important for low-level optimizations.