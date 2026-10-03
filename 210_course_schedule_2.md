# Solution Kahn algorithm+topological sort

```cpp
class Solution {
public:
   
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> graph(numCourses);
        vector<int> indegree(numCourses,0);
        for(auto p:prerequisites){
            int course=p[0];
            int preq=p[1];
            graph[preq].push_back(course);
            indegree[p[0]]++;
        }
        queue<int> q;
        for(int i=0;i<numCourses;i++){
            if(indegree[i]==0) q.push(i);
        }
        int taken=0;
        while(!q.empty()){
            int node=q.front();
            q.pop();
            taken++;
            for(auto& n:graph[node]){
                indegree[n]--;
                if(indegree[n]==0) q.push(n);
            }
        }
        return taken==numCourses;
       
    }
};
```
## Complexity
**Time:**  O(V + E)
**Space:** O(V + E)