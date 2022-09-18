![This Link Doesn't Work](https://cdn.discordapp.com/attachments/707311202547662963/1020924208714362921/unknown.png)

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        
        
        def preorderTraversal(node):
            #Base case, we will stop here at the "bottom" of the tree.
            if not node:
                return
            
            #recursively calls left and right child
            #If left or right child exists, return the array of that said child, else return empty array
            left = preorderTraversal(node.left) if node.left else []
            right = preorderTraversal(node.right) if node.right else []
            
            #What we return from bottom to top, and from top return to our outer function call.
            return [node.val] + left + right
        
        
        return preorderTraversal(root)
```

<p>Time Complexity: O(n)</p>
Since we're traversing through each node once. I think it could be more accurate depicted as O(2n)
since we're traversing top-down, then bottom-up through recursion. but it would be reduced to O(n)
anyways.

<p>Space Complexity: O(n + n)</p>
Well we need to store n elements, and since we're using recursion, we need to account for
stack memory as well. and since there are n nodes, there would be n parents and therefor n memory
for our stack.