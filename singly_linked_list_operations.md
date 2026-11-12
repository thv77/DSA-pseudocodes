# Pseudocode: Singly Linked List Operations

Each node contains data and a next link. Initialize head ← NULL.

## INSERT AT BEGINNING

~~~text
ALGORITHM InsertFront(head, value)
    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.next ← head
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
        RETURN node
    END IF
    current ← head
    WHILE current.next ≠ NULL
        current ← current.next
    END WHILE
    current.next ← node
    RETURN head
END ALGORITHM
~~~

## INSERT AFTER A KEY

~~~text
ALGORITHM InsertAfter(head, key, value)
    current ← head
    WHILE current ≠ NULL AND current.data ≠ key
        current ← current.next
    END WHILE
    IF current = NULL THEN
        OUTPUT "Key not found"
        RETURN head
    END IF

    node ← CREATE_NODE(value)
    IF node = NULL THEN
        OUTPUT "Allocation failed"
        RETURN head
    END IF
    node.next ← current.next
    current.next ← node
    RETURN head
END ALGORITHM
~~~

## DELETE FROM BEGINNING

~~~text
ALGORITHM DeleteFront(head)
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN head
    END IF
    temp ← head
    head ← head.next
    FREE temp
    RETURN head
END ALGORITHM
~~~

## DELETE FROM END

~~~text
ALGORITHM DeleteEnd(head)
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN head
    END IF
    IF head.next = NULL THEN
        FREE head
        RETURN NULL
    END IF

    current ← head
    WHILE current.next.next ≠ NULL
        current ← current.next
    END WHILE
    FREE current.next
    current.next ← NULL
    RETURN head
END ALGORITHM
~~~

## DELETE BY KEY

~~~text
ALGORITHM DeleteKey(head, key)
    IF head = NULL THEN
        OUTPUT "List is empty"
        RETURN head
    END IF
    IF head.data = key THEN
        temp ← head
        head ← head.next
        FREE temp
        RETURN head
    END IF

    previous ← head
    current ← head.next
    WHILE current ≠ NULL AND current.data ≠ key
        previous ← current
        current ← current.next
    END WHILE
    IF current = NULL THEN
        OUTPUT "Key not found"
        RETURN head
    END IF

    previous.next ← current.next
    FREE current
    RETURN head
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayList(head)
    current ← head
    WHILE current ≠ NULL
        OUTPUT current.data
        current ← current.next
    END WHILE
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
