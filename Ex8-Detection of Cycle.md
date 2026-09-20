# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List

## DATE: 20/09/2026

## AIM:

To write a program that detects a cycle in a linked list and returns the node where the cycle begins. If there is no cycle, the program should return null without modifying the linked list.

## Algorithm

1. Create a singly linked list and read the position where the cycle should be connected.
2. Use two pointers, `slow` and `fast`, to detect whether a cycle exists.
3. Move `slow` one step and `fast` two steps until they meet or `fast` reaches the end.
4. If they meet, move one pointer to the head and move both pointers one step until they meet again.
5. The meeting node is the starting node of the cycle; if no cycle exists, return null.

## Program:

```java
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
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

    static Node detectCycle(Node head) {
        Node slow = head;
        Node fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                slow = head;

                while (slow != fast) {
                    slow = slow.next;
                    fast = fast.next;
                }

                return slow;
            }
        }

        return null;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (n == 0) {
            System.out.println("No Cycle");
            return;
        }

        Node[] nodes = new Node[n];

        for (int i = 0; i < n; i++) {
            nodes[i] = new Node(sc.nextInt());
        }

        for (int i = 0; i < n - 1; i++) {
            nodes[i].next = nodes[i + 1];
        }

        int pos = sc.nextInt();

        if (pos >= 0 && pos < n) {
            nodes[n - 1].next = nodes[pos];
        }

        Node cycleStart = detectCycle(nodes[0]);

        if (cycleStart != null)
            System.out.println(cycleStart.data);
        else
            System.out.println("No Cycle");
    }
}
```

## Output:

<img width="422" height="167" alt="image" src="https://github.com/user-attachments/assets/1f4e3326-104e-465a-914a-0a32205a61f7" />


## Result:

The program successfully detects whether a cycle exists in the linked list. If a cycle is present, it correctly identifies and returns the node where the cycle begins.
