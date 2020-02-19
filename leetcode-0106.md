## 思路
- 和前序、中序数组构成二叉树思路一样，注意判断边界

```java
class Solution {
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        if(inorder.length==0) return null;
        return helper(inorder, 0, inorder.length-1, postorder, 0, postorder.length-1);
    }

    private TreeNode helper(int[] inorder, int is, int ie, int[] postorder, int ps, int pe){
        if(is==ie){
            return new TreeNode(inorder[is]);
        }
        // 这里是需要注意的
        if(is > ie){
            return null;
        }
        int rootVal = postorder[pe];
        int leftSize = 0;
        for(int i=is; i<=ie; i++){
            if(inorder[i]==rootVal){
                leftSize = i-is;
                break;
            }
        }
        TreeNode root = new TreeNode(rootVal);
        root.left = helper(inorder, is, is+leftSize-1, postorder, ps, ps+leftSize-1);
        root.right = helper(inorder, is+leftSize+1, ie, postorder, ps+leftSize, pe-1);
        return root;
    }
}
```