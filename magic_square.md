# 魔術方陣
## 3*3魔術矩陣
- 描述：
- 請使用C語言宣告一陣列 int A[3][3], 並自動填入3×3魔術方陣的值後印出
```
#include<stdlib.h>
#include<stdio.h>
int main(){
    int x=0,y=1,array[3][3]={0};
    /*for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            printf("%d\t",array[i][j]);
        }
        printf("\n");
    }*/
   array[0][1]=0;
   for(int value=1;value<10;value++){
    int x_new=0,y_new=0;
    x_new = (x+1)%3;
    y_new = (y-1+3)%3;
    if(array[y_new][x_new] != 0){
        y = y+1;
        printf("array[y][x]=%d\n",array[y][x]);
    }else{
        x = x_new;
        y = y_new;

    }
    array[y][x] = value;
    }
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            printf("%d\t",array[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```
- 結果
![image](https://github.com/user-attachments/assets/b803ea51-a97b-40f0-87d2-c7b78ddbd46a)


#### 9*9魔術矩陣
- 描述：
- 請使用C語言宣告一陣列 int A[9][9], 並自動填入3×3魔術方陣的值後印出
```
#include<stdlib.h>
#include<stdio.h>
int main(){
    int x=0,y=1,array[9][9]={0};
    /*for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            printf("%d\t",array[i][j]);
        }
        printf("\n");
    }*/
   array[0][1]=0;
   for(int value=1;value<82;value++){
    int x_new=0,y_new=0;
    x_new = (x+1)%9;
    y_new = (y-1+9)%9;
    if(array[y_new][x_new] != 0){
        y = y+1;
        //printf("array[y][x]=%d\n",array[y][x]);
    }else{
        x = x_new;
        y = y_new;

    }
    array[y][x] = value;
    }
    for(int i=0;i<9;i++){
        for(int j=0;j<9;j++){
            printf("%d\t",array[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```
- 結果
- - ![image](https://github.com/user-attachments/assets/38dfacdd-cddb-49dd-aa4d-1dfdf0052504)
