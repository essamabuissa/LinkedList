# LinkedList

1.First we will create a class for a single Node of a linked list .
Models two attributes - data and the link to the next node in the list

```python

class Node:
    data = None
    next_node = None

    def __init__(self,data):
        self.data = data

```

2.We will make a method to convert the value from what the memory shows into a string to make it readable .

```python

def __repr__(self):
        return "<Node data: %s>" % self.data

```

3.We will make a Class for the Singly Linked List.

```python

class LinkedList:

    def __init__(self):
        self.head = None


```

4.We need to check if the list is empty , so we will create a method to check that .

```python

def is_empty(self):
        return self.head == None #Here we are checking if the head is none , so if its none this condition will evaluate to True which indicates that the list is empty

```

5.So we need to visit every node to determine the size, that means that returns the number of nodes in the list takes 0(n) time.

```python

def size(self):
        current = self.head
        count = 0

        while current: #its the same as current != None
            count += 1
            current = current.next_node #Once we get to the tail , the current will equals to None , and the while loop will terminate
        return count

```

6.We will add the new node as the head of the list and pointing the old head.

```python

def add(self, data):
        # Creating a new Node to hold the data
        new_node = Node(data)

        """
        Adding the new node as the head of the list and pointing the old head ,
        if there's no node at the head this correctly sets next node to None
        """
        new_node.next_node = self.head
        self.head = new_node

```

7.We will add a new method that returns a string representaition of the list.

```python

def __repr__(self):
  """
  Returns a string representation of the list.

  """

  nodes = []
  current = self.head


  while current:
    if current is self.head:
      nodes.append("[Head: %s]" % current.data)
    elif current.next_node is None:
      nodes.append("[Tail: %s]" % current.data)
    else:
      nodes.append("[%s]" % current.data)

    current = current.next_node

  return '-> '.join(nodes)


```

8.We will search for the first node that contains a data that matches the key , and it will return None if not found, so we will add this search method

```python

 def search(self, key):
        current = self.head

        while current:
            if current.data == key:
                return current
            else:
                current = current.next_node
        return None

```

9.Inserting a new Node containing data at index position

```python

def insert(self, data, index):
        if index == 0:
            self.add(data)

        if index > 0:
            new = Node(data)

            position = index
            current = self.head

            while position > 1:
                current = Node.next_node
                position -= 1

            prev_node = current
            next_node = current.next_node

            prev_node.next_node = new
            new.next_node = next_node

```

10.Removing node containing data that matches the key by adding this method.

```python

def remove(self, key):
        current = self.head
        previous = None
        found = False

        while current and not found:
            if current.data == key and current is self.head:
                found = True
                self.head = current.next_node
            elif current.data == key:
                found = True
                previous.next_node = current.next_node
            else:
                previous = current
                current = current.next_node

        return current

```
