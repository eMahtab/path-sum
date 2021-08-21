# Path Sum 

## https://leetcode.com/problems/path-sum

Given the root of a binary tree and an integer targetSum, return true if the tree has a root-to-leaf path such that adding up all the values along the path equals targetSum.

A leaf is a node with no children.

![Path Sum example](pathsum.jpg?raw=true "Root to Leaf Path Sum")


# Implementation : DFS
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean hasPathSum(TreeNode root, int targetSum) {
        if(root == null)
            return false;
        return traverse(root, targetSum);
    }
    
    private boolean traverse(TreeNode node, int targetSum) {
        if(node.left == null && node.right == null && node.val == targetSum)
            return true;
        boolean leftPath = false;
        if(node.left != null)
            leftPath = traverse(node.left, targetSum - node.val);
        boolean rightPath = false;
        if(node.right != null)
            rightPath = traverse(node.right, targetSum - node.val);
        
        return leftPath || rightPath;
    }
}
```
