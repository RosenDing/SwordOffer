## 最小的K个数

### 题目描述
输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

### 思路
1. 可以用快速排序的思想，分块，直到分出前k个为止，前k个不一定是按顺序的，注：这个方法需要改变数组
2. 可以借助一个k容量的辅助空间，最大堆或红黑树，这个方法处理大数组小k的情况比较合适，且不用改变原始数组

### 代码
    import java.util.ArrayList;
    public class Solution {
        public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {
    		ArrayList<Integer> list = new ArrayList<Integer>();
    		if (input == null || input.length == 0 || k == 0 || k > input.length) {
    			return list;
    		}
    		if (k == input.length) {
    			for (int x: input) {
    				list.add(x);
    			}
    			return list;
    		}
    		int start = 0;
    		int end = input.length - 1;
    		int index = partition(input, start, end);
    		while (index != k - 1) {
    			if (index > k - 1) {
    				end = index - 1;
    				index = partition(input, start, end); 
    			} else {
    				start= index + 1;
    				index = partition(input, start, end);
    			}
    		}
    		for (int i = 0; i < k; i++) {
    			list.add(input[i]);
    		}
    		return list;
        }
    	
    	public int partition(int[] data, int left, int right) {
    		if (left < right) {
    			int x = data[left];
    			while (left < right) {
    				while (left < right && data[right] >= x) {
    					right--;
    				}
    				if (left < right) {
    					data[left] = data[right];
    				}
    				while (left < right && data[left] < x) {
    					left++;
    				}
    				if (left < right) {
    					data[right] = data[left];
    				}
    				data[left] = x;
    			}
    		}
    			return left;
    	}
    }
