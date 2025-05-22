#include <stdio.h>

void add(int arr[], int *n);
void update(int arr[], int n);
void removeLast(int *n);
void sortArray(int arr[], int n);
void search(int arr[], int n);
void display(int arr[], int n);

int main() {
    int arr[100];
    int n = 0;
    int choice;

    printf("How many numbers to start with? ");
    scanf("%d", &n);

    printf("Enter %d numbers:\n", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    while (1) {
        printf("\nMenu:\n");
        printf("1. Add number at end\n");
        printf("2. Update number\n");
        printf("3. Remove last number\n");
        printf("4. Sort numbers\n");
        printf("5. Search number\n");
        printf("6. Show all numbers\n");
        printf("0. Exit\n");
        printf("Choose: ");
        scanf("%d", &choice);

        if (choice == 0) {
            printf("Bye!\n");
            break;
        }

        if (choice == 1) {
            add(arr, &n);
        } else if (choice == 2) {
            update(arr, n);
        } else if (choice == 3) {
            removeLast(&n);
        } else if (choice == 4) {
            sortArray(arr, n);
        } else if (choice == 5) {
            search(arr, n);
        } else if (choice == 6) {
            display(arr, n);
        } else {
            printf("Invalid choice.\n");
        }
    }

    return 0;
}

void add(int arr[], int *n) {
    int num;
    printf("Enter number to add: ");
    scanf("%d", &num);
    arr[*n] = num;
    *n = *n + 1;
}

void update(int arr[], int n) {
    int pos, val;
    printf("Enter position to update (0 to %d): ", n - 1);
    scanf("%d", &pos);
    if (pos < 0 || pos >= n) {
        printf("Invalid position.\n");
        return;
    }
    printf("Enter new value: ");
    scanf("%d", &val);
    arr[pos] = val;
}

void removeLast(int *n) {
    if (*n == 0) {
        printf("Array is empty.\n");
    } else {
        *n = *n - 1;
        printf("Last number removed.\n");
    }
}

void sortArray(int arr[], int n) {
    int temp;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    printf("Numbers sorted.\n");
}

void search(int arr[], int n) {
    int val, found = 0;
    printf("Enter number to search: ");
    scanf("%d", &val);
    for (int i = 0; i < n; i++) {
        if (arr[i] == val) {
            printf("Found at position %d\n", i);
            found = 1;
            break;
        }
    }
    if (found == 0) {
        printf("Not found.\n");
    }
}

void display(int arr[], int n) {
    if (n == 0) {
        printf("Array is empty.\n");
        return;
    }
    printf("Numbers: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
