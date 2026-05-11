# BFS.c

#include <stdio.h>

int q[20], front = -1, rear = -1, vis[20];
int a[20][20], n;

void enqueue(int item) {
    if (front == -1) front = 0;
    q[++rear] = item;
}

int dequeue() {
    int item = q[front++];
    if (front > rear) front = rear = -1;
    return item;
}

void bfs(int start) {
    enqueue(start);
    vis[start] = 1;
    while (front != -1) {
        int curr = dequeue();
        printf("%d ", curr);
        for (int i = 1; i <= n; i++) {
            if (a[curr][i] && !vis[i]) {
                enqueue(i);
                vis[i] = 1;
            }
        }
    }
}

int main() {
    int i, j, s;
    printf("Nodes: "); scanf("%d", &n);
    printf("Adjacency Matrix:\n");
    for (i = 1; i <= n; i++)
        for (j = 1; j <= n; j++)
            scanf("%d", &a[i][j]);
    printf("Start Node: "); scanf("%d", &s);
    bfs(s);
    return 0;
}
