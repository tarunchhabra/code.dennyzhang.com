
# Leetcode: Merge k Sorted Lists     :BLOG:Medium:

---

Merge k Sorted Lists  

---

Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.  

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/problems/merge-k-sorted-lists)  

Credits To: [leetcode.com](https://leetcode.com/problems/merge-k-sorted-lists/description/)  

Leave me comments, if you have better ways to solve.  

---

    ## Blog link: https://code.dennyzhang.com/merge-k-sorted-lists
    ## Basic Ideas: Compare the first node of all list
    ##              Insert the smallest to the result list
    ##              If two lists have the same value, insert the first one, then the next
    ##
    ## Complexity: Time O(k*m), k is the max size of all list. m is the count of list. Space O(1)
    # Definition for singly-linked list.
    # class ListNode(object):
    #     def __init__(self, x):
    #         self.val = x
    #         self.next = None
    
    class Solution(object):
        def mergeKLists(self, lists):
    	"""
    	:type lists: List[ListNode]
    	:rtype: ListNode
    	"""
    	dummyNode = ListNode(None)
    	p = dummyNode
    
    	length = len(lists)
    	p_list = []
    	# Configure the heads
    	for i in xrange(length):
    	    if lists[i]:
    		p_list.append(lists[i])
    
    	while len(p_list) != 0:
    	    # For the remaining list, find the mininum value
    	    min_index = 0
    	    for i in range(1, len(p_list)):
    		if p_list[i].val < p_list[min_index].val:
    		    min_index = i
    	    # insert node
    	    p.next = p_list[min_index]
    	    p = p.next
    	    # update the old list
    	    p_list[min_index] = p_list[min_index].next
    	    # remove empty list
    	    if p_list[min_index] is None:
    		del p_list[min_index]
    	    ## Add the tail
    	    if len(p_list) == 1:
    		p.next = p_list[0]
    		break
    	return dummyNode.next
    
    # s = Solution()
    # print s.mergeKLists([[], []])
