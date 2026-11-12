# Pseudocode: Depth-First Search (DFS)

DFS explores as far as possible along each branch before backtracking. This iterative version uses a stack and an adjacency matrix `adj` (1 means an edge); vertices are numbered from 0 to vertices - 1, with at most MAX (10) vertices. A vertex is marked visited when it is pushed.

~~~text
ALGORITHM DFS
    top ← -1
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

    top ← top + 1
    stack[top] ← start
    visited[start] ← 1

    OUTPUT "DFS:"
    WHILE top ≠ -1
        current ← stack[top]
        top ← top - 1
        OUTPUT current

        FOR i ← vertices - 1 DOWNTO 0
            IF adj[current][i] = 1 AND visited[i] = 0 THEN
                top ← top + 1
                stack[top] ← i
                visited[i] ← 1
            END IF
        END FOR
    END WHILE
END ALGORITHM
~~~

Neighbors are pushed from the highest vertex number down, so the lowest-numbered neighbor is popped first. This visits only vertices reachable from the start vertex.

**Time:** O(V²) with an adjacency matrix. **Extra space:** O(V).

## C implementation

~~~c
#include <stdio.h>

#define MAX 10

int main(void)
{
    int vertices, start, current, i, j, top = -1;

    int stack[MAX];
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

    stack[++top] = start;
    visited[start] = 1;

    printf("DFS:\n");

    while (top != -1)
    {
        current = stack[top--];

        printf("%d ", current);

        for (i = vertices - 1; i >= 0; i--)
        {
            if (adj[current][i] == 1 && visited[i] == 0)
            {
                stack[++top] = i;
                visited[i] = 1;
            }
        }
    }

    printf("\n");

    return 0;
}

~~~
