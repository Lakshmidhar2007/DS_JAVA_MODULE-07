# Ex 10 : Flattening a Nested List Using an Iterator

## DATE: 20/09/2026

## AIM:

To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).

## Algorithm

1. Create a `NestedIterator` class to store and process the nested list.
2. Recursively traverse each element of the nested list.
3. If the element is an integer, add it to a flat list.
4. If the element is another nested list, recursively process its elements.
5. Use `hasNext()` and `next()` to access and display the flattened integers sequentially.

## Program:

```java
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: LAKSHMIDHAR N
RegisterNumber:  212224230138
*/

import java.util.*;

public class Main {

    interface NestedInteger {
        boolean isInteger();
        Integer getInteger();
        List<NestedInteger> getList();
    }

    static class MyNestedInteger implements NestedInteger {
        private Integer value;
        private List<NestedInteger> list;

        MyNestedInteger(int value) {
            this.value = value;
        }

        MyNestedInteger(List<NestedInteger> list) {
            this.list = list;
        }

        public boolean isInteger() {
            return value != null;
        }

        public Integer getInteger() {
            return value;
        }

        public List<NestedInteger> getList() {
            return list;
        }
    }

    static class NestedIterator implements Iterator<Integer> {
        private List<Integer> flatList = new ArrayList<>();
        private int index = 0;

        NestedIterator(List<NestedInteger> nestedList) {
            flatten(nestedList);
        }

        private void flatten(List<NestedInteger> list) {
            for (NestedInteger item : list) {
                if (item.isInteger()) {
                    flatList.add(item.getInteger());
                } else {
                    flatten(item.getList());
                }
            }
        }

        public Integer next() {
            return flatList.get(index++);
        }

        public boolean hasNext() {
            return index < flatList.size();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        List<NestedInteger> nestedList = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            int value = sc.nextInt();
            nestedList.add(new MyNestedInteger(value));
        }

        NestedIterator iterator = new NestedIterator(nestedList);

        while (iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }
    }
}
```

## Output:

<img width="390" height="115" alt="image" src="https://github.com/user-attachments/assets/1f4b5251-ddea-4ef4-9c96-ce2af223ad61" />


## Result:

The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
