# Solution one dfs
```cpp
class Solution {
public:
    bool dfs(int node,vector<int> &visit,vector<int>& path ,vector<vector<int>>& graph){
        visit[node]=1;
        path[node]=1;

        for(auto n:graph[node]){
            if(!visit[n]){
                if(dfs(n,visit,path,graph)) return true;
            }
            else if(path[n]){
                return true;
            }
        }
        path[node]=0;
        return false;
    }
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> graph(numCourses);

        for(auto p:prerequisites){
            int course=p[0];
            int preq=p[1];
            graph[preq].push_back(course);
        }
        vector<int> visit(numCourses,0);
        vector<int> path(numCourses,0);

        for(int i=0;i<numCourses;i++){
            if(!visit[i]){
                if(dfs(i,visit,path,graph)) return false;
            }
        }
        return true;
    }
};
```
## Complexity
**Time:**  O(V + E)
**Space:** O(V + E)

# Solution two 
```cpp
class Solution {
public:
   
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        vector<vector<int>> graph(numCourses);//O(E) space
        vector<int> indegree(numCourses,0);//O(v) space
        for(auto p:prerequisites){ //O(E) worst case
            int course=p[0];
            int preq=p[1];
            graph[preq].push_back(course);
            indegree[p[0]]++;
        }
        queue<int> q; //O(v) space
        for(int i=0;i<numCourses;i++){ //O(n) or O(V)
            if(indegree[i]==0) q.push(i);
        }
        int taken=0;
        while(!q.empty()){ //O(V) so total O(V+E)
            int node=q.front();
            q.pop();
            taken++;
            for(auto& n:graph[node]){   //O(E)
                indegree[n]--;
                if(indegree[n]==0) q.push(n);
            }
        }
        return taken==numCourses;
       
    }
};
```
## Complexity
**Time:**O(E)+O(V)+O(E)=2*O(E)+O(V)=O(V+E)
**Space:**O(E)+O(V)+O(V)=O(E)+2*O(V)=O(V+E)