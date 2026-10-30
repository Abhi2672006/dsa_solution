# Solution
```cpp
class Solution {
public:

    bool back(vector<vector<char>>& board,string word,int count,int i,int j){
        if(count==word.size()){
            return true;
        }
        if(i<0 || i>=board.size() || j<0 || j>=board[0].size()|| board[i][j]!=word[count]){
            return false;

        }
        char temp=board[i][j];
        board[i][j]='#';
        int diri[]={-1,1,0,0};
        int dirj[]={0,0,-1,1};
       
            for(int b=0;b<4;b++){
                int newi=i+diri[b];
                int newj=j+dirj[b];
                if(back(board,word,count+1,newi,newj)){
                    return true;
                }
            }

            board[i][j]=temp;
            return false;
        
    }
    bool exist(vector<vector<char>>& board, string word) {
        int m=board.size();
        int n=board[0].size();
        int count=0;
        for (int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(back(board,word,0,i,j)){
                  return true;
                }
            }
        }
        return false;
    }
    
};
```

