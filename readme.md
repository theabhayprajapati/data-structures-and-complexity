<!-- almost all datastructures and how to make them. 

-> time complexity of data structures.
-> space complexity of data structures.
-> how to make them.
-> how to use them.
-> in which situation to use them.
-> main purpose for using that data structure.
-->

# Data Structures
## Arrays
### Time Complexity
| Operation | Time Complexity |
| --- | --- |
| Access | O(1) |
| Search | O(n) |
| Insertion | O(1) |
| Deletion | -- |

### How to make them
```c++
int arr[10];
```

### Main purpose
To store data in a linear fashion, when you are having the idea of the size of the array.


## Array Lists  
better than arrays, because they can grow and shrink dynamically, gives ability to delete and insert elements in the at any index of arrray.
### Time Complexity

| Operation | Time Complexity |
| --- | --- |
| Access | O(1) |
| Search | O(n) |
| Insertion | O(n) |
| Deletion | O(n) |

### How to make them
```c++
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4, 5};   
}
```
<!-- java -->
```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();
        list.add(1);
        list.add(2);
        list.add(3);
        list.add(4);
        list.add(5);
    }
}

```

### Main purpose
To store data in a linear fashion, when you are not having the idea of the size of the array, and you want to add or remove elements dynamically.

## Linked Lists
### Time Complexity

| Operation | Time Complexity |
| --- | --- |
| Access | O(n) |
| Search | O(n) |
| Insertion | O(1) |
| Deletion | O(1) |

The reason for the time complexity for insertion is O(1) becuase if you have the address of the previous node, you can insert the new node in O(1) time.
However with arrays it's not possible, because you have to shift all the elements to the right, which takes O(n) time if you have to shift at the beginning elements.

### How to make them
```c++
#include <iostream>
using namespace std;

Struct Node {
    int data;
    Node* next;
};

int main() {
    Node* head = new Node();
    head->data = 1;
    head->next = NULL;
    
    Node* second = new Node();
    second->data = 2;
    second->next = NULL;
    
    head->next = second;
    /* third after head */

    Node* third = new Node();
    third->data = 3;
    third->next = NULL;

    // so inserting a node it took O(1) time.
    head->next = third;
    third->next = second;
    /* delte third */
    head->next = second;
    delete third;
    // so deleting a node it took O(1) time.

}

```
<!-- java -->
```java
import java.util.LinkedList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = new LinkedList<>();
        list.add(1);
        list.add(2);
        list.add(3);
        list.add(4);
        list.add(5);
    }
}

```

### Main purpose
It's beneifical when access elements on time is required and and also you space limits, also if you want to insert or delete elements in O(1) time, this is better than arrays.

## Stacks
### Time Complexity

| Operation | Time Complexity |
| --- | --- |
| Access | O(n) |
| Search | O(n) |
| Insertion | O(1) |
| Deletion | O(1) |

### How to make them
```c++
#include <iostream>
#include <stack>
using namespace std;

int main(){
    stack<int> s = {1, 2, 3, 4, 5};
    s.push(6);
    s.pop();
}
```
<!-- java -->
```java
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        stack.push(4);
        stack.push(5);
        stack.pop();
    }
}

```

### Main purpose
---

## Queues
### Time Complexity

| Operation | Time Complexity |
| --- | --- |
| Access | O(n) |
| Search | O(n) |
| Insertion | O(1) |
| Deletion | O(1) |

### How to make them
```c++
#include <iostream>
#include <queue>
using namespace std;
int main(){
    queue<int> q = {1, 2, 3, 4, 5};
    q.push(6);
    q.pop();
}
```
<!-- java -->
```java
import java.util.Queue;
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();
        queue.add(1);
        queue.add(2);
        queue.add(3);
        queue.add(4);
        queue.add(5);
        queue.remove();
    }
}

```

### Main purpose
When to want to perform operations in a order, without removing the elements, you can use queues.
---

## Trees

## BST 🌲 (Binary Search Tree)
### Time Complexity

| Operation | Time Complexity |
| --- | --- |
| Access | O(log n) |
| Search | O(log n) |
| Insertion | O(log n) |
| Deletion | O(log n) |

### How to make them
```c++
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

Node* getNewNode(int data) {
    Node* newNode = new Node();
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}

Node* insert(Node* root, int data) {
    if (root == NULL) {
        root = getNewNode(data);
    } else if (data <= root->data) {
        root->left = insert(root->left, data);
    } else {
        root->right = insert(root->right, data);
    }
    return root;
}

bool search(Node* root, int data) {
    if (root == NULL) return false;
    else if (root->data == data) return true;
    else if (data <= root->data) return search(root->left, data);
    else return search(root->right, data);
}

int main() {
    Node* root = NULL;
    root = insert(root, 15);
    root = insert(root, 10);
    root = insert(root, 20);
    root = insert(root, 25);
    root = insert(root, 8);
    root = insert(root, 12);
    int number;
    cout << "Enter number be searched\n";
    cin >> number;
    if (search(root, number) == true) cout << "Found\n";
    else cout << "Not Found\n";
}
```
<!-- java -->
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        BST bst = new BST();
        bst.insert(15);
        bst.insert(10);
        bst.insert(20);
        bst.insert(25);
        bst.insert(8);
        bst.insert(12);
        System.out.println("Enter number be searched");
        int number = sc.nextInt();
        if (bst.search(number)) System.out.println("Found");
        else System.out.println("Not Found");
    }
}

```

### Main purpose
When wanted to array  data in sorted and fast way, you can use BST.
Also in hierarchical data, you can use BST.
---

## Hash Tables
### Time Complexity

| Operation | Time Complexity |
| --- | --- |
| Access | O(1) |
| Search | O(1) |
| Insertion | O(1) |
| Deletion | O(1) |

worst case is O(n) for all operations.

### How to make them
```c++
#include <iostream>
#include <unordered_map>
using namespace std;
int main() {
    unordered_map<string, int> ourmap = {
        {"abc", 1},
        {"def", 2},
        {"ghi", 3},
        {"jkl", 4},
        {"mno", 5}
    };
}

```
<!-- java -->
```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, Integer> map = new HashMap<>();
        map.put("abc", 1);
        map.put("def", 2);
        map.put("ghi", 3);
        map.put("jkl", 4);
        map.put("mno", 5);
    }
}

```

### Main purpose
When you want to store data in key-value pairs, you can use hash tables.
---
<!-- write a hashfunction -->

## Graphs
### Time Complexity


