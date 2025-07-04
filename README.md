#include <stdio.h>

int front = -1, rear = -1;

void enqueue(int queue[], int data, int size) {
    if (rear == size - 1) {
        printf("Queue Overflow!\n");
    } else {
        if (front == -1)
            front = 0;
        rear++;
        queue[rear] = data;
        printf("%d inserted into queue.\n", data);
    }
}

void dequeue(int queue[]) {
    if (front == -1 || front > rear) {
        printf("Queue Underflow!\n");
    } else {
        printf("Deleted: %d\n", queue[front]);
        front++;
        if (front > rear) {
            front = -1;
            rear = -1;
        }
    }
}

void display(int queue[]) {
    if (front == -1 || front > rear) {
        printf("Queue is empty.\n");
    } else {
        printf("Queue elements: ");
        for (int i = front; i <= rear; i++) {
            printf("%d ", queue[i]);
        }
        printf("\n");
    }
}

int main() {
    int n;
    printf("Enter queue size: ");
    scanf("%d", &n);
    int queue[n];

    while (1) {
        int x;
        printf("\n-----------------------------\n");
        printf("Option 1 -> Enqueue\n");
        printf("Option 2 -> Dequeue\n");
        printf("Option 3 -> Display\n");
        printf("Option 0 -> Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &x);

        if (x == 1) {
            int data;
            printf("Enter data for enqueue operation: ");
            scanf("%d", &data);
            enqueue(queue, data, n);
        } else if (x == 2) {
            dequeue(queue);
        } else if (x == 3) {
            display(queue);
        } else if (x == 0) {
            printf("Exiting program...\n");
            break;
        } else {
            printf("Invalid choice! Try again.\n");
        }
    }

    return 0;
}
