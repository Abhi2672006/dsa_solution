# Solution 
```cpp
class MinStack {
public:
    stack<int> st;
    stack<int> minst;
    MinStack() {
        
    }
    
    void push(int value) {
          st.push(value);
        if(minst.empty() || value<=minst.top() ){
            minst.push(value);
        }
        else{
            minst.push(minst.top());
        }
    }
    
    void pop() {
        st.pop();
        minst.pop();
    }
    
    int top() {
        return st.top();
    }
    
    int getMin() {
        return minst.top();
    }
};
```
<!--There are many ways to solve this problem like with deque one stack two stack -->
## Complexity
- **Time:**O(1)
- **Space:**O(n)