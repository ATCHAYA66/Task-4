class LinkedList {
    Node head; // Head of the list
  // Node class
    static class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }
    // Function to insert a new node at the end
    public void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node temp = head;
        while (temp.next != null) {
            temp = temp.next;
        }
        temp.next = newNode;
    }

  // Function to delete the last occurrence of a given key
    public void deleteLastOccurrence(int key) {
        Node temp = head, lastOccurrence = null;
        Node prev = null, lastPrev = null;

// Traverse the list to find the last occurrence of the key
        while (temp != null) {
            if (temp.data == key) {
                lastOccurrence = temp;
                lastPrev = prev;
            }
            prev = temp;
            temp = temp.next;
        }

   // If the key is not found, return
        if (lastOccurrence == null) {
            System.out.println("Key not found in the list.");
            return;
        }

   // If the last occurrence is the head node
        if (lastOccurrence == head) {
            head = head.next;
        } else {
            lastPrev.next = lastOccurrence.next;
        }
    }

   // Function to print the linked list
    public void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " -> ");
            temp = temp.next;
        }
        System.out.println("NULL");
    }

   public static void main(String[] args) {
        LinkedList list = new LinkedList();

  // Insert elements into the linked list
        list.insert(1);
        list.insert(2);
        list.insert(3);
        list.insert(2);
        list.insert(4);
        list.insert(2);

System.out.println("Original List:");
        list.printList();

// Delete the last occurrence of 2
        list.deleteLastOccurrence(2);
        System.out.println("List after deleting last occurrence of 2:");
        list.printList();
    }
}
