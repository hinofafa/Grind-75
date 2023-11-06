# Implement Trie (Prefix Tree)
![#ffa500](https://placehold.co/1x1/ffa500/ffa500.png) `Medium`

> A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:
- Trie() Initializes the trie object.
- void insert(String word) Inserts the string word into the trie.
- boolean search(String word) Returns true if the string word is in the trie (i.e., was inserted before), and false otherwise.
- boolean startsWith(String prefix) Returns true if there is a previously inserted string word that has the prefix prefix, and false otherwise.
 

Example 1:

> Input\
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]\
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]\
Output\
[null, null, true, false, true, null, true]\
\
Explanation\
Trie trie = new Trie();\
trie.insert("apple");\
trie.search("apple");   // return True\
trie.search("app");     // return False\
trie.startsWith("app"); // return True\
trie.insert("app");\
trie.search("app");     // return True
 
Constraints:
- $1$ <= word.length, prefix.length <= $2000$
- word and prefix consist only of lowercase English letters.
At most $3 * 10^4$ calls in total will be made to insert, search, and startsWith.

Problem can be found in [here](https://leetcode.com/problems/implement-trie-prefix-tree)!

### [Solution](</Trie/208-ImplementTrie(PrefixTree)/solution.py>): Hash Table

```python
class Trie:
    def __init__(self):
        self.memo = {}

    def insert(self, word: str) -> None:
        current_memo = self.memo
        for char in word:
            if char not in current_memo:
                current_memo[char] = {}

            current_memo = current_memo[char]

        current_memo["."] = None

    def search(self, word: str) -> bool:
        current_memo = self.memo
        for char in word:
            if char not in current_memo:
                return False

            current_memo = current_memo[char]

        return "." in current_memo

    def startsWith(self, prefix: str) -> bool:
        current_memo = self.memo
        for char in prefix:
            if char not in current_memo:
                return False

            current_memo = current_memo[char]

        return True
```

Time Complexity: $O(n)$, Space Complexity: $O(n)$, where n is the length of the word.
