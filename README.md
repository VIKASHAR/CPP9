# CPP MODULE 9 :

# 9a :

# PROGRAM STATEMENT :
Write the splitNode Module of B Tree in CPP.

# ALGORITHM :
1. Initialize: Identify the node to split and its parent node. Allocate a new node to act as the sibling of 
the split node.
2. Determine Split Point: Find the middle key of the node to split, which will move to the parent node.
3. Redistribute Keys and Children: Transfer keys and child pointers from the split node to the new 
sibling node starting from the middle key onward.
4. Update Parent Node: Insert the middle key into the parent node, and update its child pointers to 
include the new sibling node.
5. Return Updated Tree: Complete the split and ensure all B-Tree properties are maintained, then 
return the updated structure

# PROGRAM :
NAME : Vikash A R
REG NO : 212222040179
```
void splitNode(int val, int *pval, int pos, BTreeNode *node, BTreeNode *child, BTreeNode 
**newNode) 
{
 int median,j;
 if(pos>MIN)
 median=MIN+1;
 else
 median=MIN;
 *newNode=new BTreeNode;
 j=median+1;
 while(j<=MAX)
 {
 (*newNode)->val[j-median]=node->val[j];
 (*newNode)->link[j-median]=node->link[j];
 j++;
 }
 node->count=median;
 (*newNode)->count=MAX-median;
 if(pos<=MIN)
 {
 insertKey(val,pos,node,child);
 
 }
 else
 {
 insertKey(val,pos-median,*newNode,child);
 }
 *pval=node->val[node->count];
 (*newNode)->link[0]=node->link[node->count];
 node->count--;
 
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/18ee2e4e-74fa-4f43-9f4c-586f13564a11)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 9b :

# PROGRAM STATEMENT :
Write the findParent Module of the BPlus Tree in CPP

# ALGORITHM :
1. Initialize: Start at the root of the B+ Tree and traverse down to locate the target node whose 
parent is to be found.
2. Track Parent: Keep a pointer to the current node as the potential parent while traversing its 
children.
3. Locate Child: For each child pointer, check if it matches the target node or contains the key 
belonging to the target node.
4. Return Parent: If the target node is found, return the current node as its parent; if no parent 
exists (root node), return nullptr.
5. End: Ensure all steps preserve the B+ Tree properties and handle edge cases like root or 
single-node trees.

# PROGRAM :
```
Node *BPTree::findParent(Node *cursor, Node *child) 
{
 Node *parent;
 if (cursor->IS_LEAF || (cursor->ptr[0])->IS_LEAF) 
 {
 return NULL;
 }
 for (int i = 0; i < cursor->size + 1; i++)
 {
 if (cursor->ptr[i] == child)
 {
 parent = cursor;
 return parent;
 }
 else
 {
 parent = findParent(cursor->ptr[i], child);
 if (parent != NULL)
 return parent;
 }
 }
 return parent;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/86259aca-f49d-4f15-beef-6bc6d7f6893f)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 9c :

# PROGRAM STATEMENT :
Write the Traversal module of the red black tree in CPP.

# ALGORITHM :
1. Initialize: Start traversal from the root node of the Red-Black Tree.
2. Choose Traversal Order: Decide on the traversal order—In-order (left, root, right), Pre￾order (root, left, right), or Post-order (left, right, root).
3. Recursive Traversal: Implement a recursive function that visits nodes in the chosen order, 
respecting Red-Black Tree properties (e.g., maintaining colors and balancing).
4. Display Nodes: During each visit, print or process the node's value (and color if required).
5. End Traversal: Return control once all nodes are visited, ensuring the tree's structure 
remains unaltered.

# PROGRAM :
```
void inorder(node* root)
{
 if(root == NULL)
 {
 return;
 }
 inorder(root->l);
 cout<<"Data="<<root->d<<" Color="<<root->c<<endl;
 inorder(root->r);
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/1de5c86b-2e94-4b21-bf8e-a00e0c089552)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 9d :

# PROGRAM STATEMENT :
Write the Splay/BST construction module of splay tree in CPP.

# ALGORITHM :
1. Initialize Tree: Start with an empty tree and define the node structure with key, left, and 
right child pointers.
2. Insert Nodes: Insert keys into the binary search tree (BST) by recursively finding the correct 
position based on the BST property.
3. Splay Operation: After insertion, perform the splay operation by rotating the newly inserted 
node to the root using Zig (single rotation), Zig-Zig, or Zig-Zag (double rotations).
4. Maintain Splay Tree Property: Ensure the recently accessed or inserted node becomes the 
root after the splay operation.
5. Complete Construction: Repeat steps 2–4 for all input keys, ensuring the splay tree is 
balanced and follows the access property.

# PROGRAM :
```
node *BST(node *root, int key)
{
 if(root == NULL)
 {
 node *newnode = new node;
 newnode->key = key;
 newnode->left = NULL;
 newnode->right = NULL;
 return newnode;
 }
 else
 {
 if(root->key > key)
 {
 root->left = BST(root->left,key);
 }
 else
 {
 root->right = BST(root->right,key);
 }
 }
 return root;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/e558709c-85f1-4a29-93c2-1abf0d621e65)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.
