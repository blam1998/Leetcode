![Picture Link Doesn't Work](https://cdn.discordapp.com/attachments/707311202547662963/1020853754695782441/unknown.png)
```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

from collections import deque
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        result = []
        
        queue = deque()
        
        #Edge case, if there's no root node, return empty array.
        if not root:
            return result
        
        #Put root in queue
        queue.append(root)
        
        while queue:
            currLevel = []
            
            """
            Here we create a "Snapshot" of all of the items currently in
            the Queue. Any items added to the queue won't be included in
            this "Snapshot". So if a node has children, we can add it to
            the queue, but it won't be considered in this iteration.
            """
            for i in range(len(queue)):
                currNode = queue.popleft()
                #If there's a left child, add it to queue
                if currNode.left:
                    queue.append(currNode.left)
                #If there's a right child, add it to queue
                if currNode.right:
                    queue.append(currNode.right)
                #Add current node to current level array
                currLevel.append(currNode.val)
            #Add current level array to result array.
            result.append(currLevel)
        
        return result
```

<p>Time Complexity: <b>O(n)</b></p>
<p>Time complexity is O(n) because we're traversing through each node once.</p>

<p>Space Complexity: <b>O(n)</b></p>
<p>Space complexity is O(n) because we're storing all of the nodes in result array. Although
we have extra memory for currLevel array, that memory is cleared afterwards. Worse case is at
most O(2n) which is equivalent to O(n).</p>
