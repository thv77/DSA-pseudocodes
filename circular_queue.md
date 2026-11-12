# Pseudocode: Circular Queue Using an Array

A circular queue reuses array positions by wrapping indices around. Initialize front ← -1 and rear ← -1; array capacity is MAX.

## ENQUEUE

~~~text
ALGORITHM CircularEnqueue(queue, front, rear, MAX, item)
    IF (rear + 1) MOD MAX = front THEN
        OUTPUT "Queue Overflow"
        RETURN (front, rear)
    END IF

    IF front = -1 THEN
        front ← 0
        rear ← 0
    ELSE
        rear ← (rear + 1) MOD MAX
    END IF

    queue[rear] ← item
    RETURN (front, rear)
END ALGORITHM
~~~

## DEQUEUE

~~~text
ALGORITHM CircularDequeue(queue, front, rear, MAX)
    IF front = -1 THEN
        OUTPUT "Queue Underflow"
        RETURN (front, rear, EMPTY)
    END IF

    item ← queue[front]
    IF front = rear THEN
        front ← -1
        rear ← -1
    ELSE
        front ← (front + 1) MOD MAX
    END IF
    RETURN (front, rear, item)
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM DisplayCircularQueue(queue, front, rear, MAX)
    IF front = -1 THEN
        OUTPUT "Queue is empty"
        RETURN
    END IF

    i ← front
    REPEAT
        OUTPUT queue[i]
        IF i = rear THEN
            BREAK
        END IF
        i ← (i + 1) MOD MAX
    UNTIL FALSE
END ALGORITHM
~~~

**Time:** Enqueue O(1), Dequeue O(1), Display O(n). **Space:** O(MAX).

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
     printf("\n-----WELCOME TO CIRCULAR QUEUE OPERATIONS----- \n \n  ~Choose ""1"" if you want to ENTER the elements.~ \n ~Choose ""2"" if you want to DELETE the Elements.~\n ~Choose ""3"" if you want to DISPLAY the elements.~ \n ~Choose ""4"" to exIT.~ \n");
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
              int i,n;
              for(i=front;i<=rear;i=(i+1)%maxsize)
                 {
                  printf("%d\n",queue[i]);
                 }
              printf("%d\n",queue[i]);
             }
~~~
