#LeetCode 771 Jewels and Stones
!(See Problem)[https://leetcode.com/problems/jewels-and-stones/description/]
## Solution 1:
Hint: Using **dict** 

	class Solution:
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        j_dict = {}
        count = 0
        for j in J:
            j_dict[j] = 1
        for c in S:
            if j_dict.get(c) == 1:
                count += 1
        return count

Note: 
1. *for j in J*
It will look through all the characters in J, and store it in to a varaible *j*.
2. *j_dict.get(c)*
for c not in j_dict, it will return **None** value.
If use j_dict[c], for c not in j_dict, it will report  **KeyError**.


