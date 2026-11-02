# solution 

```cpp
class Trie {

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
    Trie() {
        root = new Node();
    }
    int index;
    void insert(string word) {
        Node* temp = root;
        for (char c : word) {
            index=c-'a';
            if (temp->child[index] == NULL) {
                temp->child[index] = new Node();
            }
            temp = temp->child[c - 'a'];
        }
        temp->end = true;
    }

    bool search(string word) {
        Node* temp = root;
        for (char c : word) {
            index=c-'a';
            if (temp->child[index] == NULL) return false;
            temp = temp->child[index];
        }
        return temp->end;
    }

    bool startsWith(string prefix) {
        Node* temp = root;
        for (char c : prefix) {
            index=c-'a';
            if (temp->child[index] == NULL) return false;
            temp = temp->child[index];
        }
        return true;
    }
};
```
