


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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI1NjM2NTg3MiwtMTI5OTMwMDczMywxND
Q2MTc3NDAxLDM0NjAwNjg5NCw5MDI5OTc5NDEsLTg2NjUxMjA5
MSwyMTM1MzI1MTgzLDE2ODA1NTA5MjksLTE3ODAxOTg2NTMsMT
U5MzA5MDIwMSwyMDcxMTc3MDY4LC0xMDM2MTUwMTM3LC03NzI1
NDQ2MTYsLTM2NjYyODIzOCwxNTY1MTk4NTk3LDE0NDY2NTM3MD
YsLTExMDMwNDc1NSwtMTIyODIxOTg1Niw0MzEzNDE2MDcsLTE2
OTE5ODM2M119
-->