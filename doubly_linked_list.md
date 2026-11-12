# Pseudocode: Doubly Linked List Operations

Each node stores data, prev, and next. Initialize head ← NULL.

## INSERT AT BEGINNING

~~~text
ALGORITHM InsertFront(head, value)
    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.prev ← NULL
    node.next ← head
    IF head ≠ NULL THEN
        head.prev ← node
    END IF
    head ← node
    RETURN head
END ALGORITHM
~~~

## INSERT AT END

~~~text
ALGORITHM InsertEnd(head, value)
    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.next ← NULL
    IF head = NULL THEN
        node.prev ← NULL
        RETURN node
    END IF

    current ← head
    WHILE current.next ≠ NULL
        current ← current.next
    END WHILE
    current.next ← node
    node.prev ← current
    RETURN head
END ALGORITHM
~~~

## DELETE BY VALUE

~~~text
ALGORITHM DeleteValue(head, key)
    current ← head
    WHILE current ≠ NULL AND current.data ≠ key
        current ← current.next
    END WHILE
    IF current = NULL THEN
        OUTPUT "Value not found"
        RETURN head
    END IF

    IF current.prev ≠ NULL THEN
        current.prev.next ← current.next
    ELSE
        head ← current.next
    END IF
    IF current.next ≠ NULL THEN
        current.next.prev ← current.prev
    END IF
    FREE current
    RETURN head
END ALGORITHM
~~~

## DISPLAY FORWARD

~~~text
ALGORITHM DisplayForward(head)
    current ← head
    WHILE current ≠ NULL
        OUTPUT current.data
        current ← current.next
    END WHILE
END ALGORITHM
~~~

## DISPLAY BACKWARD

~~~text
ALGORITHM DisplayBackward(head)
    IF head = NULL THEN
        RETURN
    END IF
    current ← head
    WHILE current.next ≠ NULL
        current ← current.next
    END WHILE
    WHILE current ≠ NULL
        OUTPUT current.data
        current ← current.prev
    END WHILE
END ALGORITHM
~~~

**Time:** Traversal/search O(n); insertion at beginning O(1).

## C implementation

~~~c
#include <stdio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node *rlink, *llink;
};

struct node *head = NULL, *ptr = NULL, *temp = NULL;

int item, key;

void insertFirst();
void insertLast();
void insertKey();
void deleteFirst();
void deleteLast();
void deleteKey();
void display();
void display1();

int main(void)
{
    int n;

    printf("Menu:\n");
    printf("1. Insert at first\n");
    printf("2. Insert at last\n");
    printf("3. Insert after a key\n");
    printf("4. Delete from the front\n");
    printf("5. Delete from the end\n");
    printf("6. Delete a key\n");
    printf("7. Display forward\n");
    printf("8. Display reverse\n");
    printf("9. Exit\n");

    do
    {
        printf("\nEnter the choice: ");

        if (scanf("%d", &n) != 1)
        {
            printf("Invalid input\n");
            return 1;
        }

        switch (n)
        {
            case 1:
                insertFirst();
                break;

            case 2:
                insertLast();
                break;

            case 3:
                insertKey();
                break;

            case 4:
                deleteFirst();
                break;

            case 5:
                deleteLast();
                break;

            case 6:
                deleteKey();
                break;

            case 7:
                display();
                break;

            case 8:
                display1();
                break;

            case 9:
                printf("Have a nice day!\n");
                break;

            default:
                printf("Invalid operation\n");
        }

    } while (n != 9);

    return 0;
}

/* Insert at the beginning */
void insertFirst()
{
    temp = malloc(sizeof(struct node));

    if (temp == NULL)
    {
        printf("Memory allocation failed\n");
        return;
    }

    printf("Enter the element to be inserted: ");
    if (scanf("%d", &item) != 1)
    {
        free(temp);
        printf("Invalid input\n");
        return;
    }

    temp->data = item;
    temp->llink = NULL;
    temp->rlink = head;

    if (head != NULL)
    {
        head->llink = temp;
    }

    head = temp;

    printf("The current status is:\n");
    display();
}

/* Insert at the end */
void insertLast()
{
    temp = malloc(sizeof(struct node));

    if (temp == NULL)
    {
        printf("Memory allocation failed\n");
        return;
    }

    printf("Enter the element to be inserted: ");
    if (scanf("%d", &item) != 1)
    {
        free(temp);
        printf("Invalid input\n");
        return;
    }

    temp->data = item;
    temp->rlink = NULL;

    if (head == NULL)
    {
        temp->llink = NULL;
        head = temp;
    }
    else
    {
        ptr = head;

        while (ptr->rlink != NULL)
        {
            ptr = ptr->rlink;
        }

        temp->llink = ptr;
        ptr->rlink = temp;
    }

    printf("The current status is:\n");
    display();
}

/* Insert after a specified key */
void insertKey()
{
    if (head == NULL)
    {
        printf("List is empty\n");
        return;
    }

    printf("Enter the element to be inserted: ");
    if (scanf("%d", &item) != 1)
    {
        printf("Invalid input\n");
        return;
    }

    printf("Enter the key: ");
    if (scanf("%d", &key) != 1)
    {
        printf("Invalid input\n");
        return;
    }

    ptr = head;

    while (ptr != NULL && ptr->data != key)
    {
        ptr = ptr->rlink;
    }

    if (ptr == NULL)
    {
        printf("Search fails: key not found\n");
        return;
    }

    temp = malloc(sizeof(struct node));

    if (temp == NULL)
    {
        printf("Memory allocation failed\n");
        return;
    }

    temp->data = item;
    temp->rlink = ptr->rlink;
    temp->llink = ptr;

    if (ptr->rlink != NULL)
    {
        ptr->rlink->llink = temp;
    }

    ptr->rlink = temp;

    printf("The current status is:\n");
    display();
}

/* Delete from the beginning */
void deleteFirst()
{
    if (head == NULL)
    {
        printf("List is empty\n");
        return;
    }

    ptr = head;

    printf("%d is deleted\n", ptr->data);

    head = head->rlink;

    if (head != NULL)
    {
        head->llink = NULL;
    }

    free(ptr);

    printf("The current status is:\n");
    display();
}

/* Delete from the end */
void deleteLast()
{
    if (head == NULL)
    {
        printf("List is empty\n");
        return;
    }

    ptr = head;

    while (ptr->rlink != NULL)
    {
        ptr = ptr->rlink;
    }

    printf("%d is deleted\n", ptr->data);

    if (ptr->llink != NULL)
    {
        ptr->llink->rlink = NULL;
    }
    else
    {
        head = NULL;
    }

    free(ptr);

    printf("The current status is:\n");
    display();
}

/* Delete a node containing the specified key */
void deleteKey()
{
    if (head == NULL)
    {
        printf("List is empty\n");
        return;
    }

    printf("Enter the data to be deleted: ");

    if (scanf("%d", &key) != 1)
    {
        printf("Invalid input\n");
        return;
    }

    ptr = head;

    while (ptr != NULL && ptr->data != key)
    {
        ptr = ptr->rlink;
    }

    if (ptr == NULL)
    {
        printf("Search fails: key not found\n");
        return;
    }

    printf("%d is deleted\n", ptr->data);

    if (ptr->llink != NULL)
    {
        ptr->llink->rlink = ptr->rlink;
    }
    else
    {
        head = ptr->rlink;
    }

    if (ptr->rlink != NULL)
    {
        ptr->rlink->llink = ptr->llink;
    }

    free(ptr);

    printf("The current status is:\n");
    display();
}

/* Display the list in forward order */
void display()
{
    if (head == NULL)
    {
        printf("List is empty\n");
        return;
    }

    ptr = head;

    while (ptr != NULL)
    {
        printf("%d\t", ptr->data);
        ptr = ptr->rlink;
    }

    printf("\n");
}

/* Display the list in reverse order */
void display1()
{
    if (head == NULL)
    {
        printf("List is empty\n");
        return;
    }

    ptr = head;

    /* Move to the last node */
    while (ptr->rlink != NULL)
    {
        ptr = ptr->rlink;
    }

    /* Traverse backward */
    while (ptr != NULL)
    {
        printf("%d\t", ptr->data);
        ptr = ptr->llink;
    }

    printf("\n");
}
~~~
