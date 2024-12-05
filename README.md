实验五 数组
一、实验目的
1、掌握一维数组和二维数组的定义、赋值和输入输出的方法。
2、掌握字符数组和字符串函数的使用。
3、掌握与数组有关的算法（特别是排序算法）。
二、实验准备
1、复习数组的基本知识。
2、复习字符串数组的特点和常用的字符串处理函数。
三、实验内容
编写下列问题的源程序并上机调试运行。
1、用选择法对 10 个整数排序(10 个整数用 scanf 函数输入)。
#include <stdio.h>
int main() {
    int a[10];
    int i, j, t, max;
    printf("请输入10个整数：\n");
    for (i = 0; i < 10; i++) {
        scanf("%d", &a[i]);
    }
    for (i = 0; i < 9; i++) {
        max = i;
        for (j = i + 1; j < 10; j++) {
            if (a[j] > a[max]) {
                max = j;
            }
        }
        if (max != i) {
            t = a[i];
            a[i] = a[max];
            a[max] = t;
        }
    }
    printf("排序后的数组：\n");
    for (i = 0; i < 10; i++) {
        printf("%d ", a[i]);
    }
    printf("\n");
    return 0;
}
![Q7H2%4S~$KU0@3`2HO6`4WD](https://github.com/user-attachments/assets/1d5d9038-4cc1-4e11-b3ca-9698969de1da)
2、有 15 个数存放在一个数组中，输入一个数，要求用折半查找法找出该数是数组中第几个
元素的值。如果该数不在数组中，则输出“无此数”。15 个数用赋初值的方法在程序中给出。
要找的数用 scanf 函数输入。
#include <stdio.h>
int main() {
    int arr[15] = { 1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29 };
    int key, low = 0, high = 14, mid;
    int found = 0;
    printf("请输入要查找的数：\n");
    scanf("%d", &key);
    while (low <= high) {
        mid = (low + high) / 2;
        if (arr[mid] == key) {
            printf("%d 是数组中第 %d 个元素的值。\n", key, mid + 1);
            found = 1;
            break;
        }
        else if (arr[mid] < key) {
            low = mid + 1;
        }
        else {
            high = mid - 1;
        }
    }
    if (!found) {
        printf("无此数。\n");
    }
    return 0;
}
![%C9L7YYL}G)PI 2L2FXNYCP](https://github.com/user-attachments/assets/5359a691-69a1-4258-88fd-cbb4ccc2b81e)
3、将两个字符串连接起来，不要用 strcat 函数。
#include <stdio.h>
void stringConcat(char* dest, const char* src) {
    while (*dest) {
        dest++;  
    }
    while (*src) {
        *dest = *src;
        dest++;
        src++;
    }
    *dest = '\0';
}
int main() {
    char str1[100] = "Hello, ";
    char str2[] = "World!";
    stringConcat(str1, str2);
    printf("%s\n", str1);
    return 0;
}
![9II6FS_M4YYO%ZR4OM$}RDS](https://github.com/user-attachments/assets/3150997e-026e-49e0-a7f5-b6d71d20b97c)

4、找出一个二维数组的“鞍点”，即该位置上的元素在该行上最大，在该列上最小。也可能
没有鞍点。此二维数组可以设定如下，其中，数组元素的值用赋初值方法在程序中指定。
9 80 205 40
90 -60 96 1
210 -3 101 89
#include <stdio.h>
#define ROW 3
#define COL 4
int main() {
    int arr[ROW][COL] = {
        {9, 80, 205, 40},
        {90, -60, 96, 1},
        {210, -3, 101, 89}
    };
    int i, j, k;
    int flag;
    for (i = 0; i < ROW; i++) {
        int max_row_index = 0;
        for (j = 1; j < COL; j++) {
            if (arr[i][j] > arr[i][max_row_index]) {
                max_row_index = j;
            }
        }
        flag = 1;
        for (k = 0; k < ROW; k++) {
            if (arr[k][max_row_index] < arr[i][max_row_index]) {
                flag = 0;
                break;
            }
        }
        if (flag) {
            printf("鞍点为:%d\n", arr[i][max_row_index]);
            return 0;
        }
    }
    printf("没有鞍点\n");
    return 0;
}
![XCYLRILOWI)H{8$KJZIIK`E](https://github.com/user-attachments/assets/f498aa24-4780-4e2a-b20a-2dc523d7c89a)
