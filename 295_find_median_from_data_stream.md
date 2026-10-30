# solution using two priority queue min head and max heap
```cpp
class MedianFinder {
public:
    priority_queue<int> left;                                  // max-heap
    priority_queue<int, vector<int>, greater<int>> right;
    MedianFinder() {
        
    }
    
   void addNum(int num) {
    left.push(num);              // 1. push into left

    right.push(left.top());      // 2. move left's top to right
    left.pop();

    if (right.size() > left.size()) {   // 3. rebalance
        left.push(right.top());
        right.pop();
    }
}
    double findMedian() {
        if(left.size()>right.size()) return left.top();
            return (left.top()/2.0)+(right.top()/2.0);
        
    }
};

/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder* obj = new MedianFinder();
 * obj->addNum(num);
 * double param_2 = obj->findMedian();
 */
 ```
 <!-- in this we are using two priority queues min heap and mac heap in a way that at last their top will help us to find the median like if we have an array of 10 items the left max heaf will contain the left half of that array in reverse order or desecding order then the right which is min heap will contain the right half of the array in ascending order so at last we can use or queue's top to find median like if array is (1,2,3,4,5,6) then left queue will contain(3,2,1) and right will contain(4,5,6)>