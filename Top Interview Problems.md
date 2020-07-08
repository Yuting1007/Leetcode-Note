


> Written with [StackEdit](https://stackedit.io/).
> # Top Interview Problems (Leetcode Label)
### 1.  Two Sum
This one is easy, use hashmap
res will be [i, m[target - nums[i]]
Therefore, if we have found the key with (target - nums[i]) in the map, push back into res, if not found, initiate m[i] = i

### 200.  number of islands
This is a dfs+visited_memo
in the main function, we use dfs to turn all visited island point to visited=true and count by iteration
in the dfs function, we follow the (stop, action, recursion) steps to turn all adjacent island points's visited_memo into "visited"

### 2.  add two numbers
error : access null pointer => the input is null, no input->next pointer
This is excellent example for manage null pointer and unequal length linked lists.
Use 0 to represent the value of null pointer

### 42.  trapping rain water
array
If we encounter to a water trapping problems, considering two points

 1. the height of fences in the left and right directions are determined
    by the max length; 
 2. The capability of trapping water is determined by
    the shortest fences.
Use a 1D vector to record the fence lengths in both directions.

### 5. Longest Palindromic Substring

When talking about palindromic, use two pointers and consider odd and even number of string

  

### 20. Valid Parentheses

This is a matching problems, use stack

  

### 3. Longest Substring Without Repeating Characters

This one is ask about the length not the substring. Therefore, we could consider use a pointer to indicate a special meaning site.

We create a pointer called lastRepeatedPos indicating the position of last repeated character(no matter what it is)

update it if finding a repeat (use hashmap)

  

### 23. Merge k Sorted Lists

This is question based on merge two sorted list

we use divide and conquer to handle k linked list

For example, 6 lists

{0, 3}, {1, 5}, {2, 6}

Here has a interesting pair matching management
[pic here ]
k is the #linked list after pair merge

### 4. Median of Two Sorted Arrays ???

### 10. Regular Expression Matching
The tricky part of this problem is that 
`'*' Matches zero or more of the preceding element.`
This means, what coming after shall the same properties as the origin input => recursion

  

### 30. Substring with Concatenation of All Words

The keyword for this question is all word share the same length.

which means we could use substr() to slice the word from string

The iteration could starts from 0 ends at (int)s.size() - n * len

**(int) here is needed

use a hashmap to count the word in words

Since all words in words need to appear once, the way to grab substring is interesting.

two case for break:

a. word not in words

b. too many counts

also use a new hashmap to record the count

  

if(j == n) res.push_back(i)

### 15. 3Sum

This is a classic BS question.

one pointer for iteration + 2Sum

The tricky part of this question is remove duplicates

in the step of iteration

in the step of two sum

  

### 238. Product of Array Except Self

This is also a classic question about dp

When we encounter with "except" questions, we could consider left and right two directions

  

### 56. Merge Intervals

This is a interval questions. Basically, it is an implementation of mind


  

### 53. Maximum Subarray

Greedy- Pick the  locally  optimal move at each step, and that will lead to the  globally  optimal solution.

=> optimization problems, maximum or minimum questions

we need to iterate all input, update locally optimal, update globally optimal

after the iteration we come up with the result

sum = sum(maximal constrain) = max(curr_input, currMaxSum + curr_input)

(maximal constrain)

  

### 121. Best Time to Buy and Sell Stock

profit = sale_price (current input) - buy_price(minimal constrain)

(maximal constrain)


### 32. Longest Valid Parentheses

This questions we only consider one kind of parentheses and we also talk about valid => stack

And for "length" problem, use a start pointer

( => enstack

) => stack.empty ? yes => start invalid, move start

no => offset one "("

=> stack empty ? yes => [start, curr] is valid

no => only part of "(" is offset, (stack.top(), curr] is valid

  

### 37. Sudoku Solver

dfs + backtracking

This question is kinda about asking a "all solution" =>dfs

dfs template:

main function => iteration, in this case, we only start from (0, 0) since only one solution is valid

dfs => stop, action, recursion

  

In this case, the dfs function:

1.  stop
    

i >= 9 (iteration over, return true)

2.  action
    

the step is 1-9 characters, if valid, move to the next iteration => if the next iteration is valid, return true, over

=> if not, back to empty, move another step

3.  recursion
    

j >= 9 (row iteration over, move to the next row)

The cell is not empty (move to the next recursion)

  

This question does not have a clear separation between action and recursion. But it following the "mind algorithm"

start from the first cell, if not empty move to the next, if is empty, try 1-9, try the next cell based on this one, if valid => over; if not => try another number

### [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)
Since asking about all possibilities, we could consider dfs.
I think this is a resursion solution. Use left and right pointers to indicate how many parantheses avaliable. 
1. stop
no left and right left => push in res
2. action, recursion 
left > 0 => '(' push in curr
left < right => ') push in curr

### [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
This is a super classic linked list questions!!!
use prev, curr two pointers; inside the while loop, we store the next node, then turn over the next pointer and then move prev, curr pointers

### [41. First Missing Positive](https://leetcode.com/problems/first-missing-positive/)
I am kinda curious why this one is a *hard* :)
We could sort the list first.
Then find the index of first un-positive number.
the index is over OR nums[index] is greater than 1 => 1
start from the index iterating over, jump duplicates and find the first gap => nums[j] + 1

### [269. Alien Dictionary](https://leetcode.com/problems/alien-dictionary/)
**Directed Graph**
Similar Problems [210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
Logic: **BFS**
1. Use a 2D array to store all edges
	Initiate a 1D array saving the indegree
2. Use a queue for assisting, enqueue all 0 indegree nodes
3. inside while loop:
		grap the node from the queue front, pop 
		decrease the another node at the edge indegree by 1, if 0 enqueue
	
	The tricky part of this question is the way to construct graph. Usually, we use a 2D array, here a set of pairs is useful.
	Some associated in-built functions are: set<pair<char, char>> st, st.insert(make_pair(A, B)), first, second

### [297. Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)
A classic tree problem.
Recursion => preorder
Iteration => level travseral (need a queue for assistantship in both serialize and deserialize)
**istringstream** and **ostringstream**
in >> val  => read val from in
out << val => write val to out

### [322. Coin Change](https://leetcode.com/problems/coin-change/)
When we talk about the optimal solution, a dp is also a good choice (besides greedy algorithm)
dp = dfs + memo(similar functionality as dp vector)
dp[i] => the smallest number of coins to reach amout of i
Initiate it as vector<int> dp(amount+1, amount+1);
**dynamic transfer function:**
dp[i] = min(dp[i], dp[i - coins[j]] + 1);

### [139. Word Break](https://leetcode.com/problems/word-break/)
dp problems
dp[i] wether the substring [0, i) is valid
                **if(dp[j] && wordSet.count(s.substr(j, i-j))){
                    dp[i] = 1;**
 [0, i) is separated into [0, j) and [j, i), therefore, we need dp[j] and wordSet.count(s.str(j, i-j))
 The direction is backwards
 
### [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
A median diff but also classic one.
We need to specify the range that our nums[mid] fall;
after that, two candidate ranges will appear, we need to specify the range of our target falling.
有两个范围都满足条件
BS只能在sorted array中发挥作用 所以需要判断target落在那里
如果落在右边, 有两种情况比target大, 如果落在左边 有两种情况比target小
BS第一类 (<=; +1; -1)

### [54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)
**coordinate change in turn**
坐标变换数组
The direction is right, down , left and up; and this order appears in turns => %
When we hit the boarder or access to a visited point => change our direction. 

### [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)
A easy one
In order to avoid overflow, use long to store result;
inside the while loop of x != 0
res = 10* res + x % 10;
x /= 10;

### [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)
This problem could use a hashmap.
We can sort the strings to get a uniform key

### [11.  Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
A problem with trapping water => consider left and right
Two pointers
h = min(nums[left], nums[right])
Why do we move our poniter? => if nums[left] or nums[right] <= h
Or, if we explain in pain words, we move the one laggin behind
***similar question:***
[42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
This one is not asking about the most water but the total amout trapped.
As we always said, when talking about water, two directions are necessary.
we use dp to solve this question (I am thinking that if the current state somehow relies on the previous one, we could use dp)
```
        for(int i = 1; i < n; i++){
            left[i] = max(left[i-1], height[i-1]);
        }
        for(int j = n-2; j >= 0; j--){
            right[j] = max(right[j+1], height[j+1]);
        }

```
The left and right fences are determined by the max
But the water trapped in between is determined by min

### [253. Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)
This is a new approach for solving *interval questions*
1. We use two 1D vector for storing the start points and end points of each interval.
2. Then sort those two vectors
3. Set a pointer called *endpoint* indicating the current end index of meeting. Initiate it with 0
	`if (starts[i] < ends[endpos])` => `res++`
	when we start, the last one is not finished
	`else ` => `++endpos;`
	when we start, the last one is over, we can move to the next endpoint

### [76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
```
My thoughts:
Use a hashmap to record all indexes that each characters in taget, then find the shorest region (no idea about this part)
```
[video explaination](https://www.youtube.com/watch?v=eS6PZLjoaq8) from Back To Back SWE.
Ben really is my favoriate Youtuber!!!!!

BF => dulicate works analysis => improvement (two pointers)

### [138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)
This is a classic *random* problem.
We use a hashmap to bulid injection between nodes and copied nodes.
1. copy next pointers first and initiate the hashmap
2. copy the random pointers

###  [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
We may think about sort and find the kth largest element.
When talking about the sort, instead of using the in-bulit function.
1. **quick sort** + **bs**
Find a pivot, parition the rest into (smaller than pivot, larger than pivot) by swapping
swap the pivot and stopping pointer
2. **quick select**
3. **min-heap**
For the min-heap, the smallest element is at the top. Whenever we find the elements in the heap is larger than k, we pop from the heap.
```
priority_queue <int, vector<int>, greater<int>> gq;
```
### [17. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
For those combination questions => dfs+backtracking
The params needed in dfs usually follows:
```
void DFS(string digits, int index, string& curr, vector<string>& res, vector<string>& letter){}
```
or, if I put it as a more abstruct way,
```
void dfs(input, index(or degree), current_answer, result, avaiable_steps)
```
inside the dfs function, 
1. stop => usually when degree hits the boarder
2. increment => index+1
3. cursion => dfs(index+1)

### [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
```
You may assume that _nums1_ has enough space (size that is greater or equal to _m_ + _n_) to hold additional elements from _nums2_.
```
As the statement, we need to operate in the _nums1_.
And they way we handle sorting from blank. As the hint suggests, we use _nums1_ as the space we sort.
after  the pharase that `where(i >= 0 && j >= 0)`,
we need to consider the situations that only one is left.
In this case, we use _nums1_as the operation space, only consider the case that _nums2_ is not done.
**similar questions**
[21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

### [289. Game of Life](https://leetcode.com/problems/game-of-life/)
The tricky part of it question is that we need to keep a dynamic changing pattern. (kinda like we need to find the finish pharse of a changing pattern).
Here, we introduce a new topic called **state changer**, 
1. state 0 : dead -> dead
2. state 1 : live -> live
3. state 2 : live -> dead
4. state 3 : dead -> live
Then we take %2 for each state,
5. state 0, 2 -> dead
6. state 1, 3 -> live

Similar, 坐标变换数组在这里也是需要的~
For the first iteration, we keep count of state 1 and state 2
Then based on the count and state changer, change the state label.
For the second iteration, we take mod 2 to get the final result.

### [202. Happy Number](https://leetcode.com/problems/happy-number/)
we use hashset to record the numbers appearing in order to avoid loop
```
  while(n){
      sum += (n % 10) * (n % 10);
      n /= 10;
  }
  n = sum;
```

### [91. Decode Ways](https://leetcode.com/problems/decode-ways/)
dp, kinda like *climbing starts*
i will be able to coming from i-1 and i-2
`if s[i-1] == '0` => from i-1 is invalid, only from i-2 is possible
`"02"`

`if(i > 1 && (s[i-2] == '1' || (s[i-2] == '2' && s[i-1] <= '6')))` => from i-2 is valid
`"226" or "116"`
digits to be consider (i-2 => current and next; i-1 => current)

### [127. Word Ladder](https://leetcode.com/problems/word-ladder/)
A classic bfs question. 
bfs = queue + step
The tricky part of this question is that we need to record the steps we took and connect it with its associated path lenghth.
=> to avoid stepping back
`unordered_map<string, int> path`
The logic for BFS is
`intiate the queue with the starter, step all possible steps, if valid then enqueue`

### [46. Permutations](https://leetcode.com/problems/permutations/)
This is a classic dfs + backtracking problems. => **all possible solution**
In order to keep the record of visited, we need a 1D vector.
`dfs(input, index, visited, curr, res)`
`dfs => stop, action, increment`

### [79. Word Search](https://leetcode.com/problems/word-search/)
```
My thoughts: recursion: match current index + match the rest index => true
we need try every start point, and take all steps => backtracking + dfs => till here, the main function should in my mind
dfs + backtracking => stop(degree hit the requirement; hit the boarder, not match, visited), action(toggle visited state), increment(steps in four directions and increase the index)
```
### [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
It is kinda easy to think about use hashmap to record the cnt.
Therefore, we encount with **sort the hashmap based on value**.
We could use a priority queue, maxheap (by default)
```
priority_queue<pair<int, int>> q;
for(auto it : m){
    q.push({it.second, it.first});
}
```
In this case, the value will be the base to sort.

### [227. Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/)
A calssical application on stack.
```
algorithm:
if numbers => get the whole numbers and store in a variable called num
if options => (initiate as '+')
'+' st.push(num)
'-' st.push(-num)
'*" or '/' get the top element, push the outcome to stack

After iteration, add all elements in stack up to get the result.
```
I have tried rewirte this queston and found that, we need initialization (op = '+') to process the first num.

### [412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/)
Instead of if-else statement, we initialize the whole result vector with its value then rewrite those meeting the requirements.
```
 for(int i=2; i<n; i=i+3){result[i] = "Fizz";}
 for(int i=4; i<n; i=i+5){result[i] = "Buzz";}
 for(int i=14; i<n; i=i+15){result[i] = "FizzBuzz";}
```

### [124. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
When I first see this question, literally have no idea.
If this happens later, think about **recursion**.

```
class Solution {
public:
    int maxPathSum(TreeNode* root) {
        int res = INT_MIN;
        helper(root, res);
        return res;
    }
    int helper(TreeNode* node, int& res) {
        if (!node) return 0;
        int left = max(helper(node->left, res), 0);
        int right = max(helper(node->right, res), 0);
        res = max(res, left + right + node->val);
        return max(left, right) + node->val;
    }
};
```
This is a perfect example of updating result and the return value of helper function differs.
res => max(left) + max(right) + node->val
return value => max(left, right) + node->val

这就很适合有多条信息想从recusion 里面出来的情况

### [236. Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)
This is a classic tree problem.
We can use recursion here. We try to find LCA in the left subtree, in the right subtree. If null from both sides, the root is the result.

### [155. Min Stack](https://leetcode.com/problems/min-stack/)
I remembered the "queue & stack" block in the question list do have a lot this kind of questions. 
Like, using queue to implement stack, using stack to implement queue.

For this question, we could use two stacks. One for  normal order processing. The other for storing the minmum number in each step.
`if (s2.empty() || x <= s2.top()) s2.push(x);`

### [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
This is a BS question.
Two trends here, The first trend => smaller than target; the second trend => larger than target
Of course, we need to consider the boarder, if reach the boarder, return default setting result.

### [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/)
I do feel this one is with hint.
We could use a map to relect the projection between integer and roman.
Only two exceptions 4 and 9.
```
 if(i == s.size() - 1 || m[s[i]] >= m[s[i+1]]){
     res += m[s[i]];
 } else {
     res -= m[s[i]];
 }
```
### [8. String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/)
Tuantuan chance needed!

### [140. Word Break II](https://leetcode.com/problems/word-break-ii/)
Tuantuan chance needed!

### [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)
This is like the start point for dp :)!!
The tricky part for dp:
1. how much space you want, and how do you initiate them
2. The state transformation function

### [98. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)
The setting for the helper function is intersting.
BST:
1. BST for left and right childern
2. within the range
All these critira need to be covered in the helper function, via either the output, or the parameters

### [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)
kinda like the quick sort, using a pointer and swap; done by in-place.
Moving all non-zero numbers at the front `swap(nums[i], nums[leftNoZero]);`

### [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
Two pointers(left & right)
`(s[right] + 32 - 'a') % 32)`

### [239. Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
new data structure needed

### [240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)
I remembered I have watched a video about these kind of question (sorted in both row and col).
The way for solving this sort of question is that, we start at the right upper corner or left dottom corner, then BS

### [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)
题外话: 有时候string, array的问题 遇到什么最值 或者是 in-place解决的东西, 试试加上pointer with meaning
this is is pretty straight forward. Use the first word as a base, compare with all other word at the same place; increasing if matching, return if any of them not matching.

### [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
Defining uniqueness we use hashmap a lot.

### [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
**LIS**
Optimization =>
1. greedy algorithm
2. dp
3. special pointer
This one is greedy + dp
```
 for(int i = 0; i < n; i++){
     for(int j = 0; j < i; j++){
         if(nums[j] < nums[i]){
             dp[i] = max(dp[i], dp[j] + 1);//start from itself or enlarge other starter in front it
         }
     }
     res = max(res, dp[i]);
 }
```
dp is always like, using previous state to update the current one. While in this question, we are trying to find the largest previous state to update the current state. Thus, two loops are needed.

### [348. Design Tic-Tac-Toe](https://leetcode.com/problems/design-tic-tac-toe/)
**DESIGN CLASS**
[Notes](https://www.cnblogs.com/grandyang/p/5467118.html)
```
class TicTacToe {
public:
    /** Initialize your data structure here. */
    TicTacToe(int n): rows(n), cols(n), N(n), diag(0), rev_diag(0) {}

    int move(int row, int col, int player) {
        int add = player == 1 ? 1 : -1;
        rows[row] += add; 
        cols[col] += add;
        diag += (row == col ? add : 0);
        rev_diag += (row == N - col - 1 ? add : 0);
        return (abs(rows[row]) == N || abs(cols[col]) == N || abs(diag) == N || abs(rev_diag) == N) ? player : 0;
    }

private:
    vector<int> rows, cols;
    int diag, rev_diag, N;
};
```
I prefer this solution, use inverse number (offset).
如果之后遇到对阵的题目 可以思考offset.

### [50. Pow(x, n)](https://leetcode.com/problems/powx-n/)
这道题还有迭代的解法，让i初始化为n，然后看i是否是2的倍数，不是的话就让 res 乘以x。然后x乘以自己，i每次循环缩小一半，直到为0停止循环。最后看n的正负，如果为负，返回其倒数

### [152. Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
another optimization question => greedy, dp or special pointer!!
Use dp in this case, think about the negative and positive properties of numbers
```
 for(int i = 1; i < n; i++){
     maxDP[i] = max(max(maxDP[i-1]*nums[i], minDP[i-1]*nums[i]), nums[i]);
     minDP[i] = min(min(maxDP[i-1]*nums[i], minDP[i-1]*nums[i]), nums[i]);   
     res = max(maxDP[i], res);
 }
```
**contiguous sequence**
If encounter to this property, think about this: For each number, we have two options, including it (recursion) or not (abandon the previous one, start at the current point)

### [341. Flatten Nested List Iterator](https://leetcode.com/problems/flatten-nested-list-iterator/)
**DESIGN**
```
Private : the data structure (could be something for assisting or container)
Main function : initiate the data structre
```
It is asking for iteration.  We could as a stack to assist iteration.
每层都押入栈 nested在hasNext的时候压入

### [128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)
我目前的想法: 排序然后找 但是这样肯定会超时
解题的想法应该是: 先BF, big O, 然后分析inefficiency (也就是找找看有哪些重复工作), 在思考如何改进
[花花](https://www.youtube.com/watch?v=rc2QdQ7U78I)

### [204. Count Primes](https://leetcode.com/problems/count-primes/)

我们从2开始遍历到根号n，先找到第一个质数2，然后将其所有的倍数全部标记出来，然后到下一个质数3，标记其所有倍数，一次类推，直到根号n，此时数组中未被标记的数字就是质数。我们需要一个 n-1 长度的 bool 型数组来记录每个数字是否被标记，长度为 n-1 的原因是题目说是小于n的质数个数，并不包括n

这种干脆记下来好啦!!

### [136. Single Number](https://leetcode.com/problems/single-number/)
这个也是一个知识点 记住就好啦
x^x = 0, 0^x = x

### [48. Rotate Image](https://leetcode.com/problems/rotate-image/)
[notes](https://www.cnblogs.com/grandyang/p/4389572.html)
flip via  diagonal, then flip each row; 
or, flip via reverse diagonal then flip the whole matrix

### [340. Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)
我目前的想法
BF: 有一个left pointer表示左边的边界, 右边用count记录unique number, 这样的话 应该是O(n) 
重复操作 会扫过同样的区域
改进想法 dp??
[159. Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)
greedy algorithm
但是! 超时啦~
O(n) 的做法是 维护一个size = k 的hashmap

### [210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
有向图的遍历 => indegree, bfs(queue)
[207. Course Schedule](https://leetcode.com/problems/course-schedule/)
这就是经典的拓扑排序了, 可以背下来说实话
`There are a total of _n_ courses you have to take, labeled from 0 to n-1.`
This is a hint for just using vector to store indegree, otherwise, a hashmap is needed.

### [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)
This is a tricky one!! fast-slow pointer is easy to recap, but how can I compare them?
Use a **stack** to reverse the order!!
handling **odd and even** numbers of elements in linked list is also interesting!

### [179. Largest Number](https://leetcode.com/problems/largest-number/)
我现在的想法:
按照digits sort 就好, 也就是说自定义排序. 可以把数字转成vector嘛??
[notes](https://www.cnblogs.com/grandyang/p/4225047.html)
实际上是要把他们转换成字符串 string
The way for creating self-defined sort is interesting
```
sort(nums.begin(), nums.end(), [](int a, int b) { 
	return to_string(a) + to_string(b) > to_string(b) + to_string(a); 
});
``` 
### [315. Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)
BF : O(n^2)
这题的改进方法真的没有想到, 参考了解答之后, 发现居然是用BS, 思路是将给定数组从最后一个开始，用二分法插入到一个新的数组，这样新数组就是有序的，那么此时该数字在新数组中的坐标就是原数组中其右边所有较小数字的个数.
*BS insert sorting*

### [78. Subsets](https://leetcode.com/problems/subsets/)
This is a tipical backtracking. 
[Subsets II](https://leetcode.com/problems/subsets-ii/) remove duplicates

### [55. Jump Game](https://leetcode.com/problems/jump-game/)
这种1D Array 的问题可以思考dp, greedy algorithm
1. dp:
剩余跳力, 一旦出现了负值, 就说明有个点跳不动, `return false`
`dp[i] = max(dp[i-1], nums[i-1]) - 1`
2. greedy algorithm: 
不是很关心每个位子的剩余跳力, 只想知道能不能到达队尾, 也就是说只对最远能够到达的位置感兴趣
那么可以设一个新的variable called reach indicating the fatherest pace we can reach
```
for (int i = 0; i < n; ++i) {
    if (i > reach || reach >= n - 1) break; //where to stop
    reach = max(reach, i + nums[i]);
}
```

### [166. Fraction to Recurring Decimal](https://leetcode.com/problems/fraction-to-recurring-decimal/)
I have not idea about this one.....:)

### [784. Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/)
This one is interesting,
1. adding
pseudo code:
```
for(each char in S)
	len = the current length of res vector
	if is a numeric value: push into every string in res
	else :
		enlarge the res vector to 2 times;
		push the lowercase char to res[i];
		push the uppercase char to res[i+len];
```
2. recursion && backtracking
pseudo code:
```
main function:
	helper(res, index, S);
helper fucntion:
	//stop
	index == S.size();
	res.push_back(s);
	return; //backtracking
	helper(res, index + 1; S);
	if char : convert its case, helper(res, index + 1, S);
```
### [148. Sort List](https://leetcode.com/problems/sort-list/)
当只有一个结点的时候就是有序的
从中间断开, 分成两部分，左右两边再分别调用排序的递归函数 sortList()，得到各自有序的链表后，再进行 merge()，这样整体就是有序的了.
This question is a combination of two classic function:
1. cut from middle fpr a linked list
2. merge two linked list in ascending order

### [103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
This is one a classic BFS!!
Should be very familar to you!

### [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)
我的想法: 可以确定root (the first element in preorder), 然后大概就是recusion?
[note](https://www.youtube.com/watch?v=GeltTz3Z1rw)

### [134. Gas Station](https://leetcode.com/problems/gas-station/)

### [207. Course Schedule](https://leetcode.com/problems/course-schedule/)
Classic topology sort.
1. initiate the graph `vector<vector<int>> graph(numCourses, vector<int>());`
2. initiate the `vector<int> indegree(numCourses);`
3. push all 0 indegree nodes in queue
4. looping the queue, pop the top into res and decrease its edge ends indegree by 1; push to queue if it is zero
5. After the loop, if all indegree are zero => true, otherwise => false

### [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)
My thoughts, use hashmap and offset. 

### [75. Sort Colors](https://leetcode.com/problems/sort-colors/)
This one I have full remeber to it! Kinda like a quick sort
Use three pointers, red(starts at 0), blue(starts at len -1) and curr(starts at 0)
Then swap and move pointers

### [29. Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)
????

### [150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)
This is also a very classic application of stack!!

### [198. House Robber](https://leetcode.com/problems/house-robber/)
classic dp, seperate the vector into odd and even
<!--stackedit_data:
eyJoaXN0b3J5IjpbODM3NTgwMTYxLC0xMzg5ODUxMjY3LDE4NT
g3NjQ3MTcsLTIwMjAyMjE5MzYsMjA5ODgyNjQyNCwxOTA1OTI1
MDIwLC02MzkyMTgxNjMsMzQ2MjI1MDY5LDE5NjQxNzE5MzcsLT
kzMjA5MTk0NCwtMTk5MDQ1ODU0NiwtMTU2NTY3MTYwNCwxNTEx
OTEzMjI1LC0xMTc1ODAwNzIzLDE5NjUxMjYwNDksLTc4OTk0NT
A3NCwtMzI4OTk4OTg5LC0xMDg4NTU4Mjk2LC0xMjIwMzUyMjY5
LC0xNDEwMTk4NTE1XX0=
-->