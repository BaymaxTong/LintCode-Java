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

```
import java.util.Stack;
public class Solution {
	int min = Integer.MAX_VALUE;;
    Stack<Integer> stack = new Stack<Integer>();
    
    public void push(int x) {
        // only push the old minimum value when the current 
       // minimum value changes after pushing the new value x
        if(x <= min){          
            stack.push(min);
            min=x;
        }
        stack.push(x);
    }
    
    public void pop() {
        // if pop operation could result in the changing of the current minimum value, 
       // pop twice and change the current minimum value to the last minimum value.
        if(stack.peek() == min) {
            stack.pop();
            min = stack.peek();
            stack.pop();
        }else{
            stack.pop();
        }
        if(stack.empty()){
            min = Integer.MAX_VALUE;
        }
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int min() {
        return min;
    }
}
```
