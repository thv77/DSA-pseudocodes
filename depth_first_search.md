# Pseudocode: Depth-First Search (DFS)

DFS explores as far as possible along each branch before backtracking. This iterative version uses a stack and an adjacency matrix G; vertices are numbered from 0 to V - 1.

~~~text
ALGORITHM DFS(G, V, start)
    CREATE visited[0 ... V - 1], initialized to FALSE
    CREATE empty stack S
    PUSH(S, start)

    WHILE S is not empty
        u ← POP(S)
        IF visited[u] = FALSE THEN
            visited[u] ← TRUE
            OUTPUT u

            FOR v ← V - 1 DOWNTO 0
                IF G[u][v] ≠ 0 AND visited[v] = FALSE THEN
                    PUSH(S, v)
                END IF
            END FOR
        END IF
    END WHILE
END ALGORITHM
~~~

The order of neighbors pushed affects traversal order. This visits only vertices reachable from start; repeat from unvisited vertices to cover a disconnected graph.

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
