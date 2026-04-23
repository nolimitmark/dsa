# **Building A Doubly Linked List**

In this course, we’ll focus on building a doubly linked list through hands-on coding. We won’t dive into analyzing time and space complexities or writing algorithms, as we’ve already covered those concepts in the Introduction to Linked Lists course. Make sure to review that course first if you haven’t already. The operations we will implement in our linked list include:

1. Traversal
2. Searching
3. Appending
4. Insertion
5. Deletion
6. Cycle Detection

## **Creating the Node Object**

The Node object will represent each element in the doubly linked list. It will be defined as follows:

```python
class Node:
    def __init__(self, data, prev=None, next=None):
        self.prev = prev  # Reference to the previous node
        self.data = data  # Data stored in the node
        self.next = next  # Reference to the next node
```

## **Creating the Doubly Linked List Class**

The `DoublyLinkedList` class will manage the linked list operations. It will be defined as follows:

```python
class SinglyLinkedList:
    def __init__(self):
        self.head = None  # The head of the linked list, initially set to None
```

This class initializes the linked list with a `head` attribute, which points to the first node. If the list is empty, the `head` will be `None`.

## **Implementing The Traversal Function**

The traversal function allows us to visit and print the data of each node in the linked list. It can be implemented as follows:

```python
def traverse(self):
    current_node = self.head  # Start from the head of the list

    while current_node:  # Continue until we reach the end of the list
        print(current_node.data)  # Print the data of the current node
        current_node = current_node.next  # Move to the next node
```

This function begins at the head node and iterates through the list, printing the data of each node until it reaches the end (where `current_node` becomes `None`).

## **Implementing The Search Function**

The search function looks for a specific value in the linked list. It can be implemented as follows:

```python
def search(self, target):
    current_node = self.head  # Start from the head of the list
    
    while current_node:  # Continue until the end of the list
        if current_node.data == target:  # Check if the current node's data matches the target
            return True  # Return True if the target is found
        current_node = current_node.next  # Move to the next node
    
    return False  # Return False if the target is not found
```

This function starts at the head node and iterates through the list, checking each node's data against the target. If a match is found, it returns `True`. If the traversal reaches the end without finding the target, it returns `False`.

## **Implementing The Append Function**

The append function adds a new node with the specified data to the end of the linked list. It can be implemented as follows:

```python
def append(self, data):
    if self.head is None:
        self.head = Node(data)  # Create the head node if the list is empty
    else:
        current_node = self.head
        while current_node.next:  # Traverse to the last node
            current_node = current_node.next
        
        new_node = Node(data=data, prev=current_node)  # Create a new node
        current_node.next = new_node  # Link the last node to the new node
```

In this implementation, if the list is empty, a new head node is created. If not, the function traverses to the last node and links it to the new node, ensuring that the `prev` pointer of the new node correctly references the current last node.

## **Implementing The Insert Function**

The insert function adds a new node with the specified data at a given index in the linked list. It can be implemented as follows:

```python
def insert(self, index, data):
    if index == 0:  # Insert at the head
        new_node = Node(data=data, prev=None, next=self.head)
        if self.head:  # If the list is not empty, update the previous head's prev pointer
            self.head.prev = new_node
        self.head = new_node  # Update head to the new node
    else:
        current_node = self.head
        
        for i in range(index - 1):  # Traverse to the node just before the target index
            current_node = current_node.next

        next_node = current_node.next  # Store the node currently at the target index
        new_node = Node(data=data, prev=current_node, next=next_node)  # Create the new node
        if next_node:  # Update the next node's prev pointer if it exists
            next_node.prev = new_node
        current_node.next = new_node  # Link the current node to the new node
```

In this implementation, if the index is `0`, the new node is inserted at the head, and the head is updated. If the index is greater than `0`, the function traverses to the node just before the specified index, creates the new node, and properly updates the pointers of the surrounding nodes. An error is raised if the index is out of bounds.

## **Implementing The Delete Function**

The delete function removes a node at a specified index from the linked list. It can be implemented as follows:

```python
def delete(self, index):
    if index == 0:  # Delete the head node
        if self.head:  # Check if the list is not empty
            self.head = self.head.next
            if self.head:  # Update the new head's prev pointer if the list is not empty
                self.head.prev = None
    else:
        current_node = self.head
        
        for i in range(index - 1):  # Traverse to the node just before the target index
            current_node = current_node.next

        node_to_delete = current_node.next  # The node to be deleted
        if node_to_delete:  # Check if the node to delete exists
            new_next_node = node_to_delete.next  # Store the node after the one to delete
            current_node.next = new_next_node  # Link the current node to the new next node
            if new_next_node:  # Update the new next node's prev pointer if it exists
                new_next_node.prev = current_node
```

In this implementation, if the index is `0`, the head node is removed, and the new head is updated. If the index is greater than `0`, the function traverses to the node just before the specified index, and then updates the pointers accordingly to remove the targeted node. An error is raised if the index is out of bounds.

## **Implementing The Cycle Detection Function**

The cycle detection function checks if a linked list contains a cycle. It can be implemented as follows:

```python
def containsCycle(self):
    visited = set()  # Initialize a set to keep track of visited nodes
    
    current_node = self.head  # Start from the head of the list
    while current_node:  # Continue until the current node is None
        if current_node in visited:  # Check if the current node has been visited
            return True  # A cycle is detected

        visited.add(current_node)  # Add the current node to the visited set
        current_node = current_node.next  # Move to the next node
    
    return False  # No cycle found
```

In this function, we traverse the linked list while maintaining a set of visited nodes. If we encounter a node that has already been visited, it indicates the presence of a cycle, and the function returns `True`. If the end of the list is reached without finding a cycle, the function returns `False`.

## **Putting It Altogether**

```python
class Node:
    def __init__(self, data, prev=None, next=None):
        self.prev = prev
        self.data = data
        self.next = next

class DoublyLinkedList:
    def __init__(self):
        self.head = None

    def traverse(self):
        current_node = self.head

        while current_node:
            print(current_node.data)
            current_node = current_node.next
    
    def search(self, target):
        current_node = self.head

        while current_node:
            if current_node.data == target:
                return True
            current_node = current_node.next

        return False
    
    def append(self, data):
        if self.head is None:
            self.head = Node(data)
        else:
            current_node = self.head
            while current_node.next:
                current_node = current_node.next
            
            new_node = Node(data=data, prev=current_node)
            current_node.next = new_node
        
    def insert(self, index, data):
        if index == 0:
            new_node = Node(data=data, prev=None, next=self.head)
            if self.head:
                self.head.prev = new_node
            self.head = new_node
        else:
            current_node = self.head
            
            for i in range(index - 1):
                current_node = current_node.next

            next_node = current_node.next
            new_node = Node(data=data, prev=current_node, next=next_node)
            if next_node:
                next_node.prev = new_node
            current_node.next = new_node
        
    def delete(self, index):
        if index == 0:
            if self.head:
                self.head = self.head.next
                if self.head:
                    self.head.prev = None
        else:
            current_node = self.head
            
            for i in range(index - 1):
                current_node = current_node.next

            node_to_delete = current_node.next
            if node_to_delete:
                new_next_node = node_to_delete.next
                current_node.next = new_next_node
                if new_next_node:
                    new_next_node.prev = current_node
                
    
    def containsCycle(self):
        visited = set()
        
        current_node = self.head
        while current_node.next:
            if current_node.next in visited:
                return True

            visited.add(current_node)
            current_node = current_node.next
        
        return False
```

This implementation assumes the list size is known, ensuring that a valid index is always provided to the `insert` and `delete` functions.