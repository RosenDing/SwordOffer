## 和为S的连续正数序列

### 题目描述
小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck! 

### 输出描述
> 输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序

### 思路
1. 设置一个small，一个big，来控制这个序列，从1开始，若这个序列的和大于sum，则丢掉small，然后small加1；若小于sum，则增加big
2. 注意循环结束条件为：small < (sum + 1) / 2 或者 small <= (sum - 1) / 2
3. 注意：我们不必每次计算small和big之间的值都要遍历一遍，可以设置一个curSum用来保存small和big之间的和，更新small和big时只需要加减small和big即可

### 代码
    import java.util.ArrayList;
    public class Solution {
        public ArrayList<ArrayList<Integer> > FindContinuousSequence(int sum) {
           ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
    		if (sum <= 2) {
    			return result;
    		}
    		int small = 1;
    		int big = 2;
    		int middle = (sum + 1)/2;
    		int curSum = small + big;
    		while (small < middle) {
    			if (curSum == sum) {
    				ArrayList<Integer> list = new ArrayList<Integer>();
    				for (int i = small; i <= big; i++) {
    					list.add(i);
    				}
    				result.add(list);
    			} 
    			while (curSum > sum && small < middle) {
    				curSum -= small;
    				small++;
    				if (curSum == sum) {
    					ArrayList<Integer> list = new ArrayList<Integer>();
    					for (int i = small; i <= big; i++) {
    						list.add(i);
    					}
    					result.add(list);
    				}
    			} 
    			big++;
    			curSum += big;
    		}
    		return result;
        }
    }
