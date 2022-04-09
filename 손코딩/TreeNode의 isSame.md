```
class TreeNode { 
  TreeNode left, right;
  int val;
} 일 때 boolean isSame(TreeNode L, TreeNode R) 구현해라.



boolean isSame(TreeNode L, TreeNode R) { 
  if(L == null && R == null) return true;
  if(L == null && R != null) return false; 
  if(L != null && R == null) return false; 
  if(L.val != R.val) return false;
  
  boolean lSame = isSame(L.left, R.left); 
  boolean rSame = isSame(L.right, R.right);
  return lSame && rSame;
}
```
