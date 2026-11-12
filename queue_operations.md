# Pseudocode: Linear Queue Operations Using an Array

A linear queue follows **FIFO** (First In, First Out). Initialize front ← 0, rear ← -1, and use an array of capacity MAX.

## ENQUEUE

~~~text
ALGORITHM Enqueue(queue, front, rear, MAX, item)
    IF rear = MAX - 1 THEN
        OUTPUT "Queue Overflow"
        RETURN (front, rear)
    END IF
    rear ← rear + 1
    queue[rear] ← item
    RETURN (front, rear)
END ALGORITHM
~~~

## DEQUEUE

~~~text
ALGORITHM Dequeue(queue, front, rear)
    IF front > rear THEN
        OUTPUT "Queue Underflow"
        RETURN (front, rear, EMPTY)
    END IF
    item ← queue[front]
    front ← front + 1

    IF front > rear THEN
        front ← 0
        rear ← -1
    END IF
    RETURN (front, rear, item)
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayQueue(queue, front, rear)
    IF rear = -1 THEN
        OUTPUT "Queue is empty"
        RETURN
    END IF
    FOR i ← front TO rear
        OUTPUT queue[i]
    END FOR
END ALGORITHM
~~~

A linear queue may leave unused positions at the beginning after deletions; a circular queue reuses those positions.

**Time:** Enqueue O(1), Dequeue O(1), Display O(n).

## C implementation

~~~c
#include<stdio.h>
#include<stdlib.h>
#define maxsize 3

    int rear=-1;
    int front=-1;
    int queue[maxsize];
    void enqueue();
    void dequeue();
    void display();
    void main()
   {
    int n=0;
    while(n!=4)
    {
     printf("\n-----WELCOME TO  QUEUE OPERATIONS----- \n \n  ~Choose ""1"" if you want to ENTER the elements.~ \n ~Choose ""2"" if you want to DELETE the Elements.~\n ~Choose ""3"" if you want to DISPLAY the elements.~ \n ~Choose ""4"" to exIT.~ \n");
     printf("-----Enter your choice:-----\n");
     scanf("%d",&n);
                       switch(n)
                       {
                         case 1:enqueue();
                                break;
                       
                         case 2:dequeue();
                                break;
                       
                         case 3:display();
                                break;
                       
                         case 4:printf("\nGet a life dude!\n");
                                exit(0);
                                break;
                              
                         default:printf("\nlooooser!\n");
                                break;
                       }
   }
  }
                                        void enqueue()
                                        {
                                        int item;
                                        printf("Enter the number to insert:");
                                        scanf("%d",&item);
                                         if(front==(rear+1)%maxsize)
                                            printf("queue overflow\n");
                                            
                                         else if(front==-1&&rear==-1)
                                              {
                                               front=0;
                                               rear=0;
                                               queue[rear]=item;
                                              }
                                              
                                          else
                                           {
                                            rear=(rear+1)%maxsize;
                                            queue[rear]=item;
                                           }
                                          }
                                                           void dequeue()
                                                            {
                                                              int data;
                                                              if(rear==-1&&front==-1)
                                                                {
                                                                  printf("queue underflow\n");
                                                                }
                                                                
                                                              else if(rear==front)
                                                               {
                                                                data=queue[front];
                                                                front=-1;
                                                                rear=-1;
                                                               }
                                                              else
                                                              {
                                                               data=queue[front];
                                                               front=(front+1)%maxsize;
                                                               printf("one element is successfully deleted\n");
                                                              }
                                                            }
  void display()
  {
    int i;
     for(i=front;i<=rear;i++)
        {
        printf("%d\n",queue[i]);
        }
  }
~~~
