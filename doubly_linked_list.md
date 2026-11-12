# Pseudocode: Doubly Linked List Operations

Each node stores `data`, a left link `llink` (previous node) and a right link `rlink` (next node). The list starts empty (`head ← NULL`). A menu is repeated until the user chooses Exit, and the list is displayed after every insertion or deletion.

## MAIN MENU

~~~text
ALGORITHM DoublyLinkedListMenu
    head ← NULL
    OUTPUT "1.Insert at first  2.Insert at last  3.Insert after a key"
    OUTPUT "4.Delete from the front  5.Delete from the end  6.Delete a key"
    OUTPUT "7.Display forward  8.Display reverse  9.Exit"

    REPEAT
        READ n
        IF input is not a number THEN
            OUTPUT "Invalid input"
            STOP
        END IF

        IF n = 1 THEN CALL InsertFirst
        ELSE IF n = 2 THEN CALL InsertLast
        ELSE IF n = 3 THEN CALL InsertKey
        ELSE IF n = 4 THEN CALL DeleteFirst
        ELSE IF n = 5 THEN CALL DeleteLast
        ELSE IF n = 6 THEN CALL DeleteKey
        ELSE IF n = 7 THEN CALL Display
        ELSE IF n = 8 THEN CALL Display1
        ELSE IF n = 9 THEN OUTPUT "Have a nice day!"
        ELSE OUTPUT "Invalid operation"
        END IF
    UNTIL n = 9
END ALGORITHM
~~~

## INSERT AT BEGINNING

~~~text
ALGORITHM InsertFirst
    temp ← CREATE_NODE
    IF temp = NULL THEN
        OUTPUT "Memory allocation failed"
        RETURN
    END IF

    READ item
    temp.data ← item
    temp.llink ← NULL
    temp.rlink ← head
    IF head ≠ NULL THEN
        head.llink ← temp
    END IF
    head ← temp

    OUTPUT "The current status is:"
    CALL Display
END ALGORITHM
~~~

## INSERT AT END

~~~text
ALGORITHM InsertLast
    temp ← CREATE_NODE
    IF temp = NULL THEN
        OUTPUT "Memory allocation failed"
        RETURN
    END IF

    READ item
    temp.data ← item
    temp.rlink ← NULL

    IF head = NULL THEN
        temp.llink ← NULL
        head ← temp
    ELSE
        ptr ← head
        WHILE ptr.rlink ≠ NULL
            ptr ← ptr.rlink
        END WHILE
        temp.llink ← ptr
        ptr.rlink ← temp
    END IF

    OUTPUT "The current status is:"
    CALL Display
END ALGORITHM
~~~

## INSERT AFTER A KEY

~~~text
ALGORITHM InsertKey
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN
    END IF

    READ item
    READ key

    ptr ← head
    WHILE ptr ≠ NULL AND ptr.data ≠ key
        ptr ← ptr.rlink
    END WHILE
    IF ptr = NULL THEN
        OUTPUT "Search fails: key not found"
        RETURN
    END IF

    temp ← CREATE_NODE
    IF temp = NULL THEN
        OUTPUT "Memory allocation failed"
        RETURN
    END IF

    temp.data ← item
    temp.rlink ← ptr.rlink
    temp.llink ← ptr
    IF ptr.rlink ≠ NULL THEN
        ptr.rlink.llink ← temp
    END IF
    ptr.rlink ← temp

    OUTPUT "The current status is:"
    CALL Display
END ALGORITHM
~~~

## DELETE FROM BEGINNING

~~~text
ALGORITHM DeleteFirst
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN
    END IF

    ptr ← head
    OUTPUT ptr.data, "is deleted"
    head ← head.rlink
    IF head ≠ NULL THEN
        head.llink ← NULL
    END IF
    FREE ptr

    OUTPUT "The current status is:"
    CALL Display
END ALGORITHM
~~~

## DELETE FROM END

~~~text
ALGORITHM DeleteLast
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN
    END IF

    ptr ← head
    WHILE ptr.rlink ≠ NULL
        ptr ← ptr.rlink
    END WHILE

    OUTPUT ptr.data, "is deleted"
    IF ptr.llink ≠ NULL THEN
        ptr.llink.rlink ← NULL
    ELSE
        head ← NULL
    END IF
    FREE ptr

    OUTPUT "The current status is:"
    CALL Display
END ALGORITHM
~~~

## DELETE A KEY

~~~text
ALGORITHM DeleteKey
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN
    END IF

    READ key
    ptr ← head
    WHILE ptr ≠ NULL AND ptr.data ≠ key
        ptr ← ptr.rlink
    END WHILE
    IF ptr = NULL THEN
        OUTPUT "Search fails: key not found"
        RETURN
    END IF

    OUTPUT ptr.data, "is deleted"
    IF ptr.llink ≠ NULL THEN
        ptr.llink.rlink ← ptr.rlink
    ELSE
        head ← ptr.rlink
    END IF
    IF ptr.rlink ≠ NULL THEN
        ptr.rlink.llink ← ptr.llink
    END IF
    FREE ptr

    OUTPUT "The current status is:"
    CALL Display
END ALGORITHM
~~~

## DISPLAY FORWARD

~~~text
ALGORITHM Display
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN
    END IF

    ptr ← head
    WHILE ptr ≠ NULL
        OUTPUT ptr.data
        ptr ← ptr.rlink
    END WHILE
END ALGORITHM
~~~

## DISPLAY REVERSE

~~~text
ALGORITHM Display1
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN
    END IF

    ptr ← head
    WHILE ptr.rlink ≠ NULL          // move to the last node
        ptr ← ptr.rlink
    END WHILE

    WHILE ptr ≠ NULL                // traverse backward
        OUTPUT ptr.data
        ptr ← ptr.llink
    END WHILE
END ALGORITHM
~~~

**Time:** Traversal/search O(n); insertion/deletion at the beginning O(1).

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
