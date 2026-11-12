# Pseudocode: Queue Operations Using an Array

The program keeps an array `queue` of capacity maxsize (3) with `front ← -1` and `rear ← -1`. Insertions move `rear` forward with the modulo operator, so freed positions are reused. A menu is repeated until the user chooses EXIT.

## MAIN MENU

~~~text
ALGORITHM QueueMenu
    front ← -1
    rear ← -1
    REPEAT
        OUTPUT "1.ENTER  2.DELETE  3.DISPLAY  4.EXIT"
        READ n

        IF n = 1 THEN
            CALL Enqueue
        ELSE IF n = 2 THEN
            CALL Dequeue
        ELSE IF n = 3 THEN
            CALL Display
        ELSE IF n = 4 THEN
            EXIT PROGRAM
        ELSE
            OUTPUT "Invalid choice"
        END IF
    UNTIL n = 4
END ALGORITHM
~~~

## ENQUEUE

~~~text
ALGORITHM Enqueue
    READ item
    IF front = (rear + 1) MOD maxsize THEN
        OUTPUT "queue overflow"
    ELSE IF front = -1 AND rear = -1 THEN
        front ← 0
        rear ← 0
        queue[rear] ← item
    ELSE
        rear ← (rear + 1) MOD maxsize
        queue[rear] ← item
    END IF
END ALGORITHM
~~~

## DEQUEUE

~~~text
ALGORITHM Dequeue
    IF rear = -1 AND front = -1 THEN
        OUTPUT "queue underflow"
    ELSE IF rear = front THEN
        data ← queue[front]
        front ← -1
        rear ← -1
    ELSE
        data ← queue[front]
        front ← (front + 1) MOD maxsize
        OUTPUT "one element is successfully deleted"
    END IF
END ALGORITHM
~~~

## DISPLAY

~~~text
ALGORITHM Display
    FOR i ← front TO rear
        OUTPUT queue[i]
    END FOR
END ALGORITHM
~~~

**Time:** Enqueue O(1), Dequeue O(1), Display O(n). **Space:** O(maxsize).

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
