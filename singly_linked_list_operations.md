# Pseudocode: Singly Linked List Operations

Each node contains `data` and a `link` to the next node. The list starts empty (`head ← NULL`). A menu is repeated until the user chooses Exit, and the list is displayed after every insertion or deletion.

## MAIN MENU

~~~text
ALGORITHM LinkedListMenu
    head ← NULL
    OUTPUT "1.Insert at first  2.Insert at last  3.Insert after a key"
    OUTPUT "4.Delete from the front  5.Delete from the end  6.Delete a key"
    OUTPUT "7.Display  8.Exit"

    REPEAT
        READ n

        IF n = 1 THEN CALL InsertFirst
        ELSE IF n = 2 THEN CALL InsertLast
        ELSE IF n = 3 THEN CALL InsertKey
        ELSE IF n = 4 THEN CALL DeleteFirst
        ELSE IF n = 5 THEN CALL DeleteLast
        ELSE IF n = 6 THEN CALL DeleteKey
        ELSE IF n = 7 THEN CALL Display
        ELSE IF n = 8 THEN
            OUTPUT "Have a nice day"
            EXIT PROGRAM
        ELSE
            OUTPUT "Invalid operation"
        END IF
    UNTIL n = 8
END ALGORITHM
~~~

## INSERT AT BEGINNING

~~~text
ALGORITHM InsertFirst
    temp ← CREATE_NODE
    IF temp = NULL THEN
        OUTPUT "Memory underflow"
    ELSE
        READ item
        temp.data ← item
        temp.link ← head
        head ← temp
        CALL Display
    END IF
END ALGORITHM
~~~

## INSERT AT END

~~~text
ALGORITHM InsertLast
    temp ← CREATE_NODE
    IF temp = NULL THEN
        OUTPUT "Memory underflow"
        EXIT PROGRAM
    END IF

    READ item
    IF head = NULL THEN
        temp.data ← item
        temp.link ← head
        head ← temp
    ELSE
        ptr ← head
        WHILE ptr.link ≠ NULL
            ptr ← ptr.link
        END WHILE
        ptr.link ← temp
        temp.data ← item
        temp.link ← NULL
    END IF
    CALL Display
END ALGORITHM
~~~

## INSERT AFTER A KEY

~~~text
ALGORITHM InsertKey
    temp ← CREATE_NODE
    IF temp = NULL THEN
        OUTPUT "Memory underflow"
        EXIT PROGRAM
    END IF

    READ item
    READ key

    ptr ← head
    WHILE ptr ≠ NULL AND ptr.data ≠ key
        ptr ← ptr.link
    END WHILE

    IF ptr = NULL THEN
        OUTPUT "Search fails"
    ELSE
        temp.data ← item
        temp.link ← ptr.link
        ptr.link ← temp
    END IF
    CALL Display
END ALGORITHM
~~~

## DELETE FROM FRONT

~~~text
ALGORITHM DeleteFirst
    IF head = NULL THEN
        OUTPUT "The list is empty"
        EXIT PROGRAM
    END IF

    OUTPUT head.data, "is deleted"
    prev ← head
    head ← head.link
    FREE prev
    CALL Display
END ALGORITHM
~~~

## DELETE FROM END

~~~text
ALGORITHM DeleteLast
    IF head = NULL THEN
        OUTPUT "The list is empty"
        EXIT PROGRAM
    END IF

    prev ← head
    current ← head
    WHILE current.link ≠ NULL
        prev ← current
        current ← current.link
    END WHILE

    prev.link ← NULL
    OUTPUT current.data, "is deleted"
    FREE current
    CALL Display
END ALGORITHM
~~~

## DELETE A KEY

~~~text
ALGORITHM DeleteKey
    IF head = NULL THEN
        OUTPUT "The list is empty"
        EXIT PROGRAM
    END IF

    READ key
    prev ← head
    current ← head
    WHILE current ≠ NULL AND current.data ≠ key
        prev ← current
        current ← current.link
    END WHILE

    IF current = NULL THEN
        OUTPUT "Search fails"
    ELSE
        OUTPUT current.data, "is deleted"
        IF current = head THEN
            head ← current.link
        ELSE
            prev.link ← current.link
        END IF
        FREE current
    END IF
    CALL Display
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM Display
    IF head = NULL THEN
        OUTPUT "the list is empty"
    ELSE
        ptr ← head
        WHILE ptr ≠ NULL
            OUTPUT ptr.data
            ptr ← ptr.link
        END WHILE
    END IF
END ALGORITHM
~~~

**Time:** Search and end operations O(n); insertion/deletion at the beginning O(1).

## C implementation

~~~c
#include<stdio.h>
#include<stdlib.h>

struct node
{
    int data;
    struct node *link;
};

struct node *head=NULL,*temp=NULL,*ptr=NULL,*prev=NULL,*current=NULL;
int item,key;

void insertFirst();
void insertLast();
void insertKey();
void deleteFirst();
void deleteLast();
void deleteKey();
void display();

void main()
{
    int n;

    printf("***********LinkedList Operations Menu*************\n");
    printf("1.Insert at first.\n2.Insert at last.\n3.Insert after a key.\n4.Delete from the front.\n5.Delete from the end.\n6.Delete a key.\n7.Display.\n8.Exit\n");

    do
    {
        printf("Enter the choice:");
        scanf("%d",&n);

        switch(n)
        {
            case 1: insertFirst();
                    break;
            case 2: insertLast();
                    break;
            case 3: insertKey();
                    break;
            case 4: deleteFirst();
                    break;
            case 5: deleteLast();
                    break;
            case 6: deleteKey();
                    break;
            case 7: display();
                    break;
            case 8: printf("Have a nice day\n");
                    exit(0);
                    break;
            default: printf("Invalid operation");
                    break;
        }
    }
    while(n!=8);
}

void insertFirst()
{
    temp=(struct node*)malloc(sizeof(struct node));

    if(temp==NULL)
    {
        printf("Memory underflow");
    }
    else
    {
        printf("Enter the element to be inserted:");
        scanf("%d",&item);

        temp->data=item;
        temp->link=head;
        head=temp;

        display();
        printf("\n");
    }
}

void insertLast()
{
    temp=(struct node*)malloc(sizeof(struct node));

    if(temp==NULL)
    {
        printf("Memory underflow");
        exit(0);
    }

    printf("Enter the element to be inserted:");
    scanf("%d",&item);

    if(head==NULL)
    {
        temp->data=item;
        temp->link=head;
        head=temp;
    }
    else
    {
        ptr=head;

        while(ptr->link!=NULL)
        {
            ptr=ptr->link;
        }

        ptr->link=temp;
        temp->data=item;
        temp->link=NULL;
    }

    display();
    printf("\n");
}

void insertKey()
{
    temp=(struct node*)malloc(sizeof(struct node));

    if(temp==NULL)
    {
        printf("Memory underflow");
        exit(0);
    }

    printf("Enter the element to be inserted:");
    scanf("%d",&item);

    printf("Enter the key:");
    scanf("%d",&key);

    ptr=head;

    while(ptr->data!=key && ptr->link!=NULL)
    {
        ptr=ptr->link;
    }

    if(ptr->link==NULL)
    {
        printf("Search fails\n");
    }
    else
    {
        temp->data=item;
        temp->link=ptr->link;
        ptr->link=temp;
    }

    display();
    printf("\n");
}

void deleteFirst()
{
    if(head==NULL)
    {
        printf("The list is empty\n");
        exit(0);
    }

    printf("%d is deleted\n",head->data);

    prev=head;
    head=head->link;

    free((void*)prev);

    display();
    printf("\n");
}

void deleteLast()
{
    if(head==NULL)
    {
        printf("The list is empty\n");
        exit(0);
    }

    prev=head;
    current=head;

    while(current->link!=NULL)
    {
        prev=current;
        current=current->link;
    }

    prev->link=NULL;

    printf("%d is deleted\n",current->data);

    free((void*)current);

    display();
    printf("\n");
}

void deleteKey()
{
    if(head==NULL)
    {
        printf("The list is empty\n");
        exit(0);
    }

    printf("Enter the key:");
    scanf("%d",&key);

    prev=head;
    current=head;

    while(current->data!=key && current->link!=NULL)
    {
        prev=current;
        current=current->link;
    }

    if(current->link==NULL)
    {
        printf("Search fails\n");
    }
    else
    {
        printf("%d is deleted\n",current->data);
        prev->link=current->link;
    }

    display();
    printf("\n");
}

void display()
{
    if(head==NULL)
    {
        printf("the list is empty\n");
    }
    else
    {
        ptr=head;

        while(ptr!=NULL)
        {
            printf("%d \t",ptr->data);
            ptr=ptr->link;
        }
    }
}
~~~
