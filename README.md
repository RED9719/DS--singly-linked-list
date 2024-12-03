# DS--singly-linked-list
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None

    def traverse(self):
        current = self.head
        while current:
            print(current.data, end=" -> ")
            current = current.next
        print("None")

    def insert_at_beginning(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def insert_at_end(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last_node = self.head
        while last_node.next:
            last_node = last_node.next
        last_node.next = new_node

    def insert_at_position(self, position, data):
        if position < 0:
            print("Invalid position!")
            return
        new_node = Node(data)
        if position == 0:
            new_node.next = self.head
            self.head = new_node
            return
        current = self.head
        for _ in range(position - 1):
            if not current:
                print("Position out of bounds!")
                return
            current = current.next
        new_node.next = current.next
        current.next = new_node

    def delete_from_beginning(self):
        if not self.head:
            print("List is empty!")
            return
        self.head = self.head.next

    def delete_from_end(self):
        if not self.head:
            print("List is empty!")
            return
        if not self.head.next:
            self.head = None
            return
        second_last = self.head
        while second_last.next.next:
            second_last = second_last.next
        second_last.next = None

    def delete_from_position(self, position):
        if position < 0 or not self.head:
            print("Invalid position or list is empty!")
            return
        if position == 0:
            self.head = self.head.next
            return
        current = self.head
        for _ in range(position - 1):
            if not current.next:
                print("Position out of bounds!")
                return
            current = current.next
        if not current.next:
            print("Position out of bounds!")
            return
        current.next = current.next.next


if __name__ == "__main__":
    sll = SinglyLinkedList()
    sll.insert_at_beginning(10)
    sll.insert_at_end(20)
    sll.insert_at_end(30)
    sll.insert_at_position(1, 15)
    print("Linked List after insertion:")
    sll.traverse()

    sll.delete_from_beginning()
    print("\nLinked List after deletion from beginning:")
    sll.traverse()

    sll.delete_from_end()
    print("\nLinked List after deletion from end:")
    sll.traverse()

    sll.delete_from_position(1)
    print("\nLinked List after deletion from position 1:")
    sll.traverse()

