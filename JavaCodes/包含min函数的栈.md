## 包含min函数的栈

### 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈最小元素的min函数

### 思路
1. 使用一个辅助栈，跟踪原始栈中每个元素在栈口时的该栈的最小值

### 代码
    import java.util.Stack;
    
    public class Solution {
    
        Stack<Integer> s_data = new Stack();
    	Stack<Integer> s_min = new Stack();
    	public void push(int node) {
            s_data.push(node);
            if (s_min.empty() || node < s_min.peek()) {
            	s_min.push(node);
            } else {
            	s_min.push(s_min.peek());
            }
        }
        
        public void pop() {
            if (!s_data.empty()) {
        		s_data.pop();
        	}
        	if (!s_min.empty()) {
        		s_min.pop();
        	}
        }
        
        public int top() {
            return s_data.peek();
        }
        
        public int min() {
        	return s_min.peek();
        }
    }
