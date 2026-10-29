# Pseudocode: Binary Search Tree (BST)

Values smaller than a node go to its left subtree; larger values go to its right subtree. Duplicate values are ignored.

## INSERT

~~~text
ALGORITHM Insert(root, value)
    IF root = NULL THEN
        RETURN CREATE_NODE(value)
    END IF
    IF value < root.data THEN
        root.left ← Insert(root.left, value)
    ELSE IF value > root.data THEN
        root.right ← Insert(root.right, value)
    END IF
    RETURN root
END ALGORITHM
~~~

## SEARCH

~~~text
ALGORITHM Search(root, key)
    current ← root
    WHILE current ≠ NULL
        IF current.data = key THEN
            RETURN current
        ELSE IF key < current.data THEN
            current ← current.left
        ELSE
            current ← current.right
        END IF
    END WHILE
    RETURN NULL
END ALGORITHM
~~~

## INORDER TRAVERSAL

~~~text
ALGORITHM Inorder(root)
    IF root ≠ NULL THEN
        Inorder(root.left)
        OUTPUT root.data
        Inorder(root.right)
    END IF
END ALGORITHM
~~~

Inorder traversal outputs values in ascending order.

**Time:** Average O(log n) per insertion/search in a balanced tree; worst case O(n). **Recursion space:** O(h), where h is tree height.
