<p>Here we will talk about the general outline of depth first search using global variables.
A trick I used to remember each type of traversal is PriP.

<b>Pr</b>eorder Traversal (Root, Left, Right)<br>
<b>I</b>norder Traversal (Left, Root, Right)<br>
<b>P</b>ostorder Traversal (Left, Right, Root)<br>

Note how in the PrIP order, the root shift right every time. In our DFS, our "core" code 
would act similarly by shifting down. 
</p>

<p>Here is the global variable version and intuition for <a href = "https://leetcode.com/problems/binary-tree-preorder-traversal/">Preorder Traversal</a></p>

```Python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        
        #Global variable to store our result
        #Note that lists and data objects are automatically global variables inside another function's scope
        result = []
        
        #PrIP --> Root/Left/Right
        def preorderTraversal(node):
            #Base case
            if not node:
                return
            
            #Root code
            result.append(node.val)
            #Left
            preorderTraversal(node.left)
            #Right
            preorderTraversal(node.right)
            
            return
        
        
        preorderTraversal(root)
        return result
```

<p>Here is the global variable version of <a href = "https://leetcode.com/problems/binary-tree-inorder-traversal/"> Inorder traversal </a></p>

```Python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        #Global variable
        result = []
        
        def inorder(node):
            #Base Case
            if not node:
                return
            
            #Left
            inorder(node.left)
            #Root code
            result.append(node.val)
            #Right
            inorder(node.right)
            
            return
        
        #Execute function
        inorder(root)
        return result

```


<p>Here is the global variable version of <a href = "https://leetcode.com/problems/binary-tree-postorder-traversal/">Postorder Traversal.</a></p>

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        #Global variable
        result = []
        
        def inorder(node):
            #Base Case
            if not node:
                return
            
            #Left
            inorder(node.left)
            #Root code
            result.append(node.val)
            #Right
            inorder(node.right)
            
            return
        
        #Execute function
        inorder(root)
        return result
```

<p>Note how the format for every traversal is the same, but the result.append is shifted
down by 1 line every time. It follows the PrIP format and it's a helpful trick to remember
if you ever need it.

There are different base cases too, since we're using recursion and recursion isn't limited
to Tree traversal. We can use them for back-tracking algorithms which is useful for 
back-tracking problems and DP (Yes, some dp are recursions with memoization).</p>
