#包含min函数的栈

##题目描述

定义栈的数据结构，请在该类型中实现一个能够得到栈最小元素的min函数。

```
import java.util.Stack;
public class Solution {
    
	int min;
    Stack<Integer> stack = new Stack<Integer>();
    public void push(int x) {
        if (stack.isEmpty()){
            stack.push(0);
            min = x;
        }else{
            stack.push(x - min);//Could be negative if min value needs to change
            if (x < min) 
                min = x;
        }
    }
    public void pop() {
        if (stack.isEmpty()) {
            return;
        }
        int pop=stack.pop();
        if (pop < 0) {
            min = min - pop;//If negative, increase the min value
        } 
    }
    public int top() {
        int top = stack.peek();
        if (top > 0){
            return (top + min);
        }else{
           return min;
        }
    }
    public int min() {
        return min;
    }
}
```
