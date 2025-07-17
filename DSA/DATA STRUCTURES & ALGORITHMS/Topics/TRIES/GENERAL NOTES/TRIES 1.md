  
⇒A  
**Trie** is a special kind of tree used to store and search words or sequences in a way that makes finding them faster.  
  
⇒A  
**Trie** is a type of tree data structure commonly used for storing strings. It is especially efficient for prefix-based queries, making it useful for applications like autocomplete, spell checking, and longest prefix matching.

### What is a Trie?

Imagine you are organizing words in a **dictionary**. Instead of storing words in a list, you store them letter by letter, building paths. Each letter leads to the next letter of a word.

For example:

- You want to store the words: **cat**, **car**, and **can**.
- Instead of writing them as separate strings, you can share their common letters:
    - The first three letters **ca** are the same for all three words, so they share a branch.
    - From **ca**, there are different branches for **t** (for cat), **r** (for car), and **n** (for can).

This way, you create a tree-like structure where:

- **Each node represents a letter.**
- **A path from the root to a node represents a word or part of a word.**

###   
Key Concepts of Tries  

1. **Nodes**: Each node in a trie represents a single character of a string.
2. **Edges**: The edges between nodes represent the connection between consecutive characters in the strings.
3. **Root**: The root node is an empty node representing the start of all strings.
4. **Children**: Each node can have up to `k` children, where `k` is the number of possible characters (for example, in English lowercase letters, `k = 26`).
5. **End of Word**: A special marker is used at the end of a word to signify that a valid word ends at that node.

  

### →How does a Trie work?

Let’s look at a simple example:

- Words to store: **bat**, **bad**, **bag**
- In the Trie:
    - Start from the root (empty node).
    - Add **b**, which leads to **a**.
    - From **a**, create branches for **t**, **d**, and **g**.

Here’s a rough visual:

```CSS
       (root)
         |
         b
         |
         a
       / | \
      t  d  g
```

- The word **bat** is represented by the path from the root → b → a → t.
- Similarly, **bad** is root → b → a → d, and **bag** is root → b → a → g.

Example→

```CSS
                      (root)
                      /   \
                     c     b
                    /|     | \
                   a a     a  a
                  /|  \    |  | \
                 t r   p   t  r  g
```

### How it works:

- **cat** is stored by following the path: root → c → a → t.
- **car** is stored by following the path: root → c → a → r.
- **bat** is stored by following the path: root → b → a → t.

  

### Why use a Trie?

1. **Efficient searching**: Finding whether a word exists is fast because you follow the path letter by letter. Instead of scanning through a list of words, you just check if the path exists.

→SO BASICALLY YAHAN MAIN PATHS BANATA HUON,LIKE PATH ROOT SE SHURU HOTA HAIN AND END HOTA HAI LAST WORD PAR JO KI FLAG SE SIGNIFY HOTA HAI

1. **Prefix searching**: Tries are great for finding all words that start with a certain prefix. For example, if you want to find all words starting with "ba", you can just follow the path from **b → a**, and then explore the words underneath.

  

### Use Cases:

- **Autocomplete**: When you start typing in a search bar and it suggests words, a Trie could be used to quickly find all the words that match the letters you’ve typed.
- **Spell-checking**: Checking if a word is spelled correctly can be done efficiently by searching through the Trie.

---

→TRIE DATA STRUCTURE BASICALLY EK CLASS HOTI HAI

→ HERE WE’RE ASSUMING EVERY CHARACTER IS OF LOWER ALPAHBET

→ TERE WILL ALWAYS BE A ROOT IN THE TRIE DATA STRUCTURE

### Trie Node Structure

Each node in the Trie will store:

- **Children nodes** (for each letter of the alphabet, we can use an array of size 26).
- A **flag** to mark the end of a word.

### What is `TrieNode`?

A `TrieNode` is a building block of the **Trie** data structure. Each node (or point) in the Trie stores part of a word and links to other nodes that store the next letters of that word. The node also helps us figure out if we've reached the end of a word.

### Key Components of the `TrieNode` class:

1. `**TrieNode* children[26];**`:
    - This is an **array** of pointers. Each pointer can point to another `TrieNode`, which represents the next letter in the word.
    - The size of the array is 26 because we are assuming we are working with **lowercase English letters** (a to z), and there are 26 letters in the alphabet.
    - Each position in the array corresponds to a letter:
        - Index 0 = 'a'
        - Index 1 = 'b'
        - Index 2 = 'c'
        - ... up to Index 25 = 'z'.
    - So, if a node has the letter 'b' and you want to find what comes after it, you check its pointer at position `1` (because 'b' is the second letter). **So we just have to do idx =ch-’a’ to get the index**
2. `**bool isEndOfWord;**`:
    - This is a **flag** (a true/false value) that tells us if this node marks the **end of a valid word**.
    - For example, in the word **cat**, the node for 't' would have `isEndOfWord = true`, meaning "this is the last letter of a word."
    - If it's `false`, it means the node is part of a word but not the end of one.
3. **Constructor:** `**TrieNode()**`:
    - This is the **constructor**, a special function that runs when you create a new `TrieNode`.
    - What does it do?
        - It sets `isEndOfWord` to `false`, meaning the node doesn’t end a word by default.
        - It also initializes the `children` array by setting each pointer in the array to `nullptr` (meaning, by default, this node doesn’t have any children yet).

### In layman terms, what does this code do?

- **Each** `**TrieNode**` **represents a letter**.
- The `**children[26]**` array allows each node to link to the next possible letters in the alphabet.
- The `**isEndOfWord**` tells us if we’ve reached the end of a valid word at this node.
- The **constructor** just sets up the node to be empty initially: no children and not marking the end of a word yet.

Think of it like a **branch of a tree**. Each node is like a junction on that branch:

- It may lead to several more branches (through the `children` array).
- It can also mark the **end** of a word (using `isEndOfWord`).

### Main Operations

1. **Insert** a word into the Trie.
2. **Search** for a word in the Trie.
3. **Prefix search** to find if any word starts with a given prefix.

  

## NOW IMPLEMENTATION

[https://www.naukri.com/code360/problems/implement-trie_631356?leftPanelTabValue=PROBLEM](https://www.naukri.com/code360/problems/implement-trie_631356?leftPanelTabValue=PROBLEM)

```CSS
/*
    Your Trie object will be instantiated and called as such:
    Trie* obj = new Trie();
    obj->insert(word);
    bool check2 = obj->search(word);
    bool check3 = obj->startsWith(prefix);
 */
class trieNode{
    public:
    trieNode*links[26];  // In case if there is a reference present at a certain index
    bool flag;           // then that surely means, that element is present there 
     
    trieNode(){
        for(int i=0;i<26;i++){
           this->links[i]=nullptr;
            this->flag=false;
        }
    }
    bool containskey(char ch){
       return this->links[ch-'a']!=nullptr;
    }
    void put(trieNode*temp,char ch){
     this->links[ch-'a']=temp;
   }
   trieNode*get(char ch){
       return this->links[ch-'a'];
   }
   void setend(){
       this->flag=true;
   }
};

class Trie {
    private:
    trieNode*root;
public:

    /** Initialize your data structure here. */
    Trie() {
        root=new trieNode();

    }

    /** Inserts a word into the trie. */
    void insert(string word) {
        trieNode*temp=root;
        for(int i=0;i<word.size();i++){
            if(temp->containskey(word[i])){
                temp= temp->get(word[i]);
            }else{
               temp->put(new trieNode(),word[i]);
               temp= temp->get(word[i]);
            }
            
        }
        temp->setend();
    }

    /** Returns if the word is in the trie. */
    bool search(string word) {
        trieNode*temp=root;
        for(int i=0;i<word.size();i++){
            if(temp->containskey(word[i])){
               temp= temp->get(word[i]);
            }else{
                return false;
           }

        }
        if(!temp->flag){
            return false;
        }
        return true;

    }

    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string prefix) {
        trieNode*temp=root;
        for(int i=0;i<prefix.size();i++){
            char ch=prefix[i];
            if(temp->containskey(prefix[i])){
             temp= temp->get(prefix[i]);
            }else{
                return false;
            }
        }
       
      return true;
    }
};
```

  

[https://www.naukri.com/code360/problems/implement-trie_1387095?leftPanelTabValue=PROBLEM](https://www.naukri.com/code360/problems/implement-trie_1387095?leftPanelTabValue=PROBLEM)

ERASE FUNCTION DIKKAT DE RAHA HAI

```CSS
\#include <bits/stdc++.h> 
class trieNode{
public:
 trieNode*links[26];
 int ew;
 int pn;
 trieNode(){
     for(int i=0;i<26;i++){
         links[i]=nullptr;
     }
     ew=0;
     pn=0;
 }

};
class Trie{
    private:
    trieNode*root;
    public:

    Trie(){
        // Write your code here.
        root=new trieNode();
    }

    void insert(string &word){
        // Write your code here.
        trieNode*temp=root; // starting hamesha root se hoti hai ye bat pkki hai
        for(int i=0;i<word.size();i++){
            char ch=word[i];
            if(temp->links[ch-'a']==nullptr){  // vahan koi refrence nahi hai mtlb insert karo
               temp->links[ch-'a']=new trieNode();
               temp=temp->links[ch-'a'];
               temp->pn++;
            }else{
               temp=temp->links[ch-'a'];
               temp->pn++;

            }
        }
        temp->ew++;
        temp->pn++;
    }

    int countWordsEqualTo(string &word){
        // Write your code here.
        trieNode*temp=root; // starting hamesha root se hoti hai ye bat pkki hai
        for(int i=0;i<word.size();i++){
            char ch=word[i];
            if(temp->links[ch-'a']==nullptr){  // vahan koi refrence nahi hai mtlb insert karo
               return 0;
            }else{
               temp=temp->links[ch-'a'];
               }
        }
        return temp->ew;
    }

    int countWordsStartingWith(string &word){
        // Write your code here.
         trieNode*temp=root; // starting hamesha root se hoti hai ye bat pkki hai
        for(int i=0;i<word.size();i++){
            char ch=word[i];
            if(temp->links[ch-'a']==nullptr){  // vahan koi refrence nahi hai mtlb insert karo
               return 0;
            }else{
               temp=temp->links[ch-'a'];
               }
        }
        return temp->pn;

    }

    void erase(string &word){
        // Write your code here.
        trieNode* temp = root;
        for (char ch : word) {
            trieNode* next = temp->links[ch - 'a'];
            next->pn--;
            if (next->pn == 0) {
                delete next;
                temp->links[ch - 'a'] = nullptr;
                return;
            }
            temp = next;
        }
        temp->ew--;
    }
   
};
```

  

[https://www.naukri.com/code360/problems/complete-string_2687860](https://www.naukri.com/code360/problems/complete-string_2687860)

REVISE KRNA YE ACHA SAWAL HAI YE