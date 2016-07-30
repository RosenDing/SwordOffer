## 二叉搜索树的第k个结点

### 题目描述
给定一颗二叉搜索树，请找出其中的第k大的结点。例如，5 / \ 3 7 /\ /\ 2 4 6 8 中，按结点数值大小顺序第三个结点的值为4。

### 思路
1. 对于二叉搜索树，中序遍历的结果是按照顺序来的，我们设置一个变量用来计数，递归的遍历树，如果到了第k个，则把那个数取出来，我在这用的是ArrayList来存储那个结点
2. 还可以在递归方法中直接返回结点，无需用ArrayList跟踪存储，更加简化

### 代码
    import java.util.ArrayList;
    /*
    public class TreeNode {
        int val = 0;
        TreeNode left = null;
        TreeNode right = null;
    
        public TreeNode(int val) {
            this.val = val;
    
        }
    
    }
    */
    public class Solution {
        TreeNode KthNode(TreeNode pRoot, int k)
        {
            if (pRoot == null) {
            	return null;
            }
            ArrayList<TreeNode> list = new ArrayList<TreeNode>();
            myNode(pRoot, k, list);
            if (list.size() == 0) {
            	return null;
            } else {
            	return list.get(0);
            }
        }
    	int index = 0;
    	public void myNode(TreeNode node, int k, ArrayList<TreeNode> list) {
    		if (node == null) {
    			return;
    		}
    		myNode(node.left, k, list);
    		index++;
    		if (index == k) {
    			list.add(node);
    			return;
    		}
    		myNode(node.right, k, list);
    		
    	}
    // 递归的方法返回结点
    public TreeNode myNode01(TreeNode node, int k) {
		TreeNode target = null;
		if (node.left != null) {
			target = myNode01(node.left, k);
		}
		if (target == null) {
			index++;
			if (index == k) {
				return node;
			}
		}
		if (target == null && node.right != null) {
			target = myNode01(node.right, k);
		}
		return target;
		
	}
    }
