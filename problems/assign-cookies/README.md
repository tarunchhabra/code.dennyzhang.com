
# Leetcode: Assign Cookies     :BLOG:Amusing:

---

Assign cookies wisely, and make more children happy  

---

Similar Problems:  

-   [Review: TwoPointers Problems](https://code.dennyzhang.com/review-twopointer), [Tag: #twopointer](https://code.dennyzhang.com/tag/twopointer)
-   [Review: Game Problems](https://code.dennyzhang.com/review-game), [Tag: #game](https://code.dennyzhang.com/tag/game)

---

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor gi, which is the minimum size of a cookie that the child will be content with; and each cookie j has a size sj. If sj >= gi, we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.  

Note:  

-   You may assume the greed factor is always positive.
-   You cannot assign more than one cookie to one child.

Example 1:  

    Input: [1,2,3], [1,1]
    
    Output: 1
    
    Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
    And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
    You need to output 1.

Example 2:  

    Input: [1,2], [1,2,3]
    
    Output: 2
    
    Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
    You have 3 cookies and their sizes are big enough to gratify all of the children, 
    You need to output 2.

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/problems/assign-cookies)  

Credits To: [leetcode.com](https://leetcode.com/problems/assign-cookies/description/)  

Leave me comments, if you have better ways to solve.  

---

    ## Blog link: https://code.dennyzhang.com/assign-cookies
    ## Basic Ideas: Greedy
    ##        Assign the smallest cookie to the the mininum greedy child, if it matches
    ##        Sort the list of g and s
    ## Complexity: Time O(n*log(n)), Space O(1)
    class Solution(object):
        def findContentChildren(self, g, s):
    	"""
    	:type g: List[int]
    	:type s: List[int]
    	:rtype: int
    	"""
    	g, s = sorted(g), sorted(s)
    	i, res = 0, 0
    	# check for each cookie
    	for cookie in s:
    	    # check child
    	    if cookie >= g[i]:
    		# assign cookie
    		res += 1
    		# move to next child
    		i += 1
    	    # no child to check
    	    if i == len(g):
    		break            
    	return res
    
    # s = Solution()
    # print s.findContentChildren([10,9,8,7], [5,6,7,8]) # 2
    # print s.findContentChildren([1,2, 3], [1,1]) # 1
    # print s.findContentChildren([1,2], [1,2,3]) # 2
