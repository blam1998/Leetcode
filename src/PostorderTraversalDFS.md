![This Link Doesn't Work](https://media.discordapp.net/attachments/707311202547662963/1020935773178056774/unknown.png?width=767&height=675)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        
        
        def postorder(node):
            #Base case
            if not node:
                return

            #left =  left array if left child exists, else left = empty array
            left = postorder(node.left) if node.left else []
            #right = right array if right child exists, else right = empty array
            right = postorder(node.right) if node.right else []
            
            return left + right + [node.val]
        
        return postorder(root)
```