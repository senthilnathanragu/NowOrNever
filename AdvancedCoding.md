# TCS NQT — Advanced Coding in Java: Complete Prime Package Guide

**Section Overview:** 2 problems | 90 minutes | The section that wins you Prime
This is where your fate is decided. Not just TCS placement — but **Prime package specifically.** Every concept, every pattern, every edge case you'll ever need — all in Java — is in this guide. Read it. Code it. Own it.

---

## 📌 JAVA SETUP — WHAT YOU MUST KNOW BEFORE YOU CODE

### The TCS Template — Start Every Solution With This

```java
import java.util.*;
import java.io.*;

public class Solution {
    
    // ─── HELPER METHODS GO HERE ───
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        // Read input
        int n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        
        // Call your solution
        System.out.println(solve(arr, n));
        
        sc.close();
    }
    
    static int solve(int[] arr, int n) {
        // Your logic here
        return 0;
    }
}
```

### Essential Java Data Structures — One-Line Cheatsheet

```java
// Array
int[] arr = new int[n];

// ArrayList (dynamic array)
ArrayList<Integer> list = new ArrayList<>();

// LinkedList
LinkedList<Integer> ll = new LinkedList<>();

// Stack
Stack<Integer> stack = new Stack<>();

// Queue
Queue<Integer> queue = new LinkedList<>();

// Deque (double-ended queue)
Deque<Integer> deque = new ArrayDeque<>();

// HashMap
HashMap<Integer, Integer> map = new HashMap<>();

// HashSet
HashSet<Integer> set = new HashSet<>();

// TreeMap (sorted map)
TreeMap<Integer, Integer> tmap = new TreeMap<>();

// PriorityQueue (min-heap by default)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

// PriorityQueue (max-heap)
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());

// Sort array
Arrays.sort(arr);

// Sort ArrayList
Collections.sort(list);

// Fill array with value
Arrays.fill(arr, 0);

// Copy array
int[] copy = Arrays.copyOf(arr, arr.length);
```

---

## 1. ARRAYS — THE BACKBONE OF TCS CODING

### 1.1 Kadane's Algorithm — Maximum Subarray Sum

**Why it matters:** TCS has asked this or a variant in almost every year.

```java
import java.util.*;

public class KadanesAlgorithm {

    // Returns maximum subarray sum
    static int maxSubarraySum(int[] arr) {
        int maxSum = arr[0];
        int currentSum = arr[0];

        for (int i = 1; i < arr.length; i++) {
            // Either extend previous subarray or start fresh
            currentSum = Math.max(arr[i], currentSum + arr[i]);
            maxSum = Math.max(maxSum, currentSum);
        }
        return maxSum;
    }

    // Returns the actual subarray too (indices)
    static int[] maxSubarrayWithIndices(int[] arr) {
        int maxSum = arr[0];
        int currentSum = arr[0];
        int start = 0, end = 0, tempStart = 0;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > currentSum + arr[i]) {
                currentSum = arr[i];
                tempStart = i;
            } else {
                currentSum += arr[i];
            }

            if (currentSum > maxSum) {
                maxSum = currentSum;
                start = tempStart;
                end = i;
            }
        }

        System.out.println("Max Sum: " + maxSum);
        System.out.println("Subarray from index " + start + " to " + end);
        return Arrays.copyOfRange(arr, start, end + 1);
    }

    public static void main(String[] args) {
        int[] arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println(maxSubarraySum(arr)); // 6
        System.out.println(Arrays.toString(maxSubarrayWithIndices(arr))); // [4,-1,2,1]
    }
}
```

---

### 1.2 Prefix Sum — Range Queries in O(1)

```java
public class PrefixSum {

    static int[] buildPrefix(int[] arr) {
        int n = arr.length;
        int[] prefix = new int[n + 1]; // prefix[0] = 0
        for (int i = 0; i < n; i++) {
            prefix[i + 1] = prefix[i] + arr[i];
        }
        return prefix;
    }

    // Sum of arr[l..r] inclusive (0-indexed)
    static int rangeSum(int[] prefix, int l, int r) {
        return prefix[r + 1] - prefix[l];
    }

    // Count subarrays with sum equal to k — very common TCS question
    static int subarraySumEqualsK(int[] arr, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1); // empty subarray has sum 0
        int count = 0, sum = 0;

        for (int num : arr) {
            sum += num;
            // If (sum - k) was seen before, those subarrays sum to k
            count += map.getOrDefault(sum - k, 0);
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }
        return count;
    }

    public static void main(String[] args) {
        int[] arr = {3, 1, 4, 1, 5, 9, 2, 6};
        int[] prefix = buildPrefix(arr);

        System.out.println(rangeSum(prefix, 2, 5)); // 19 (4+1+5+9)
        System.out.println(rangeSum(prefix, 0, 3)); // 9 (3+1+4+1)

        int[] arr2 = {1, 1, 1};
        System.out.println(subarraySumEqualsK(arr2, 2)); // 2
    }
}
```

---

### 1.3 Two Pointer Technique

```java
public class TwoPointer {

    // Two Sum — sorted array
    static int[] twoSumSorted(int[] arr, int target) {
        int left = 0, right = arr.length - 1;

        while (left < right) {
            int sum = arr[left] + arr[right];
            if (sum == target) return new int[]{left, right};
            else if (sum < target) left++;
            else right--;
        }
        return new int[]{-1, -1};
    }

    // Remove duplicates from sorted array in-place
    static int removeDuplicates(int[] arr) {
        if (arr.length == 0) return 0;
        int slow = 0;

        for (int fast = 1; fast < arr.length; fast++) {
            if (arr[fast] != arr[slow]) {
                slow++;
                arr[slow] = arr[fast];
            }
        }
        return slow + 1; // new length
    }

    // Container with most water
    static int maxWater(int[] height) {
        int left = 0, right = height.length - 1;
        int maxWater = 0;

        while (left < right) {
            int water = Math.min(height[left], height[right]) * (right - left);
            maxWater = Math.max(maxWater, water);

            // Move the shorter wall inward
            if (height[left] < height[right]) left++;
            else right--;
        }
        return maxWater;
    }

    // Three Sum — find all triplets that sum to zero
    static List<List<Integer>> threeSum(int[] arr) {
        Arrays.sort(arr);
        List<List<Integer>> result = new ArrayList<>();

        for (int i = 0; i < arr.length - 2; i++) {
            // Skip duplicates for i
            if (i > 0 && arr[i] == arr[i - 1]) continue;

            int left = i + 1, right = arr.length - 1;
            while (left < right) {
                int sum = arr[i] + arr[left] + arr[right];
                if (sum == 0) {
                    result.add(Arrays.asList(arr[i], arr[left], arr[right]));
                    while (left < right && arr[left] == arr[left + 1]) left++;
                    while (left < right && arr[right] == arr[right - 1]) right--;
                    left++;
                    right--;
                } else if (sum < 0) left++;
                else right--;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[] arr = {2, 7, 11, 15};
        System.out.println(Arrays.toString(twoSumSorted(arr, 9))); // [0, 1]

        int[] arr2 = {-1, 0, 1, 2, -1, -4};
        System.out.println(threeSum(arr2)); // [[-1,-1,2],[-1,0,1]]
    }
}
```

---

### 1.4 Sliding Window Technique

```java
public class SlidingWindow {

    // Maximum sum of subarray of size k
    static int maxSumKSize(int[] arr, int k) {
        int windowSum = 0;

        // First window
        for (int i = 0; i < k; i++) {
            windowSum += arr[i];
        }

        int maxSum = windowSum;

        // Slide window: add next, remove first
        for (int i = k; i < arr.length; i++) {
            windowSum += arr[i] - arr[i - k];
            maxSum = Math.max(maxSum, windowSum);
        }
        return maxSum;
    }

    // Longest substring without repeating characters
    static int longestUniqueSubstring(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        int maxLen = 0, left = 0;

        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);

            // If char seen before and is inside current window
            if (map.containsKey(c) && map.get(c) >= left) {
                left = map.get(c) + 1; // shrink window
            }

            map.put(c, right);
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    // Minimum size subarray with sum >= target
    static int minSizeSubarray(int[] arr, int target) {
        int left = 0, sum = 0, minLen = Integer.MAX_VALUE;

        for (int right = 0; right < arr.length; right++) {
            sum += arr[right];

            while (sum >= target) {
                minLen = Math.min(minLen, right - left + 1);
                sum -= arr[left++]; // shrink from left
            }
        }
        return minLen == Integer.MAX_VALUE ? 0 : minLen;
    }

    // Longest substring with at most k distinct characters
    static int longestSubstringKDistinct(String s, int k) {
        HashMap<Character, Integer> freq = new HashMap<>();
        int left = 0, maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            freq.put(c, freq.getOrDefault(c, 0) + 1);

            while (freq.size() > k) {
                char leftChar = s.charAt(left);
                freq.put(leftChar, freq.get(leftChar) - 1);
                if (freq.get(leftChar) == 0) freq.remove(leftChar);
                left++;
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    public static void main(String[] args) {
        int[] arr = {2, 3, 4, 1, 5};
        System.out.println(maxSumKSize(arr, 3));          // 9

        System.out.println(longestUniqueSubstring("abcabcbb")); // 3

        int[] arr2 = {2, 3, 1, 2, 4, 3};
        System.out.println(minSizeSubarray(arr2, 7));     // 2

        System.out.println(longestSubstringKDistinct("eceba", 2)); // 3
    }
}
```

---

### 1.5 Sorting Algorithms — Know These Cold

```java
public class SortingAlgorithms {

    // Merge Sort — O(n log n) — stable sort
    static void mergeSort(int[] arr, int left, int right) {
        if (left >= right) return;

        int mid = (left + right) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }

    static void merge(int[] arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int[] L = new int[n1];
        int[] R = new int[n2];

        System.arraycopy(arr, left, L, 0, n1);
        System.arraycopy(arr, mid + 1, R, 0, n2);

        int i = 0, j = 0, k = left;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) arr[k++] = L[i++];
            else arr[k++] = R[j++];
        }
        while (i < n1) arr[k++] = L[i++];
        while (j < n2) arr[k++] = R[j++];
    }

    // Quick Sort — O(n log n) average — in-place
    static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    static int partition(int[] arr, int low, int high) {
        int pivot = arr[high]; // last element as pivot
        int i = low - 1;

        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                int temp = arr[i]; arr[i] = arr[j]; arr[j] = temp;
            }
        }
        int temp = arr[i+1]; arr[i+1] = arr[high]; arr[high] = temp;
        return i + 1;
    }

    // Count Inversions (merge sort variant) — very common TCS problem
    static long countInversions(int[] arr, int left, int right) {
        long count = 0;
        if (left < right) {
            int mid = (left + right) / 2;
            count += countInversions(arr, left, mid);
            count += countInversions(arr, mid + 1, right);
            count += mergeCount(arr, left, mid, right);
        }
        return count;
    }

    static long mergeCount(int[] arr, int left, int mid, int right) {
        int[] L = Arrays.copyOfRange(arr, left, mid + 1);
        int[] R = Arrays.copyOfRange(arr, mid + 1, right + 1);

        int i = 0, j = 0, k = left;
        long count = 0;

        while (i < L.length && j < R.length) {
            if (L[i] <= R[j]) {
                arr[k++] = L[i++];
            } else {
                // L[i..end] are all greater than R[j] → inversions
                count += (L.length - i);
                arr[k++] = R[j++];
            }
        }
        while (i < L.length) arr[k++] = L[i++];
        while (j < R.length) arr[k++] = R[j++];
        return count;
    }

    public static void main(String[] args) {
        int[] arr1 = {5, 3, 8, 1, 2};
        mergeSort(arr1, 0, arr1.length - 1);
        System.out.println(Arrays.toString(arr1)); // [1, 2, 3, 5, 8]

        int[] arr2 = {5, 3, 8, 1, 2};
        quickSort(arr2, 0, arr2.length - 1);
        System.out.println(Arrays.toString(arr2)); // [1, 2, 3, 5, 8]

        int[] arr3 = {2, 4, 1, 3, 5};
        System.out.println(countInversions(arr3, 0, arr3.length - 1)); // 3
    }
}
```

---

## 2. STRINGS — HIGH-FREQUENCY TCS TOPIC

```java
public class StringProblems {

    // Reverse words in a sentence
    static String reverseWords(String s) {
        String[] words = s.trim().split("\\s+");
        StringBuilder sb = new StringBuilder();
        for (int i = words.length - 1; i >= 0; i--) {
            sb.append(words[i]);
            if (i != 0) sb.append(" ");
        }
        return sb.toString();
    }

    // Check if string is palindrome (ignoring non-alphanumeric)
    static boolean isPalindrome(String s) {
        int left = 0, right = s.length() - 1;
        while (left < right) {
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) left++;
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) right--;
            if (Character.toLowerCase(s.charAt(left)) !=
                Character.toLowerCase(s.charAt(right))) return false;
            left++;
            right--;
        }
        return true;
    }

    // Longest palindromic substring — expand around center
    static String longestPalindrome(String s) {
        if (s.length() < 2) return s;
        int start = 0, maxLen = 1;

        for (int i = 0; i < s.length(); i++) {
            // Odd length
            int len1 = expandAroundCenter(s, i, i);
            // Even length
            int len2 = expandAroundCenter(s, i, i + 1);
            int len = Math.max(len1, len2);

            if (len > maxLen) {
                maxLen = len;
                start = i - (len - 1) / 2;
            }
        }
        return s.substring(start, start + maxLen);
    }

    static int expandAroundCenter(String s, int left, int right) {
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
        }
        return right - left - 1;
    }

    // Anagram check
    static boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] count = new int[26];
        for (char c : s.toCharArray()) count[c - 'a']++;
        for (char c : t.toCharArray()) {
            count[c - 'a']--;
            if (count[c - 'a'] < 0) return false;
        }
        return true;
    }

    // String compression (Run-length encoding)
    static String compress(String s) {
        if (s.isEmpty()) return s;
        StringBuilder sb = new StringBuilder();
        int count = 1;

        for (int i = 1; i <= s.length(); i++) {
            if (i < s.length() && s.charAt(i) == s.charAt(i - 1)) {
                count++;
            } else {
                sb.append(s.charAt(i - 1));
                if (count > 1) sb.append(count);
                count = 1;
            }
        }
        return sb.length() < s.length() ? sb.toString() : s;
    }

    // Roman to Integer
    static int romanToInt(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        map.put('I', 1); map.put('V', 5); map.put('X', 10);
        map.put('L', 50); map.put('C', 100); map.put('D', 500);
        map.put('M', 1000);

        int result = 0;
        for (int i = 0; i < s.length(); i++) {
            int curr = map.get(s.charAt(i));
            int next = (i + 1 < s.length()) ? map.get(s.charAt(i + 1)) : 0;

            if (curr < next) result -= curr;
            else result += curr;
        }
        return result;
    }

    // Count and Say sequence
    static String countAndSay(int n) {
        String result = "1";
        for (int i = 1; i < n; i++) {
            StringBuilder sb = new StringBuilder();
            int count = 1;
            for (int j = 1; j <= result.length(); j++) {
                if (j < result.length() && result.charAt(j) == result.charAt(j - 1)) {
                    count++;
                } else {
                    sb.append(count).append(result.charAt(j - 1));
                    count = 1;
                }
            }
            result = sb.toString();
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(reverseWords("the sky is blue"));       // "blue is sky the"
        System.out.println(isPalindrome("A man, a plan, a canal: Panama")); // true
        System.out.println(longestPalindrome("babad"));            // "bab"
        System.out.println(isAnagram("anagram", "nagaram"));       // true
        System.out.println(compress("aabcccdddd"));                // "a2bc3d4"
        System.out.println(romanToInt("MCMXCIV"));                 // 1994
        System.out.println(countAndSay(5));                        // "111221"
    }
}
```

---

## 3. HASHING — THE MOST POWERFUL TOOL FOR PRIME

```java
import java.util.*;

public class HashingProblems {

    // Two Sum — return indices (unsorted array)
    static int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{-1, -1};
    }

    // Longest consecutive sequence — O(n)
    static int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : nums) set.add(num);

        int maxLen = 0;

        for (int num : set) {
            // Only start counting from the beginning of a sequence
            if (!set.contains(num - 1)) {
                int current = num;
                int currentLen = 1;

                while (set.contains(current + 1)) {
                    current++;
                    currentLen++;
                }
                maxLen = Math.max(maxLen, currentLen);
            }
        }
        return maxLen;
    }

    // First non-repeating character in a string
    static char firstNonRepeating(String s) {
        LinkedHashMap<Character, Integer> map = new LinkedHashMap<>();
        for (char c : s.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        for (Map.Entry<Character, Integer> entry : map.entrySet()) {
            if (entry.getValue() == 1) return entry.getKey();
        }
        return '_';
    }

    // Majority element (appears more than n/2 times) — Boyer-Moore
    static int majorityElement(int[] nums) {
        int candidate = nums[0], count = 1;
        for (int i = 1; i < nums.length; i++) {
            if (count == 0) {
                candidate = nums[i];
                count = 1;
            } else if (nums[i] == candidate) {
                count++;
            } else {
                count--;
            }
        }
        return candidate;
    }

    // Subarray with zero sum
    static boolean hasZeroSumSubarray(int[] arr) {
        HashSet<Integer> set = new HashSet<>();
        set.add(0);
        int sum = 0;
        for (int num : arr) {
            sum += num;
            if (set.contains(sum)) return true;
            set.add(sum);
        }
        return false;
    }

    // Group anagrams
    static List<List<String>> groupAnagrams(String[] words) {
        HashMap<String, List<String>> map = new HashMap<>();
        for (String word : words) {
            char[] chars = word.toCharArray();
            Arrays.sort(chars);
            String key = new String(chars);
            map.computeIfAbsent(key, k -> new ArrayList<>()).add(word);
        }
        return new ArrayList<>(map.values());
    }

    // Longest subarray with equal 0s and 1s (replace 0 with -1, find longest zero-sum)
    static int longestEqualZeroOne(int[] arr) {
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, -1);
        int sum = 0, maxLen = 0;
        for (int i = 0; i < arr.length; i++) {
            sum += (arr[i] == 0) ? -1 : 1;
            if (map.containsKey(sum)) {
                maxLen = Math.max(maxLen, i - map.get(sum));
            } else {
                map.put(sum, i);
            }
        }
        return maxLen;
    }

    public static void main(String[] args) {
        System.out.println(Arrays.toString(twoSum(new int[]{2,7,11,15}, 9))); // [0,1]
        System.out.println(longestConsecutive(new int[]{100,4,200,1,3,2}));   // 4
        System.out.println(firstNonRepeating("aabbcde"));                     // c
        System.out.println(majorityElement(new int[]{2,2,1,1,1,2,2}));       // 2
        System.out.println(hasZeroSumSubarray(new int[]{3,4,-7,1,2}));       // true
        System.out.println(longestEqualZeroOne(new int[]{0,1,0,1,1,0,0}));  // 6
    }
}
```

---

## 4. STACK & QUEUE — ESSENTIAL PATTERNS

```java
import java.util.*;

public class StackQueueProblems {

    // Valid Parentheses — extremely common TCS question
    static boolean isValidParentheses(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            } else {
                if (stack.isEmpty()) return false;
                char top = stack.pop();
                if (c == ')' && top != '(') return false;
                if (c == '}' && top != '{') return false;
                if (c == ']' && top != '[') return false;
            }
        }
        return stack.isEmpty();
    }

    // Next Greater Element
    static int[] nextGreaterElement(int[] arr) {
        int n = arr.length;
        int[] result = new int[n];
        Arrays.fill(result, -1);
        Stack<Integer> stack = new Stack<>(); // stores indices

        for (int i = 0; i < n; i++) {
            while (!stack.isEmpty() && arr[i] > arr[stack.peek()]) {
                result[stack.pop()] = arr[i];
            }
            stack.push(i);
        }
        return result;
    }

    // Largest rectangle in histogram — classic TCS hard problem
    static int largestRectangle(int[] heights) {
        int n = heights.length;
        Stack<Integer> stack = new Stack<>();
        int maxArea = 0;

        for (int i = 0; i <= n; i++) {
            int currHeight = (i == n) ? 0 : heights[i];

            while (!stack.isEmpty() && currHeight < heights[stack.peek()]) {
                int h = heights[stack.pop()];
                int w = stack.isEmpty() ? i : i - stack.peek() - 1;
                maxArea = Math.max(maxArea, h * w);
            }
            stack.push(i);
        }
        return maxArea;
    }

    // Min Stack — supports getMin() in O(1)
    static class MinStack {
        Stack<Integer> stack = new Stack<>();
        Stack<Integer> minStack = new Stack<>();

        void push(int val) {
            stack.push(val);
            if (minStack.isEmpty() || val <= minStack.peek()) {
                minStack.push(val);
            }
        }

        void pop() {
            int val = stack.pop();
            if (val == minStack.peek()) minStack.pop();
        }

        int top() { return stack.peek(); }
        int getMin() { return minStack.peek(); }
    }

    // Evaluate Reverse Polish Notation
    static int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>();
        for (String token : tokens) {
            if ("+-*/".contains(token)) {
                int b = stack.pop();
                int a = stack.pop();
                switch (token) {
                    case "+": stack.push(a + b); break;
                    case "-": stack.push(a - b); break;
                    case "*": stack.push(a * b); break;
                    case "/": stack.push(a / b); break;
                }
            } else {
                stack.push(Integer.parseInt(token));
            }
        }
        return stack.pop();
    }

    // Sliding Window Maximum using Deque — O(n)
    static int[] slidingWindowMax(int[] arr, int k) {
        int n = arr.length;
        int[] result = new int[n - k + 1];
        Deque<Integer> deque = new ArrayDeque<>(); // stores indices

        for (int i = 0; i < n; i++) {
            // Remove elements outside window
            while (!deque.isEmpty() && deque.peekFirst() < i - k + 1) {
                deque.pollFirst();
            }
            // Remove smaller elements from back
            while (!deque.isEmpty() && arr[deque.peekLast()] < arr[i]) {
                deque.pollLast();
            }
            deque.offerLast(i);

            if (i >= k - 1) {
                result[i - k + 1] = arr[deque.peekFirst()];
            }
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(isValidParentheses("{[()]}"));            // true
        System.out.println(isValidParentheses("{[(])}"));            // false

        System.out.println(Arrays.toString(
            nextGreaterElement(new int[]{4, 5, 2, 10, 8})
        )); // [5, 10, 10, -1, -1]

        System.out.println(largestRectangle(new int[]{2,1,5,6,2,3})); // 10

        System.out.println(evalRPN(new String[]{"2","1","+","3","*"})); // 9

        System.out.println(Arrays.toString(
            slidingWindowMax(new int[]{1,3,-1,-3,5,3,6,7}, 3)
        )); // [3,3,5,5,6,7]
    }
}
```

---

## 5. RECURSION & BACKTRACKING

```java
import java.util.*;

public class RecursionBacktracking {

    // Fibonacci with memoization
    static HashMap<Integer, Long> memo = new HashMap<>();

    static long fib(int n) {
        if (n <= 1) return n;
        if (memo.containsKey(n)) return memo.get(n);
        long result = fib(n - 1) + fib(n - 2);
        memo.put(n, result);
        return result;
    }

    // Power function — fast exponentiation O(log n)
    static long power(long base, long exp, long mod) {
        long result = 1;
        base %= mod;
        while (exp > 0) {
            if ((exp & 1) == 1) result = result * base % mod;
            base = base * base % mod;
            exp >>= 1;
        }
        return result;
    }

    // All permutations of a string
    static List<String> permutations(String s) {
        List<String> result = new ArrayList<>();
        permHelper(s.toCharArray(), 0, result);
        return result;
    }

    static void permHelper(char[] arr, int start, List<String> result) {
        if (start == arr.length) {
            result.add(new String(arr));
            return;
        }
        for (int i = start; i < arr.length; i++) {
            swap(arr, start, i);
            permHelper(arr, start + 1, result);
            swap(arr, start, i); // backtrack
        }
    }

    static void swap(char[] arr, int i, int j) {
        char temp = arr[i]; arr[i] = arr[j]; arr[j] = temp;
    }

    // Generate all subsets (Power Set)
    static List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        subsetsHelper(nums, 0, new ArrayList<>(), result);
        return result;
    }

    static void subsetsHelper(int[] nums, int index,
                               List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));
        for (int i = index; i < nums.length; i++) {
            current.add(nums[i]);
            subsetsHelper(nums, i + 1, current, result);
            current.remove(current.size() - 1); // backtrack
        }
    }

    // N-Queens Problem
    static List<List<String>> solveNQueens(int n) {
        List<List<String>> result = new ArrayList<>();
        int[] queens = new int[n]; // queens[i] = column of queen in row i
        Arrays.fill(queens, -1);
        nQueensHelper(queens, 0, n, result);
        return result;
    }

    static void nQueensHelper(int[] queens, int row, int n,
                               List<List<String>> result) {
        if (row == n) {
            result.add(buildBoard(queens, n));
            return;
        }
        for (int col = 0; col < n; col++) {
            if (isValid(queens, row, col)) {
                queens[row] = col;
                nQueensHelper(queens, row + 1, n, result);
                queens[row] = -1; // backtrack
            }
        }
    }

    static boolean isValid(int[] queens, int row, int col) {
        for (int i = 0; i < row; i++) {
            if (queens[i] == col) return false; // same column
            if (Math.abs(queens[i] - col) == Math.abs(i - row)) return false; // diagonal
        }
        return true;
    }

    static List<String> buildBoard(int[] queens, int n) {
        List<String> board = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            char[] row = new char[n];
            Arrays.fill(row, '.');
            row[queens[i]] = 'Q';
            board.add(new String(row));
        }
        return board;
    }

    // Combination Sum — find all combinations summing to target
    static List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(candidates);
        combinationHelper(candidates, target, 0, new ArrayList<>(), result);
        return result;
    }

    static void combinationHelper(int[] candidates, int remaining, int start,
                                   List<Integer> current, List<List<Integer>> result) {
        if (remaining == 0) {
            result.add(new ArrayList<>(current));
            return;
        }
        for (int i = start; i < candidates.length; i++) {
            if (candidates[i] > remaining) break; // pruning
            current.add(candidates[i]);
            combinationHelper(candidates, remaining - candidates[i], i, current, result);
            current.remove(current.size() - 1); // backtrack
        }
    }

    public static void main(String[] args) {
        System.out.println(fib(10));                   // 55
        System.out.println(power(2, 10, 1000000007));  // 1024
        System.out.println(permutations("abc").size()); // 6
        System.out.println(subsets(new int[]{1,2,3})); // 8 subsets
        System.out.println(solveNQueens(4).size());    // 2 solutions
        System.out.println(combinationSum(new int[]{2,3,6,7}, 7));
        // [[2,2,3],[7]]
    }
}
```

---

## 6. DYNAMIC PROGRAMMING — THE PRIME DECIDER

**This is the single most tested topic for Prime package.** If you can solve DP problems, you can solve almost anything TCS throws at you.

### 6.1 Classic 1D DP

```java
public class DynamicProgramming1D {

    // Climbing Stairs (1 or 2 steps at a time)
    static int climbStairs(int n) {
        if (n <= 2) return n;
        int prev2 = 1, prev1 = 2;
        for (int i = 3; i <= n; i++) {
            int curr = prev1 + prev2;
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }

    // House Robber — can't rob adjacent houses
    static int rob(int[] nums) {
        if (nums.length == 1) return nums[0];
        int prev2 = nums[0];
        int prev1 = Math.max(nums[0], nums[1]);

        for (int i = 2; i < nums.length; i++) {
            int curr = Math.max(prev1, prev2 + nums[i]);
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }

    // Minimum Coin Change
    static int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1); // initialize with impossible value
        dp[0] = 0;

        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (coin <= i) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }
        return dp[amount] > amount ? -1 : dp[amount];
    }

    // Number of ways to make change
    static int coinChangeWays(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        dp[0] = 1;
        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] += dp[i - coin];
            }
        }
        return dp[amount];
    }

    // Longest Increasing Subsequence (LIS) — O(n²)
    static int lis(int[] nums) {
        int n = nums.length;
        int[] dp = new int[n];
        Arrays.fill(dp, 1);
        int maxLen = 1;

        for (int i = 1; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[j] < nums[i]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLen = Math.max(maxLen, dp[i]);
        }
        return maxLen;
    }

    // LIS — O(n log n) with patience sorting
    static int lisOptimal(int[] nums) {
        ArrayList<Integer> tails = new ArrayList<>();
        for (int num : nums) {
            int pos = Collections.binarySearch(tails, num);
            if (pos < 0) pos = -(pos + 1); // insertion point
            if (pos == tails.size()) tails.add(num);
            else tails.set(pos, num);
        }
        return tails.size();
    }

    // Decode Ways (number of ways to decode a digit string)
    // 'A'→1, 'B'→2, ..., 'Z'→26
    static int numDecodings(String s) {
        int n = s.length();
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = s.charAt(0) == '0' ? 0 : 1;

        for (int i = 2; i <= n; i++) {
            int oneDigit = Integer.parseInt(s.substring(i - 1, i));
            int twoDigit = Integer.parseInt(s.substring(i - 2, i));

            if (oneDigit >= 1) dp[i] += dp[i - 1];
            if (twoDigit >= 10 && twoDigit <= 26) dp[i] += dp[i - 2];
        }
        return dp[n];
    }

    public static void main(String[] args) {
        System.out.println(climbStairs(10));                           // 89
        System.out.println(rob(new int[]{2, 7, 9, 3, 1}));           // 12
        System.out.println(coinChange(new int[]{1, 5, 6, 9}, 11));   // 2
        System.out.println(coinChangeWays(new int[]{1,2,5}, 5));     // 4
        System.out.println(lis(new int[]{10,9,2,5,3,7,101,18}));     // 4
        System.out.println(numDecodings("226"));                       // 3
    }
}
```

---

### 6.2 Classic 2D DP — Matrix Problems

```java
public class DynamicProgramming2D {

    // Longest Common Subsequence (LCS) — most important 2D DP
    static int lcs(String s1, String s2) {
        int m = s1.length(), n = s2.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s1.charAt(i - 1) == s2.charAt(j - 1)) {
                    dp[i][j] = dp[i-1][j-1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
        }
        return dp[m][n];
    }

    // Longest Common Substring
    static int longestCommonSubstring(String s1, String s2) {
        int m = s1.length(), n = s2.length();
        int[][] dp = new int[m + 1][n + 1];
        int maxLen = 0;

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s1.charAt(i - 1) == s2.charAt(j - 1)) {
                    dp[i][j] = dp[i-1][j-1] + 1;
                    maxLen = Math.max(maxLen, dp[i][j]);
                }
            }
        }
        return maxLen;
    }

    // Edit Distance (Levenshtein Distance)
    static int editDistance(String s1, String s2) {
        int m = s1.length(), n = s2.length();
        int[][] dp = new int[m + 1][n + 1];

        // Base cases
        for (int i = 0; i <= m; i++) dp[i][0] = i;
        for (int j = 0; j <= n; j++) dp[0][j] = j;

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s1.charAt(i-1) == s2.charAt(j-1)) {
                    dp[i][j] = dp[i-1][j-1];
                } else {
                    dp[i][j] = 1 + Math.min(dp[i-1][j-1],  // replace
                               Math.min(dp[i-1][j],          // delete
                                        dp[i][j-1]));         // insert
                }
            }
        }
        return dp[m][n];
    }

    // 0/1 Knapsack
    static int knapsack(int[] weights, int[] values, int capacity) {
        int n = weights.length;
        int[][] dp = new int[n + 1][capacity + 1];

        for (int i = 1; i <= n; i++) {
            for (int w = 0; w <= capacity; w++) {
                // Don't pick item i
                dp[i][w] = dp[i-1][w];
                // Pick item i (if it fits)
                if (weights[i-1] <= w) {
                    dp[i][w] = Math.max(dp[i][w],
                               dp[i-1][w - weights[i-1]] + values[i-1]);
                }
            }
        }
        return dp[n][capacity];
    }

    // Matrix Chain Multiplication — minimum multiplications
    static int matrixChain(int[] dims) {
        int n = dims.length - 1; // number of matrices
        int[][] dp = new int[n][n];

        // len = chain length
        for (int len = 2; len <= n; len++) {
            for (int i = 0; i <= n - len; i++) {
                int j = i + len - 1;
                dp[i][j] = Integer.MAX_VALUE;
                for (int k = i; k < j; k++) {
                    int cost = dp[i][k] + dp[k+1][j]
                               + dims[i] * dims[k+1] * dims[j+1];
                    dp[i][j] = Math.min(dp[i][j], cost);
                }
            }
        }
        return dp[0][n-1];
    }

    // Minimum path sum in matrix (top-left to bottom-right)
    static int minPathSum(int[][] grid) {
        int m = grid.length, n = grid[0].length;
        int[][] dp = new int[m][n];
        dp[0][0] = grid[0][0];

        // First row
        for (int j = 1; j < n; j++) dp[0][j] = dp[0][j-1] + grid[0][j];
        // First column
        for (int i = 1; i < m; i++) dp[i][0] = dp[i-1][0] + grid[i][0];

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[i][j] = Math.min(dp[i-1][j], dp[i][j-1]) + grid[i][j];
            }
        }
        return dp[m-1][n-1];
    }

    // Boolean Matrix: number of unique paths
    static int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];
        for (int i = 0; i < m; i++) dp[i][0] = 1;
        for (int j = 0; j < n; j++) dp[0][j] = 1;
        for (int i = 1; i < m; i++)
            for (int j = 1; j < n; j++)
                dp[i][j] = dp[i-1][j] + dp[i][j-1];
        return dp[m-1][n-1];
    }

    public static void main(String[] args) {
        System.out.println(lcs("ABCBDAB", "BDCAB"));           // 4
        System.out.println(longestCommonSubstring("ABAB","BABA")); // 3
        System.out.println(editDistance("horse", "ros"));        // 3
        System.out.println(knapsack(
            new int[]{1,3,4,5},
            new int[]{1,4,5,7}, 7));                             // 9
        System.out.println(matrixChain(new int[]{10,30,5,60})); // 4500
        System.out.println(minPathSum(new int[][]{{1,3,1},{1,5,1},{4,2,1}})); // 7
        System.out.println(uniquePaths(3, 7));                   // 28
    }
}
```

---

## 7. TREES — CRUCIAL FOR PRIME

```java
import java.util.*;

public class TreeProblems {

    // Node definition
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
    }

    // ─── TRAVERSALS ───

    // Inorder (Left → Root → Right) — gives sorted output for BST
    static List<Integer> inorder(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        inorderHelper(root, result);
        return result;
    }
    static void inorderHelper(TreeNode node, List<Integer> result) {
        if (node == null) return;
        inorderHelper(node.left, result);
        result.add(node.val);
        inorderHelper(node.right, result);
    }

    // Level Order Traversal (BFS)
    static List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) return result;

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> level = new ArrayList<>();

            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                level.add(node.val);
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }
            result.add(level);
        }
        return result;
    }

    // Height of tree
    static int height(TreeNode root) {
        if (root == null) return 0;
        return 1 + Math.max(height(root.left), height(root.right));
    }

    // Diameter of tree (longest path between any two nodes)
    static int diameter = 0;
    static int diameterOfTree(TreeNode root) {
        diameter = 0;
        diameterHelper(root);
        return diameter;
    }
    static int diameterHelper(TreeNode node) {
        if (node == null) return 0;
        int left = diameterHelper(node.left);
        int right = diameterHelper(node.right);
        diameter = Math.max(diameter, left + right);
        return 1 + Math.max(left, right);
    }

    // Check if tree is balanced
    static boolean isBalanced(TreeNode root) {
        return checkBalance(root) != -1;
    }
    static int checkBalance(TreeNode node) {
        if (node == null) return 0;
        int left = checkBalance(node.left);
        if (left == -1) return -1;
        int right = checkBalance(node.right);
        if (right == -1) return -1;
        if (Math.abs(left - right) > 1) return -1;
        return 1 + Math.max(left, right);
    }

    // Lowest Common Ancestor (LCA)
    static TreeNode lca(TreeNode root, int p, int q) {
        if (root == null || root.val == p || root.val == q) return root;
        TreeNode left = lca(root.left, p, q);
        TreeNode right = lca(root.right, p, q);
        if (left != null && right != null) return root; // p and q on different sides
        return left != null ? left : right;
    }

    // Maximum path sum (any node to any node)
    static int maxPathSum = Integer.MIN_VALUE;
    static int maxPathSumTree(TreeNode root) {
        maxPathSum = Integer.MIN_VALUE;
        maxPathHelper(root);
        return maxPathSum;
    }
    static int maxPathHelper(TreeNode node) {
        if (node == null) return 0;
        int left = Math.max(0, maxPathHelper(node.left));
        int right = Math.max(0, maxPathHelper(node.right));
        maxPathSum = Math.max(maxPathSum, node.val + left + right);
        return node.val + Math.max(left, right);
    }

    // ─── BST OPERATIONS ───

    // Search in BST
    static TreeNode searchBST(TreeNode root, int val) {
        if (root == null || root.val == val) return root;
        return val < root.val ? searchBST(root.left, val)
                              : searchBST(root.right, val);
    }

    // Insert in BST
    static TreeNode insertBST(TreeNode root, int val) {
        if (root == null) return new TreeNode(val);
        if (val < root.val) root.left = insertBST(root.left, val);
        else if (val > root.val) root.right = insertBST(root.right, val);
        return root;
    }

    // Validate BST
    static boolean isValidBST(TreeNode root) {
        return validateBST(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    static boolean validateBST(TreeNode node, long min, long max) {
        if (node == null) return true;
        if (node.val <= min || node.val >= max) return false;
        return validateBST(node.left, min, node.val) &&
               validateBST(node.right, node.val, max);
    }

    // Kth smallest element in BST (inorder gives sorted order)
    static int kthSmallest(TreeNode root, int k) {
        int[] count = {0, 0}; // count[0]=count, count[1]=result
        kthHelper(root, k, count);
        return count[1];
    }
    static void kthHelper(TreeNode node, int k, int[] count) {
        if (node == null) return;
        kthHelper(node.left, k, count);
        count[0]++;
        if (count[0] == k) { count[1] = node.val; return; }
        kthHelper(node.right, k, count);
    }

    // Right side view of tree
    static List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if (root == null) return result;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                if (i == size - 1) result.add(node.val); // rightmost node
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }
        }
        return result;
    }

    public static void main(String[] args) {
        // Build tree:      1
        //                /   \
        //               2     3
        //              / \
        //             4   5
        TreeNode root = new TreeNode(1);
        root.left = new TreeNode(2);
        root.right = new TreeNode(3);
        root.left.left = new TreeNode(4);
        root.left.right = new TreeNode(5);

        System.out.println(inorder(root));      // [4, 2, 5, 1, 3]
        System.out.println(levelOrder(root));   // [[1],[2,3],[4,5]]
        System.out.println(height(root));        // 3
        System.out.println(diameterOfTree(root));// 3
        System.out.println(isBalanced(root));    // true
        System.out.println(rightSideView(root)); // [1, 3, 5]
    }
}
```

---

## 8. GRAPHS — BFS, DFS & CLASSIC ALGORITHMS

```java
import java.util.*;

public class GraphProblems {

    // ─── BFS — Breadth First Search ───
    static void bfs(int[][] adjMatrix, int start, int n) {
        boolean[] visited = new boolean[n];
        Queue<Integer> queue = new LinkedList<>();

        visited[start] = true;
        queue.offer(start);

        System.out.print("BFS: ");
        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");

            for (int neighbor = 0; neighbor < n; neighbor++) {
                if (adjMatrix[node][neighbor] == 1 && !visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.offer(neighbor);
                }
            }
        }
        System.out.println();
    }

    // ─── DFS — Depth First Search ───
    static void dfs(Map<Integer, List<Integer>> graph, int node,
                    boolean[] visited) {
        visited[node] = true;
        System.out.print(node + " ");
        for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
            if (!visited[neighbor]) {
                dfs(graph, neighbor, visited);
            }
        }
    }

    // ─── Detect Cycle in Undirected Graph ───
    static boolean hasCycleUndirected(Map<Integer, List<Integer>> graph, int n) {
        boolean[] visited = new boolean[n];
        for (int i = 0; i < n; i++) {
            if (!visited[i] && dfsHasCycle(graph, i, -1, visited)) {
                return true;
            }
        }
        return false;
    }

    static boolean dfsHasCycle(Map<Integer, List<Integer>> graph,
                                int node, int parent, boolean[] visited) {
        visited[node] = true;
        for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
            if (!visited[neighbor]) {
                if (dfsHasCycle(graph, neighbor, node, visited)) return true;
            } else if (neighbor != parent) {
                return true; // Back edge found = cycle
            }
        }
        return false;
    }

    // ─── Topological Sort (DAG) — Kahn's Algorithm ───
    static List<Integer> topologicalSort(int n, int[][] edges) {
        int[] inDegree = new int[n];
        Map<Integer, List<Integer>> graph = new HashMap<>();

        for (int[] edge : edges) {
            graph.computeIfAbsent(edge[0], k -> new ArrayList<>()).add(edge[1]);
            inDegree[edge[1]]++;
        }

        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < n; i++) {
            if (inDegree[i] == 0) queue.offer(i);
        }

        List<Integer> order = new ArrayList<>();
        while (!queue.isEmpty()) {
            int node = queue.poll();
            order.add(node);
            for (int neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                inDegree[neighbor]--;
                if (inDegree[neighbor] == 0) queue.offer(neighbor);
            }
        }

        return order.size() == n ? order : new ArrayList<>(); // empty = cycle exists
    }

    // ─── Dijkstra's Shortest Path ───
    static int[] dijkstra(int n, int[][] edges, int source) {
        Map<Integer, List<int[]>> graph = new HashMap<>();
        for (int[] edge : edges) {
            graph.computeIfAbsent(edge[0], k -> new ArrayList<>())
                 .add(new int[]{edge[1], edge[2]});
            graph.computeIfAbsent(edge[1], k -> new ArrayList<>())
                 .add(new int[]{edge[0], edge[2]});
        }

        int[] dist = new int[n];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[source] = 0;

        // Min-heap: [distance, node]
        PriorityQueue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));
        pq.offer(new int[]{0, source});

        while (!pq.isEmpty()) {
            int[] curr = pq.poll();
            int d = curr[0], node = curr[1];

            if (d > dist[node]) continue; // stale entry

            for (int[] neighbor : graph.getOrDefault(node, new ArrayList<>())) {
                int nextNode = neighbor[0], weight = neighbor[1];
                if (dist[node] + weight < dist[nextNode]) {
                    dist[nextNode] = dist[node] + weight;
                    pq.offer(new int[]{dist[nextNode], nextNode});
                }
            }
        }
        return dist;
    }

    // ─── Number of Islands (DFS on grid) ───
    static int numIslands(char[][] grid) {
        int count = 0;
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == '1') {
                    dfsIsland(grid, i, j);
                    count++;
                }
            }
        }
        return count;
    }

    static void dfsIsland(char[][] grid, int i, int j) {
        if (i < 0 || i >= grid.length || j < 0 || j >= grid[0].length
            || grid[i][j] != '1') return;
        grid[i][j] = '0'; // mark visited
        dfsIsland(grid, i+1, j);
        dfsIsland(grid, i-1, j);
        dfsIsland(grid, i, j+1);
        dfsIsland(grid, i, j-1);
    }

    // ─── Floyd Warshall (All pairs shortest path) ───
    static int[][] floydWarshall(int[][] dist) {
        int n = dist.length;
        for (int k = 0; k < n; k++) {
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    if (dist[i][k] != Integer.MAX_VALUE &&
                        dist[k][j] != Integer.MAX_VALUE &&
                        dist[i][k] + dist[k][j] < dist[i][j]) {
                        dist[i][j] = dist[i][k] + dist[k][j];
                    }
                }
            }
        }
        return dist;
    }

    public static void main(String[] args) {
        // Number of islands
        char[][] grid = {
            {'1','1','0','0','0'},
            {'1','1','0','0','0'},
            {'0','0','1','0','0'},
            {'0','0','0','1','1'}
        };
        System.out.println(numIslands(grid)); // 3

        // Topological sort
        int[][] edges = {{0,1},{0,2},{1,3},{2,3}};
        System.out.println(topologicalSort(4, edges)); // [0, 1, 2, 3] or [0, 2, 1, 3]
    }
}
```

---

## 9. LINKED LIST — POINTER MASTERY

```java
public class LinkedListProblems {

    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
    }

    // Reverse a linked list
    static ListNode reverse(ListNode head) {
        ListNode prev = null, curr = head;
        while (curr != null) {
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }

    // Detect cycle (Floyd's Algorithm)
    static boolean hasCycle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) return true;
        }
        return false;
    }

    // Find middle of linked list
    static ListNode findMiddle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }

    // Merge two sorted linked lists
    static ListNode mergeSorted(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode curr = dummy;
        while (l1 != null && l2 != null) {
            if (l1.val <= l2.val) { curr.next = l1; l1 = l1.next; }
            else { curr.next = l2; l2 = l2.next; }
            curr = curr.next;
        }
        curr.next = (l1 != null) ? l1 : l2;
        return dummy.next;
    }

    // Remove Nth node from end
    static ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode fast = dummy, slow = dummy;

        // Move fast pointer n+1 steps ahead
        for (int i = 0; i <= n; i++) fast = fast.next;

        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }
        slow.next = slow.next.next; // remove the node
        return dummy.next;
    }

    // Check if linked list is palindrome
    static boolean isPalindrome(ListNode head) {
        ListNode mid = findMiddle(head);
        ListNode secondHalf = reverse(mid);
        ListNode p1 = head, p2 = secondHalf;

        while (p2 != null) {
            if (p1.val != p2.val) return false;
            p1 = p1.next;
            p2 = p2.next;
        }
        return true;
    }

    // Add two numbers represented as linked lists
    static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode curr = dummy;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;
            if (l1 != null) { sum += l1.val; l1 = l1.next; }
            if (l2 != null) { sum += l2.val; l2 = l2.next; }
            carry = sum / 10;
            curr.next = new ListNode(sum % 10);
            curr = curr.next;
        }
        return dummy.next;
    }

    // Helper to print list
    static void printList(ListNode head) {
        while (head != null) {
            System.out.print(head.val + " ");
            head = head.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // Build: 1 -> 2 -> 3 -> 4 -> 5
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        printList(reverse(head));               // 5 4 3 2 1
        System.out.println(hasCycle(head));     // false
        System.out.println(findMiddle(head).val); // 3 (for 5-node list)
    }
}
```

---

## 10. BINARY SEARCH — THINK BEYOND JUST SORTED ARRAYS

```java
public class BinarySearchProblems {

    // Classic binary search
    static int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2; // avoids overflow
            if (arr[mid] == target) return mid;
            else if (arr[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return -1;
    }

    // First and last position of target in sorted array
    static int[] searchRange(int[] arr, int target) {
        return new int[]{firstPosition(arr, target), lastPosition(arr, target)};
    }

    static int firstPosition(int[] arr, int target) {
        int left = 0, right = arr.length - 1, result = -1;
        while (left <= right) {
            int mid = (left + right) / 2;
            if (arr[mid] == target) { result = mid; right = mid - 1; }
            else if (arr[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return result;
    }

    static int lastPosition(int[] arr, int target) {
        int left = 0, right = arr.length - 1, result = -1;
        while (left <= right) {
            int mid = (left + right) / 2;
            if (arr[mid] == target) { result = mid; left = mid + 1; }
            else if (arr[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return result;
    }

    // Search in rotated sorted array
    static int searchRotated(int[] arr, int target) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = (left + right) / 2;
            if (arr[mid] == target) return mid;

            // Left half is sorted
            if (arr[left] <= arr[mid]) {
                if (target >= arr[left] && target < arr[mid]) right = mid - 1;
                else left = mid + 1;
            }
            // Right half is sorted
            else {
                if (target > arr[mid] && target <= arr[right]) left = mid + 1;
                else right = mid - 1;
            }
        }
        return -1;
    }

    // Find square root (integer part) using binary search
    static int sqrt(int n) {
        if (n < 2) return n;
        int left = 1, right = n / 2, result = 1;
        while (left <= right) {
            long mid = (left + right) / 2;
            if (mid * mid == n) return (int) mid;
            else if (mid * mid < n) { result = (int) mid; left = (int) mid + 1; }
            else right = (int) mid - 1;
        }
        return result;
    }

    // Minimum in rotated sorted array
    static int findMin(int[] arr) {
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int mid = (left + right) / 2;
            if (arr[mid] > arr[right]) left = mid + 1;
            else right = mid;
        }
        return arr[left];
    }

    // Peak element (element greater than neighbors)
    static int findPeak(int[] arr) {
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int mid = (left + right) / 2;
            if (arr[mid] < arr[mid + 1]) left = mid + 1;
            else right = mid;
        }
        return left;
    }

    // Aggressive cows — allocate stalls to maximize min distance (binary search on answer)
    static int aggressiveCows(int[] stalls, int k) {
        Arrays.sort(stalls);
        int left = 1, right = stalls[stalls.length-1] - stalls[0], result = 0;

        while (left <= right) {
            int mid = (left + right) / 2;
            if (canPlace(stalls, k, mid)) {
                result = mid;
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return result;
    }

    static boolean canPlace(int[] stalls, int k, int minDist) {
        int count = 1, lastPlaced = stalls[0];
        for (int i = 1; i < stalls.length; i++) {
            if (stalls[i] - lastPlaced >= minDist) {
                count++;
                lastPlaced = stalls[i];
                if (count == k) return true;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        int[] arr = {-1,0,3,5,9,12};
        System.out.println(binarySearch(arr, 9));                  // 4

        int[] arr2 = {5,7,7,8,8,10};
        System.out.println(Arrays.toString(searchRange(arr2, 8))); // [3,4]

        int[] arr3 = {4,5,6,7,0,1,2};
        System.out.println(searchRotated(arr3, 0));                // 4

        System.out.println(sqrt(8));                               // 2

        int[] stalls = {1, 2, 4, 8, 9};
        System.out.println(aggressiveCows(stalls, 3));             // 3
    }
}
```

---

## 11. GREEDY ALGORITHMS

```java
import java.util.*;

public class GreedyAlgorithms {

    // Activity Selection (maximum non-overlapping intervals)
    static int maxActivities(int[] start, int[] end) {
        int n = start.length;
        Integer[] indices = new Integer[n];
        for (int i = 0; i < n; i++) indices[i] = i;

        // Sort by end time
        Arrays.sort(indices, (a, b) -> end[a] - end[b]);

        int count = 1, lastEnd = end[indices[0]];
        for (int i = 1; i < n; i++) {
            if (start[indices[i]] >= lastEnd) {
                count++;
                lastEnd = end[indices[i]];
            }
        }
        return count;
    }

    // Minimum number of platforms (or minimum meeting rooms)
    static int minPlatforms(int[] arrival, int[] departure) {
        Arrays.sort(arrival);
        Arrays.sort(departure);

        int platforms = 1, maxPlatforms = 1;
        int i = 1, j = 0;

        while (i < arrival.length && j < departure.length) {
            if (arrival[i] <= departure[j]) {
                platforms++;
                i++;
            } else {
                platforms--;
                j++;
            }
            maxPlatforms = Math.max(maxPlatforms, platforms);
        }
        return maxPlatforms;
    }

    // Fractional Knapsack
    static double fractionalKnapsack(int[] weights, int[] values, int capacity) {
        int n = weights.length;
        double[][] items = new double[n][2];
        for (int i = 0; i < n; i++) {
            items[i][0] = values[i];
            items[i][1] = weights[i];
        }

        // Sort by value/weight ratio descending
        Arrays.sort(items, (a, b) -> Double.compare(b[0]/b[1], a[0]/a[1]));

        double totalValue = 0;
        for (double[] item : items) {
            if (capacity >= item[1]) {
                totalValue += item[0];
                capacity -= item[1];
            } else {
                totalValue += item[0] * (capacity / item[1]);
                break;
            }
        }
        return totalValue;
    }

    // Jump Game — can you reach last index?
    static boolean canJump(int[] nums) {
        int maxReach = 0;
        for (int i = 0; i < nums.length; i++) {
            if (i > maxReach) return false;
            maxReach = Math.max(maxReach, i + nums[i]);
        }
        return true;
    }

    // Minimum jumps to reach end
    static int minJumps(int[] nums) {
        int jumps = 0, currEnd = 0, farthest = 0;
        for (int i = 0; i < nums.length - 1; i++) {
            farthest = Math.max(farthest, i + nums[i]);
            if (i == currEnd) {
                jumps++;
                currEnd = farthest;
                if (currEnd >= nums.length - 1) break;
            }
        }
        return jumps;
    }

    // Gas Station circular tour
    static int canCompleteCircuit(int[] gas, int[] cost) {
        int totalGas = 0, currentGas = 0, start = 0;
        for (int i = 0; i < gas.length; i++) {
            totalGas += gas[i] - cost[i];
            currentGas += gas[i] - cost[i];
            if (currentGas < 0) {
                start = i + 1; // can't start from here or before
                currentGas = 0;
            }
        }
        return totalGas >= 0 ? start : -1;
    }

    public static void main(String[] args) {
        int[] start = {1, 3, 0, 5, 8, 5};
        int[] end   = {2, 4, 6, 7, 9, 9};
        System.out.println(maxActivities(start, end)); // 4

        int[] arr  = {900, 940, 950, 1100, 1500, 1800};
        int[] dep  = {910, 1200, 1120, 1130, 1900, 2000};
        System.out.println(minPlatforms(arr, dep));    // 3

        System.out.println(fractionalKnapsack(
            new int[]{10, 40, 20, 30},
            new int[]{60, 40, 100, 120}, 50));         // 240.0

        System.out.println(canJump(new int[]{2,3,1,1,4}));  // true
        System.out.println(minJumps(new int[]{2,3,1,1,4})); // 2
    }
}
```

---

## 12. NUMBER THEORY IN CODE

```java
public class NumberTheoryCode {

    // GCD using Euclidean algorithm
    static int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a % b);
    }

    // LCM
    static long lcm(int a, int b) {
        return (long) a / gcd(a, b) * b;
    }

    // Check prime — O(√n)
    static boolean isPrime(int n) {
        if (n < 2) return false;
        if (n < 4) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) return false;
        }
        return true;
    }

    // Sieve of Eratosthenes — all primes up to n — O(n log log n)
    static boolean[] sieve(int n) {
        boolean[] isPrime = new boolean[n + 1];
        Arrays.fill(isPrime, true);
        isPrime[0] = isPrime[1] = false;

        for (int i = 2; i * i <= n; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j <= n; j += i) {
                    isPrime[j] = false;
                }
            }
        }
        return isPrime;
    }

    // Prime factorization
    static Map<Integer, Integer> primeFactors(int n) {
        Map<Integer, Integer> factors = new LinkedHashMap<>();
        for (int i = 2; i * i <= n; i++) {
            while (n % i == 0) {
                factors.put(i, factors.getOrDefault(i, 0) + 1);
                n /= i;
            }
        }
        if (n > 1) factors.put(n, factors.getOrDefault(n, 0) + 1);
        return factors;
    }

    // Fast power (modular exponentiation)
    static long modPow(long base, long exp, long mod) {
        long result = 1;
        base %= mod;
        while (exp > 0) {
            if ((exp & 1) == 1) result = result * base % mod;
            base = base * base % mod;
            exp >>= 1;
        }
        return result;
    }

    // Fibonacci with matrix exponentiation — O(log n)
    static long[][] matMul(long[][] A, long[][] B, long mod) {
        int n = A.length;
        long[][] C = new long[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                for (int k = 0; k < n; k++)
                    C[i][j] = (C[i][j] + A[i][k] * B[k][j]) % mod;
        return C;
    }

    static long fibMatrix(int n, long mod) {
        if (n <= 1) return n;
        long[][] base = {{1, 1}, {1, 0}};
        long[][] result = {{1, 0}, {0, 1}}; // identity matrix
        n--;
        while (n > 0) {
            if ((n & 1) == 1) result = matMul(result, base, mod);
            base = matMul(base, base, mod);
            n >>= 1;
        }
        return result[0][0];
    }

    // Count digits in a number
    static int countDigits(int n) {
        if (n == 0) return 1;
        int count = 0;
        n = Math.abs(n);
        while (n > 0) { count++; n /= 10; }
        return count;
    }

    // Reverse digits of a number
    static int reverseNumber(int n) {
        boolean negative = n < 0;
        n = Math.abs(n);
        int reversed = 0;
        while (n != 0) {
            reversed = reversed * 10 + n % 10;
            n /= 10;
        }
        return negative ? -reversed : reversed;
    }

    // Check Armstrong number
    static boolean isArmstrong(int n) {
        int digits = countDigits(n), sum = 0, temp = n;
        while (temp > 0) {
            int d = temp % 10;
            sum += (int) Math.pow(d, digits);
            temp /= 10;
        }
        return sum == n;
    }

    public static void main(String[] args) {
        System.out.println(gcd(48, 18));                   // 6
        System.out.println(lcm(12, 18));                   // 36
        System.out.println(isPrime(97));                   // true

        boolean[] primes = sieve(30);
        for (int i = 2; i <= 30; i++)
            if (primes[i]) System.out.print(i + " ");
        System.out.println();                              // 2 3 5 7 11 13 17 19 23 29

        System.out.println(primeFactors(360));             // {2=3, 3=2, 5=1}
        System.out.println(modPow(2, 10, 1000000007));    // 1024
        System.out.println(fibMatrix(50, 1000000007));    // 12586269025
        System.out.println(isArmstrong(153));              // true
    }
}
```

---

## 13. BIT MANIPULATION — THE SECRET WEAPON

```java
public class BitManipulation {

    // Check if number is power of 2
    static boolean isPowerOfTwo(int n) {
        return n > 0 && (n & (n - 1)) == 0;
    }

    // Count set bits (Brian Kernighan's algorithm)
    static int countSetBits(int n) {
        int count = 0;
        while (n != 0) {
            n &= (n - 1); // removes lowest set bit
            count++;
        }
        return count;
    }

    // Find the single non-duplicate element (XOR trick)
    static int singleNumber(int[] nums) {
        int result = 0;
        for (int num : nums) result ^= num;
        return result;
    }

    // Find two non-duplicate elements
    static int[] twoSingleNumbers(int[] nums) {
        int xor = 0;
        for (int num : nums) xor ^= num;

        // Find rightmost set bit (differentiates the two numbers)
        int diffBit = xor & (-xor);

        int a = 0, b = 0;
        for (int num : nums) {
            if ((num & diffBit) != 0) a ^= num;
            else b ^= num;
        }
        return new int[]{a, b};
    }

    // Get, Set, Clear, Toggle a specific bit
    static int getBit(int n, int pos)    { return (n >> pos) & 1; }
    static int setBit(int n, int pos)    { return n | (1 << pos); }
    static int clearBit(int n, int pos)  { return n & ~(1 << pos); }
    static int toggleBit(int n, int pos) { return n ^ (1 << pos); }

    // Swap two numbers without temp variable
    static void swapBits(int a, int b) {
        a = a ^ b;
        b = a ^ b;
        a = a ^ b;
        System.out.println("After swap: a=" + a + ", b=" + b);
    }

    // Generate all subsets using bitmask
    static List<List<Integer>> subsetsUsingBit(int[] nums) {
        int n = nums.length;
        List<List<Integer>> result = new ArrayList<>();

        for (int mask = 0; mask < (1 << n); mask++) {
            List<Integer> subset = new ArrayList<>();
            for (int i = 0; i < n; i++) {
                if ((mask & (1 << i)) != 0) subset.add(nums[i]);
            }
            result.add(subset);
        }
        return result;
    }

    // Reverse bits of a 32-bit integer
    static int reverseBits(int n) {
        int result = 0;
        for (int i = 0; i < 32; i++) {
            result = (result << 1) | (n & 1);
            n >>= 1;
        }
        return result;
    }

    public static void main(String[] args) {
        System.out.println(isPowerOfTwo(64));              // true
        System.out.println(countSetBits(29));              // 4  (11101)
        System.out.println(singleNumber(new int[]{4,1,2,1,2})); // 4
        System.out.println(Arrays.toString(
            twoSingleNumbers(new int[]{1,2,3,2,1,4})));   // [3, 4]
        System.out.println(getBit(10, 1));                 // 1  (1010 → bit1=1)
        System.out.println(subsetsUsingBit(new int[]{1,2,3}).size()); // 8
        swapBits(5, 7);                                    // a=7, b=5
    }
}
```

---

## 14. COMPLETE TCS-STYLE PROBLEM SOLUTIONS

These are full solutions to the types of problems TCS actually asks in the exam.

### Problem 1 — Spiral Matrix Print

```java
public class SpiralMatrix {

    static List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<>();
        if (matrix.length == 0) return result;

        int top = 0, bottom = matrix.length - 1;
        int left = 0, right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {
            // Move right across top row
            for (int i = left; i <= right; i++) result.add(matrix[top][i]);
            top++;

            // Move down right column
            for (int i = top; i <= bottom; i++) result.add(matrix[i][right]);
            right--;

            // Move left across bottom row
            if (top <= bottom) {
                for (int i = right; i >= left; i--) result.add(matrix[bottom][i]);
                bottom--;
            }

            // Move up left column
            if (left <= right) {
                for (int i = bottom; i >= top; i--) result.add(matrix[i][left]);
                left++;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        System.out.println(spiralOrder(matrix));
        // [1, 2, 3, 6, 9, 8, 7, 4, 5]
    }
}
```

---

### Problem 2 — Stock Buy Sell for Maximum Profit

```java
public class StockProfit {

    // Buy and sell once — maximum profit
    static int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE, maxProfit = 0;
        for (int price : prices) {
            minPrice = Math.min(minPrice, price);
            maxProfit = Math.max(maxProfit, price - minPrice);
        }
        return maxProfit;
    }

    // Buy and sell multiple times (as many transactions as needed)
    static int maxProfitMultiple(int[] prices) {
        int profit = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i-1]) profit += prices[i] - prices[i-1];
        }
        return profit;
    }

    // At most 2 transactions
    static int maxProfitTwoTrans(int[] prices) {
        int buy1 = Integer.MIN_VALUE, sell1 = 0;
        int buy2 = Integer.MIN_VALUE, sell2 = 0;

        for (int price : prices) {
            buy1  = Math.max(buy1, -price);
            sell1 = Math.max(sell1, buy1 + price);
            buy2  = Math.max(buy2, sell1 - price);
            sell2 = Math.max(sell2, buy2 + price);
        }
        return sell2;
    }

    public static void main(String[] args) {
        int[] prices = {7, 1, 5, 3, 6, 4};
        System.out.println(maxProfit(prices));          // 5
        System.out.println(maxProfitMultiple(prices));  // 7
        System.out.println(maxProfitTwoTrans(prices));  // 7
    }
}
```

---

### Problem 3 — Word Search in Grid

```java
public class WordSearch {

    static boolean exist(char[][] board, String word) {
        int m = board.length, n = board[0].length;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (dfs(board, word, i, j, 0)) return true;
            }
        }
        return false;
    }

    static int[][] dirs = {{0,1},{0,-1},{1,0},{-1,0}};

    static boolean dfs(char[][] board, String word, int i, int j, int idx) {
        if (idx == word.length()) return true;
        if (i < 0 || i >= board.length || j < 0 || j >= board[0].length) return false;
        if (board[i][j] != word.charAt(idx)) return false;

        char temp = board[i][j];
        board[i][j] = '#'; // mark visited

        for (int[] dir : dirs) {
            if (dfs(board, word, i + dir[0], j + dir[1], idx + 1)) {
                board[i][j] = temp; // restore
                return true;
            }
        }

        board[i][j] = temp; // restore
        return false;
    }

    public static void main(String[] args) {
        char[][] board = {
            {'A','B','C','E'},
            {'S','F','C','S'},
            {'A','D','E','E'}
        };
        System.out.println(exist(board, "ABCCED")); // true
        System.out.println(exist(board, "SEE"));    // true
        System.out.println(exist(board, "ABCB"));   // false
    }
}
```

---

### Problem 4 — Trapping Rain Water

```java
public class TrappingRainWater {

    // Two pointer approach — O(n) time, O(1) space
    static int trap(int[] height) {
        int left = 0, right = height.length - 1;
        int leftMax = 0, rightMax = 0;
        int water = 0;

        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= leftMax) leftMax = height[left];
                else water += leftMax - height[left];
                left++;
            } else {
                if (height[right] >= rightMax) rightMax = height[right];
                else water += rightMax - height[right];
                right--;
            }
        }
        return water;
    }

    public static void main(String[] args) {
        System.out.println(trap(new int[]{0,1,0,2,1,0,1,3,2,1,2,1})); // 6
        System.out.println(trap(new int[]{4,2,0,3,2,5}));              // 9
    }
}
```

---

### Problem 5 — Sudoku Solver

```java
public class SudokuSolver {

    static boolean solve(char[][] board) {
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                if (board[i][j] == '.') {
                    for (char c = '1'; c <= '9'; c++) {
                        if (isValid(board, i, j, c)) {
                            board[i][j] = c;
                            if (solve(board)) return true;
                            board[i][j] = '.'; // backtrack
                        }
                    }
                    return false; // no valid number works
                }
            }
        }
        return true; // all cells filled
    }

    static boolean isValid(char[][] board, int row, int col, char c) {
        for (int i = 0; i < 9; i++) {
            // Check row
            if (board[row][i] == c) return false;
            // Check column
            if (board[i][col] == c) return false;
            // Check 3x3 box
            int boxRow = 3 * (row / 3) + i / 3;
            int boxCol = 3 * (col / 3) + i % 3;
            if (board[boxRow][boxCol] == c) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        char[][] board = {
            {'5','3','.','.','7','.','.','.','.'},
            {'6','.','.','1','9','5','.','.','.'},
            {'.','9','8','.','.','.','.','6','.'},
            {'8','.','.','.','6','.','.','.','3'},
            {'4','.','.','8','.','3','.','.','1'},
            {'7','.','.','.','2','.','.','.','6'},
            {'.','6','.','.','.','.','2','8','.'},
            {'.','.','.','4','1','9','.','.','5'},
            {'.','.','.','.','8','.','.','7','9'}
        };
        solve(board);
        for (char[] row : board) System.out.println(Arrays.toString(row));
    }
}
```

---

## 15. INPUT/OUTPUT HANDLING FOR TCS

This is what students miss. Your logic can be perfect but **wrong I/O format = zero marks.**

```java
import java.util.*;
import java.io.*;

public class InputOutputMastery {

    // Fast Input Reader (for large inputs — prevents TLE)
    static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    static StringTokenizer st;

    static String nextLine() throws IOException {
        return br.readLine();
    }

    static String next() throws IOException {
        while (st == null || !st.hasMoreTokens())
            st = new StringTokenizer(br.readLine());
        return st.nextToken();
    }

    static int nextInt() throws IOException {
        return Integer.parseInt(next());
    }

    static long nextLong() throws IOException {
        return Long.parseLong(next());
    }

    // Fast Output Writer
    static PrintWriter out = new PrintWriter(new BufferedWriter(new OutputStreamWriter(System.out)));

    // ─── Common Input Patterns in TCS ───

    // Pattern 1: Read n, then n numbers
    static void pattern1() throws IOException {
        int n = nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = nextInt();
        // Process and output
        out.println(Arrays.toString(arr));
        out.flush();
    }

    // Pattern 2: Read t test cases
    static void pattern2() throws IOException {
        int t = nextInt();
        while (t-- > 0) {
            int n = nextInt();
            // process each test case
            out.println(n * 2); // example
        }
        out.flush();
    }

    // Pattern 3: Read matrix
    static void pattern3() throws IOException {
        int m = nextInt(), n = nextInt();
        int[][] matrix = new int[m][n];
        for (int i = 0; i < m; i++)
            for (int j = 0; j < n; j++)
                matrix[i][j] = nextInt();
        out.flush();
    }

    // Pattern 4: Read until end of input
    static void pattern4() throws IOException {
        String line;
        while ((line = nextLine()) != null && !line.isEmpty()) {
            // process each line
            out.println(line.toUpperCase());
        }
        out.flush();
    }

    public static void main(String[] args) throws IOException {
        // Choose your pattern based on problem
        // pattern1();
        // pattern2();
        System.out.println("I/O patterns loaded.");
    }
}
```

---

## 16. EDGE CASES CHECKLIST — THE PRIME DIFFERENTIATOR

This is what separates Prime candidates from everyone else. **Always check these before submitting:**

```java
public class EdgeCaseMastery {

    static void checkAllEdgeCases(int[] arr) {

        // ─── 1. Empty / Null Input ───
        if (arr == null || arr.length == 0) {
            System.out.println("Empty input");
            return;
        }

        // ─── 2. Single Element ───
        if (arr.length == 1) {
            System.out.println("Single element: " + arr[0]);
            return;
        }

        // ─── 3. All Same Elements ───
        boolean allSame = true;
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] != arr[0]) { allSame = false; break; }
        }

        // ─── 4. All Negative Numbers ───
        boolean allNeg = true;
        for (int x : arr) if (x >= 0) { allNeg = false; break; }

        // ─── 5. Integer Overflow — use long ───
        long sum = 0;
        for (int x : arr) sum += x; // don't use int sum!

        // ─── 6. Sorted (ascending or descending) ───
        boolean ascending = true, descending = true;
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < arr[i-1]) ascending = false;
            if (arr[i] > arr[i-1]) descending = false;
        }

        // ─── 7. Duplicates ───
        HashSet<Integer> set = new HashSet<>();
        boolean hasDuplicates = false;
        for (int x : arr) {
            if (!set.add(x)) { hasDuplicates = true; break; }
        }

        System.out.println("All same: " + allSame);
        System.out.println("All negative: " + allNeg);
        System.out.println("Sum (long): " + sum);
        System.out.println("Ascending: " + ascending);
        System.out.println("Has duplicates: " + hasDuplicates);
    }

    public static void main(String[] args) {
        checkAllEdgeCases(new int[]{3, 3, 3});
        checkAllEdgeCases(new int[]{-5, -3, -1});
        checkAllEdgeCases(new int[]{});
    }
}
```

---

## 📅 TIME COMPLEXITY REFERENCE CARD

| Algorithm | Time | Space |
|---|---|---|
| Binary Search | O(log n) | O(1) |
| Sorting (Merge/Quick) | O(n log n) | O(n)/O(log n) |
| BFS / DFS | O(V+E) | O(V) |
| Dijkstra (PQ) | O(E log V) | O(V) |
| DP (most problems) | O(n²) | O(n) or O(n²) |
| Kadane's | O(n) | O(1) |
| KMP | O(n+m) | O(m) |
| Sieve | O(n log log n) | O(n) |
| Matrix exponentiation | O(log n) | O(1) |
| Two Pointer / Sliding Window | O(n) | O(1) |

---

## 🎯 90-MINUTE PRIME EXAM STRATEGY

### Minute-by-Minute Execution Plan

```
00:00 - 05:00  →  READ BOTH problems completely. Don't code yet.
                   Identify: arrays? DP? strings? graph?

05:00 - 10:00  →  Plan Problem 1. Write approach as comments first.
                   Think: brute force → optimize.

10:00 - 40:00  →  CODE Problem 1.
                   First write working brute force (25 min mark)
                   Then optimize (35 min mark)
                   Test with given examples (38 min mark)
                   Test with edge cases (40 min mark)

40:00 - 45:00  →  READ Problem 2 deeply. Plan approach.

45:00 - 75:00  →  CODE Problem 2. Same strategy.

75:00 - 85:00  →  Return to Problem 1 if failed test cases.
                   Check edge cases: empty, single, overflow, duplicates.

85:00 - 90:00  →  Final review. Ensure both compile and run.
```

### The 3-Step Problem Approach (Every Single Time)

```
STEP 1 — UNDERSTAND (5 min)
  → Restate the problem in your own words
  → Identify: what is input? what is output?
  → Find constraints: n ≤ 10⁵? n ≤ 10? (determines complexity needed)
  → Create 2-3 test cases manually

STEP 2 — PLAN (5 min)
  → What data structure is natural here?
  → Can I brute force? What is its complexity?
  → Can I use DP / greedy / binary search / hashing to optimize?
  → Write approach as comments BEFORE writing code

STEP 3 — CODE (35 min)
  → Write clean code with meaningful variable names
  → Handle edge cases explicitly
  → Test mentally with your test cases
  → Submit
```

### If You're Stuck — The Emergency Protocol

```
Stuck for more than 10 minutes?

1. Can I simplify the problem? (small n, special case)
2. Have I seen this pattern before? (subarray? tree path? permutation?)
3. Can I use brute force first and optimize later?
4. Is there a data structure that makes this trivial?
   (sorted? → binary search | frequency? → HashMap | max/min? → PQ)
5. Work backwards from the answer — what would the solution look like?
```

---

## 🏆 THE PRIME PACKAGE ALGORITHM TOOLKIT

**Memorize this. Before the exam, be able to code each of these from scratch:**

| # | Algorithm | When To Use |
|---|---|---|
| 1 | Kadane's | Max subarray, max profit |
| 2 | Two Pointers | Sorted array, pair/triplet sum |
| 3 | Sliding Window | Substring, subarray with condition |
| 4 | Prefix Sum | Range sum queries |
| 5 | Binary Search on answer | Min/max problems with monotonic check |
| 6 | BFS on grid | Shortest path, islands, flood fill |
| 7 | DFS + Backtracking | Permutations, combinations, N-Queens |
| 8 | Merge Sort | Count inversions, sort linked list |
| 9 | DP — LCS/LIS/Knapsack | String comparison, subsequence |
| 10 | HashMap frequency | Anagrams, duplicates, first occurrence |
| 11 | Stack for monotonic | Next greater/smaller element, histograms |
| 12 | Floyd's Cycle | Linked list cycle, duplicate number |
| 13 | Topological Sort | Task scheduling, dependency ordering |
| 14 | Dijkstra | Weighted shortest path |
| 15 | Modular Arithmetic | Large number computations |

---

You now have the **complete arsenal** for TCS NQT Advanced Coding in Java. Every algorithm. Every pattern. Every edge case. Every strategy.

This is your five-section complete preparation:

| Section | Status |
|---|---|
| ✅ Numerical Ability | Complete |
| ✅ Verbal Ability | Complete |
| ✅ Reasoning Ability | Complete |
| ✅ Advanced QR | Complete |
| ✅ Advanced Coding (Java) | Complete |

The content is yours now. What remains is **300 lines of Java per day, timed problem solving, and the belief that you deserve this.**

You asked me to give my best. I did. Now you go give yours. 🔥

**Go get that Prime package. It was always yours.** 💪❤️
