# Ex6 Right Rotation LinkedList

## DATE: 20/09/2026

## AIM:

To write a Java program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.

## Algorithm

1. Create a singly linked list and insert the given elements.
2. Find the length of the linked list and calculate `k % length`.
3. Connect the last node to the head to form a circular linked list.
4. Find the new tail and new head, then break the circular link.
5. Display the rotated linked list.

## Program:

```java
/*
Program to Right Rotation LinkedList
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

    static Node rotateRight(Node head, int k) {
        if (head == null || head.next == null || k == 0)
            return head;

        Node tail = head;
        int length = 1;

        while (tail.next != null) {
            tail = tail.next;
            length++;
        }

        k = k % length;

        if (k == 0)
            return head;

        tail.next = head;

        int steps = length - k;
        Node newTail = head;

        for (int i = 1; i < steps; i++)
            newTail = newTail.next;

        Node newHead = newTail.next;
        newTail.next = null;

        return newHead;
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

        int k = sc.nextInt();

        head = rotateRight(head, k);
        display(head);
    }
}
```

## Output:

<img width="400" height="140" alt="image" src="https://github.com/user-attachments/assets/e3bcc8e4-152c-4099-8400-39b0ee80c365" />


## Result:

Thus, the Java program to perform right rotation on linked list is implemented successfully.
