## 和为S的两个数字

### 题目描述
输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。 

### 输出描述
> 对应每个测试案例，输出两个数，小的先输出。

### 思路
1. 从两头开始遍历数组，若和小于sum，left++，若和大于sum，right--
2. 两头的数的乘积比中间的数的乘积小

### 代码
    import java.util.ArrayList;
    public class Solution {
    	public ArrayList<Integer> FindNumbersWithSum(int [] array,int sum) {
            ArrayList<Integer> result = new ArrayList<Integer>();
            if (array == null || array.length < 2) {
            	return result;
            }
            int left = 0;
            int right = array.length - 1;
            while (left < right) {
            	int temp = array[left] + array[right];
            	if (temp == sum) {
            		result.add(array[left]);
            		result.add(array[right]);
            		return result;
            	} else if (temp > sum) {
            		right--;
            	} else {
            		left++;
            	}
            }
            return result;
        }
    }
