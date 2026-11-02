# solution dfs 
```cpp
class WordDictionary {
public:
    struct Node{
        Node* child[26];
        bool end;
        Node(){
            end=false;
            for(int i=0;i<26;i++){
                child[i]=NULL;
            }
        }
    };
    Node* root;
    WordDictionary() {
        root=new Node();
    }
    int index;
    void addWord(string word) {
        Node* temp=root;
        for(char& c:word){
            index=c-'a';
            if(temp->child[index]==NULL){
                temp->child[index]=new Node();
            }
            temp=temp->child[index];
        }
        temp->end=true;
    }
    bool dfs(Node* root,string& word,int i){
        if(i==word.size()) return root->end;

        char c=word[i];
        if(c!='.' && root!=NULL){
            Node* next=root->child[c-'a'];
            if(next==NULL) return false;
            return dfs(root->child[c-'a'],word,i+1);

        }
        for(int k=0;k<26;k++){
            if(root!=NULL && root->child[k]!=NULL && dfs(root->child[k],word,i+1));
            true;
        }
        return false;
    }
    bool search(string word) {
       return dfs(root,word,0);
    }
};

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary* obj = new WordDictionary();
 * obj->addWord(word);
 * bool param_2 = obj->search(word);
 */
 ```

<!--here in this when there is . then we have to check all the not null paths then do same as other characters -->