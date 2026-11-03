# Solution Graph bfs
```cpp
class Solution {
public:
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        wordList.push_back(beginWord);
        unordered_map<string,vector<string>> mp;
        
        for(auto &x:wordList){
            for(int i=0;i<x.size();i++){
                string word=x.substr(0,i)+'*'+x.substr(i+1);
                mp[word].push_back(x);
            }
        }
        unordered_set<string> vis;
        queue<pair<string,int>> q;
        q.push({beginWord,1});
        string word;
        string nword;
        vis.insert(beginWord);
        int counter;
        while(!q.empty()){
            word=q.front().first;
            counter=q.front().second; 
            q.pop();
            if(word==endWord) return counter;
            
                for(int i=0;i<word.size();i++){
                    nword=word.substr(0,i)+'*'+word.substr(i+1);
                    for(auto& s:mp[nword]){
                        if(vis.find(s)==vis.end()){
                            vis.insert(s);
                            q.push({s,counter+1});
                    }
                }}
            
        }
        return 0;

    }
};
```
## Complexity
**Time:**O(N*M*M)
**Space:**O(N*M*M)