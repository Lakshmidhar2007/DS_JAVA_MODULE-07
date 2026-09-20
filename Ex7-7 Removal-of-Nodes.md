# Ex7 Removal of Nodes with a Specific Value from a Linked List

## DATE: 20/09/2026

## AIM:

To write a java program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm

1. Create a singly linked list with the given elements.
2. Read the value `val` that needs to be removed.
3. Remove nodes from the beginning while their value matches `val`.
4. Traverse the remaining list and remove every node whose value matches `val`.
5. Display the modified linked list.

## Program:

```java
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: LAKSHMIDHAR N
RegisterNumber:  212224230138
*/

import java.util.*;

public class Main {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    static Node removeElements(Node head, int val) {
        while (head != null && head.data == val) {
            head = head.next;
        }

        Node current = head;

        while (current != null && current.next != null) {
            if (current.next.data == val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }

        return head;
    }

    static void display(Node head) {
        while (head != null) {
            System.out.print(head.data + " ");
            head = head.next;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        Node head = null;
        Node tail = null;

        for (int i = 0; i < n; i++) {
            Node newNode = new Node(sc.nextInt());

            if (head == null) {
                head = newNode;
                tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }

        int val = sc.nextInt();

        head = removeElements(head, val);

        display(head);
    }
}
```

## Output:

<img width="457" height="147" alt="image" src="https://github.com/user-attachments/assets/4b2ddba2-9242-4dcf-9ac8-4ea7adb26bd3" />


## Result:

The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
