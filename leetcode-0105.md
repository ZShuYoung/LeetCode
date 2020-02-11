## 思路
- 递归
- 先根据先序的第一个值从中序中找到对应的位置，那么中序中左侧的为左子树，右侧的为右子树，依次递归

```java
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        if(preorder.length != inorder.length) return null;
        if(preorder.length == 0) return null;
        if(preorder.length == 1) return new TreeNode(preorder[0]);
        TreeNode root = new TreeNode(preorder[0]);
        int leftNodes = 0;
        for(int i=0; i<inorder.length; i++){
            if(inorder[i] == root.val){
                leftNodes = i;
                break;
            }
        }
        int[] leftPreorder = Arrays.copyOfRange(preorder, 1, 1+leftNodes);
        int[] leftInorder = Arrays.copyOfRange(inorder, 0, leftNodes);
        int[] rightPreorder = Arrays.copyOfRange(preorder, 1+leftNodes, preorder.length);
        int[] rightInorder = Arrays.copyOfRange(inorder, 1+leftNodes, inorder.length);
        TreeNode left = buildTree(leftPreorder, leftInorder);
        TreeNode right = buildTree(rightPreorder, rightInorder);

        root.left = left;
        root.right = right;
        return root;

    }
}
```