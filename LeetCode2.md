# LeetCode 2. Add Two Numbers
[See Problem](https://leetcode.com/problems/add-two-numbers/solution/)

## Solution 1:
Consider: The length of l1 may be different with l2, and also could be 0.

Hint: The position of a digit in the linkedlist = the position of this digit in the number

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
	def addTwoNumbers(self, l1, l2):
		"""
		:type l1: ListNode
		:type l2: ListNode
		:rtype: ListNode
		"""
		# points to current position
		l1_current = l1
		l2_current = l2
		
		# stores the sum of two numbers
		result = 0
			
        # stores the number stored in l1 and l2 linkedlist
		l1_number = 0
		l2_number = 0
				
		# i stores the position
		i = 0
				
		# Do loop, find these two numbers 
		while l1_current != None:
			l1_number = l1_number + l1_current.val*pow(10,i)
			l1_current = l1_current.next
			i+=1
						
		# Initial position, since l1 and l2 may have different length    
		i = 0
		while l2_current != None:
			l2_number = l2_number + l2_current.val*pow(10,i)
			l2_current = l2_current.next
			i+=1
        
		# Sum calculation
		result = l1_number + l2_number
    
		# Store the result into linkedlist
		# Do before the loop, 
		#    1. store the head;
		#    2, avoid the consequence that result is 0 output nothing
		result_list = ListNode(result%10)
		result_list_current = result_list
		result = result/10
		while result != 0:
			result_list_current.next = ListNode(result%10)
			result_list_current = result_list_current.next
			result = result/10
		return result_list
```

Note:

1. *pow(10,i)* : 

   calculate the result of the power i of number 10.

