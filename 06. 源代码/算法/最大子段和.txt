#include <stdio.h>
#include <stdlib.h>

int MaxSubSum(int *Array, int left, int right) {
    int sum = 0;
    int i;

    if (left == right) {
        if (Array[left] > 0)
            sum = Array[left];
        else
            sum = 0;
    } else {
        int center = (left + right) / 2;
        int leftSum = MaxSubSum(Array, left, center);
        int rightSum = MaxSubSum(Array, center + 1, right);

        int s1 = 0;
        int lefts = 0;
        for (i = center; i >= left; i -- ) {
            lefts += Array[i];
            if (lefts > s1)
                s1 = lefts;
        }

        int s2 = 0;
        int rights = 0;
        for (i = center + 1; i <= right; i ++ ) {
            rights += Array[i];
            if (rights > s2)
                s2 = rights;
        }

        sum = s1 + s2;

        if (sum < leftSum)
            sum = leftSum;

        if (sum < rightSum)
            sum = rightSum;
    }

    return sum;
}

int main() {
    int *Array = (int *) malloc(6 * sizeof(int));
    Array[0] = -2;
    Array[1] = 11;
    Array[2] = -4;
    Array[3] = 13;
    Array[4] = -5;
    Array[5] = -2;

    int result = MaxSubSum(Array, 0, 5);
    printf("%d", result);

    return 0;
}
