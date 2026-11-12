# Pseudocode: Breadth-First Search (BFS)

BFS visits graph vertices level by level using a queue. G is an adjacency matrix; vertices are numbered from 0 to V - 1.

~~~text
ALGORITHM BFS(G, V, start)
    CREATE visited[0 ... V - 1], initialized to FALSE
    CREATE empty queue Q
    visited[start] ← TRUE
    ENQUEUE(Q, start)

    WHILE Q is not empty
        u ← DEQUEUE(Q)
        OUTPUT u

        FOR v ← 0 TO V - 1
            IF G[u][v] ≠ 0 AND visited[v] = FALSE THEN
                visited[v] ← TRUE
                ENQUEUE(Q, v)
            END IF
        END FOR
    END WHILE
END ALGORITHM
~~~

This visits only vertices reachable from start. To traverse a disconnected graph, start BFS again at each unvisited vertex.

**Time:** O(V²) with an adjacency matrix. **Extra space:** O(V).

## C implementation

~~~c
#include <stdio.h>

#define MAX 10

int main(void)
{
    int vertices, start, current, i, j;
    int front = 0, rear = -1;

    int queue[MAX];
    int adj[MAX][MAX];
    int visited[MAX] = {0};

    printf("Enter the number of vertices: ");
    scanf("%d", &vertices);

    if (vertices < 1 || vertices > MAX)
    {
        printf("Invalid number of vertices\n");
        return 1;
    }

    printf("Enter adjacency matrix:\n");

    for (i = 0; i < vertices; i++)
    {
        for (j = 0; j < vertices; j++)
        {
            scanf("%d", &adj[i][j]);
        }
    }

    printf("Enter starting vertex (0 to %d): ", vertices - 1);
    scanf("%d", &start);

    if (start < 0 || start >= vertices)
    {
        printf("Invalid starting vertex\n");
        return 1;
    }

    queue[++rear] = start;
    visited[start] = 1;

    printf("BFS:\n");

    while (front <= rear)
    {
        current = queue[front++];

        printf("%d ", current);

        for (i = 0; i < vertices; i++)
        {
            if (adj[current][i] == 1 && visited[i] == 0)
            {
                queue[++rear] = i;
                visited[i] = 1;
            }
        }
    }

    printf("\n");

    return 0;
}

~~~
