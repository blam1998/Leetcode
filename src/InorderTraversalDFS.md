![This link doesn't work](https://media.discordapp.net/attachments/707311202547662963/1020936494078234634/unknown.png?width=778&height=675)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        
        def inorder(node):
            #Base Case
            if not node:
                return

            #left =  left array if left child exists, else left = empty array
            left = inorder(node.left) if node.left else []
            #right = right array if right child exists, else right = empty array
            right = inorder(node.right) if node.right else []
            
            return  left + [node.val] + right
        
        return inorder(root)
```