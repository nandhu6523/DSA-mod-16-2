# DSA-mod-16-2
# AIM:
 To implement a left rotation operation in an AVL tree and insert a user-given value n into the tree, then display the AVL tree using preorder traversal.
# ALGORITHM:

step 1:Start by defining a node class Node to represent AVL tree nodes.

step 2:Define AVL tree class with methods:

   a] insert for inserting nodes with balancing

   b] leftRotate for performing left rotation

   c] getHeight, getBalance to assist balancing

step 3:Create the tree with initial elements [13, 10, 15, 5, 11, 16].

step 4:Get value n from the user.

step 5:Insert n into the AVL tree.

step 6:Print the tree using preorder traversal.

# PROGRAM:
```
class TreeNode(object):
	def __init__(self, val):
		self.val = val
		self.left = None
		self.right = None
		self.height = 1

class AVL_Tree(object):
	def insert(self, root, key):
		if not root:
			return TreeNode(key)
		elif key < root.val:
			root.left = self.insert(root.left, key)
		else:
			root.right = self.insert(root.right, key)

	
		root.height = 1 + max(self.getHeight(root.left),
						self.getHeight(root.right))

		balance = self.getBalance(root)

		if balance > 1 and key < root.left.val:
			return self.rightRotate(root)

	
		if balance < -1 and key > root.right.val:
			return self.leftRotate(root)

		
		if balance > 1 and key > root.left.val:
			root.left = self.leftRotate(root.left)
			return self.rightRotate(root)
   
		if balance < -1 and key < root.right.val:
			root.right = self.rightRotate(root.right)
			return self.leftRotate(root)

		return root

	def leftRotate(self, z):
	    
	    y=z.right
	    T2=y.left
	    
	    y.left=z
	    z.right=T2
	    z.height=1+max(self.getHeight(z.left),
	                self.getHeight(z.right))
	                      
	    y.height=1+max(self.getHeight(y.left),
	                self.getHeight(y.right))
	    return y

	
	def getHeight(self, root):
		if not root:
			return 0

		return root.height

	def getBalance(self, root):
		if not root:
			return 0

		return self.getHeight(root.left) - self.getHeight(root.right)

	def preOrder(self, root):

		if not root:
			return

		print("{0} ".format(root.val), end="")
		self.preOrder(root.left)
		self.preOrder(root.right)


myTree = AVL_Tree()
root = None

 # WRITE YOUR CODE HERE 
n=int(input()) 
root = myTree.insert(root, 13)
root = myTree.insert(root, 10)
root = myTree.insert(root, 15)
root = myTree.insert(root, 5)
root = myTree.insert(root, 11)
root = myTree.insert(root, 16)
root = myTree.insert(root, n)

 # WRITE YOUR CODE HERE 


print("Preorder traversal of the constructed AVL tree is")
myTree.preOrder(root)
print()
```

# RESULT:
 Thus the implement of a left rotation operation in an AVL tree and insert a user-given value n into the tree, then display the AVL tree using preorder traversal was successfully executed.
