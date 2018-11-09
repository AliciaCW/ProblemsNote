# LeetCode 3. Longest Substring Without Repeating Characters
(See Problem)[https://leetcode.com/problems/longest-substring-without-repeating-characters/description/]
1. Brute Force: Find all substrings and check duplicate

2. Sliding Windows: Use dict store the (char, index) of a substring s[i,j]. Let result = max(result, j-i) .If meet a duplicate char,, update i be i + 1, and keep looping untill  i = len(s).

3. Improved Sliding Windows: Use dict store the newest index of char, let result = max(result, j-i). If meet a duplicate char, update the i be the duplicated char index + 1, update dict[char], keep looping untill j = len(s).


​	
    class Solution:
    ​    def lengthOfLongestSubstring(self, s):
    ​        """
    ​        :type s: str
    ​        :rtype: int
    ​        """
    ​        char_dict = {}
    ​        result = 0
    ​        i = 0
    ​        length = len(s)
    ​        for j in range(length):
    ​            if s[j] in char_dict and char_dict.get(s[j]) >= i:
    ​                i = char_dict.get(s[j]) + 1
    ​            else:
    ​                result = max(j-i+1,result)
    ​                char_dict[s[j]] = j
    
    ​        return result


​    
    	char_dict[s[j]] = j
    
     return result


Note:
1. *s[j] in char_dict*:
    check if key:s[j] in dict: char_dict or not.