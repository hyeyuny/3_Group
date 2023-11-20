### **<코드>**
```c
#include<stdio.h>

int Min(int* pArr, int size) 
{
    int min = pArr[0];
    for (int i = 0; i < size; i++) 
    {
        if (min > pArr[i])
            min = pArr[i];
    }
    return min;
}

int Max(int* pArr, int size)
{
    int max = pArr[0];
    for (int i = 0; i < size; i++)
    {
        if (max < pArr[i])
            max = pArr[i];
    }
    return max;
}


int Sorting(int* pArr, int size) {
    int temp;
    for (int i = 0; i < size; i++)
    {
        for (int a = 0; a < size; a++)
        {
            if (pArr[i] > pArr[a])
            {
                temp = pArr[a];
                pArr[a] = pArr[i];
                pArr[i] = temp;
            }
        }
    }
    for (int i = 0; i < size; i++)
        return pArr[i];
}

int main()
{
    int b[] = {20, 34, 12, 24, 54, 91, 9, 40, 81, 10};
    int size = sizeof(b) / sizeof(b[0]);
    Sorting(b, size);
    printf("최대값 = %d\n", Max(b, size));
    printf("최소값 = %d\n", Min(b, size));
    printf("정렬 = ");
    for (int i = 0; i < size; i++) {
        printf("%d ", b[i]);
    }
    return 0;
}
```

과>**
![image](https://github.com/hyeyuny/C_pg-3_group-notes-note-1/assets/144858340/e911d20c-7e16-4584-9e7f-88f531145d1e)
