#include <stdio.h>
#include <sched.h>

void Merge(int A[], int p, int q, int r) {
    int i, j, k;

    int L[50], R[50];
    int n1 = q - p + 1, n2 = r - q;
    for (i = 0; i < n1; i ++ ) {
        L[i] = A[p + i];
    }

    for (j = 0; j < n2; j ++ ) {
        R[j] = A[q + j + 1];
    }

    L[n1] = INT_MAX;
    R[n2] = INT_MAX;

    i = 0;
    j = 0;
    for (k = p; k < r + 1; k ++ ) {
        if (L[i] < R[j]) {
            A[k] = L[i];
            i ++ ;
        } else {
            A[k] = R[j];
            j ++ ;
        }
    }
}

void MergeSort(int A[], int p, int r) {
    int q;
    if (p < r) {
        q = (p + r) / 2;
        MergeSort(A, p, q);
        MergeSort(A, q + 1, r);

        Merge(A, p, q, r);
    }
}

int main() {
    int A[] = {4, 1, 3, 6, 8, 5, 2, 9};
    MergeSort(A, 0, 7);

    int i;
    for (i = 0; i < 8; i ++ ) {
        printf("%d ", A[i]);
    }

    return 0;
}
