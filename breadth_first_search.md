# Pseudocode: Breadth-First Search (BFS)

BFS visits graph vertices level by level using a queue. The graph is read as an adjacency matrix `adj` (1 means an edge); vertices are numbered from 0 to vertices - 1, with at most MAX (10) vertices.

~~~text
ALGORITHM BFS
    front ← 0
    rear ← -1
    visited[0 ... MAX - 1] ← 0

    READ vertices
    IF vertices < 1 OR vertices > MAX THEN
        OUTPUT "Invalid number of vertices"
        STOP
    END IF

    READ adj[vertices][vertices]

    READ start
    IF start < 0 OR start ≥ vertices THEN
        OUTPUT "Invalid starting vertex"
        STOP
    END IF

    rear ← rear + 1
    queue[rear] ← start
    visited[start] ← 1

    OUTPUT "BFS:"
    WHILE front ≤ rear
        current ← queue[front]
        front ← front + 1
        OUTPUT current

        FOR i ← 0 TO vertices - 1
            IF adj[current][i] = 1 AND visited[i] = 0 THEN
                rear ← rear + 1
                queue[rear] ← i
                visited[i] ← 1
            END IF
        END FOR
    END WHILE
END ALGORITHM
~~~

This visits only vertices reachable from the start vertex.

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
