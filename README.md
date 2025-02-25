# C_syntax
## 資料結別
### 指標介紹
> 雙層指標(int** p)跟單層指標(int* p)一樣都可以對一個變數(a)進行READ或是WRITE

> 雙層指標是(pp)修改另一個變數的指標變數(p),也就是該變數(a)的副本(p)

> 單層指標(**p)是指標變數,作用是直接對該變數(a)進行READ或是WRITE

> 與單層指標(p)差別在雙層指標(pp)修改的是指標變數(p)

> 第一層指標(p)儲存的是該變數的記憶體位址

> 第二層指標(pp)儲存的是該變數(a)的指標變數(p)的記憶體位址

- **甚麼是指標?甚麼是雙重指標?**
- 舉例說明:
```
#include <stdio.h>

void updatePointer(int** pp, int* newAddr) {
    *pp = newAddr;  // 修改單層指標的內容
}

int main() {
    int a = 10, b = 20;
    int* p = &a;    // 單層指標，指向 a
    int** pp = &p;  // 雙層指標，指向 p

    printf("p 初始指向: %p\n", p);    // 指向 a 的地址
    printf("a 的值: %d\n", *p);       // a 的值 10

    updatePointer(pp, &b);            // 修改 p，讓它指向 b

    printf("p 修改後指向: %p\n", p);  // 指向 b 的地址
    printf("b 的值: %d\n", *p);       // b 的值 20

    return 0;
}
```
- 輸出
```
p 初始指向: 000000000062FE14
a 的值: 10
p 修改後指向: 000000000062FE10
b 的值: 20

```
- p單層指標可以用來讀取或修改另一個變數的數值(Call By Address),但是無法改變p單層指標中儲存的a變數的記憶體位址空間。
- 雙層指標儲存的是p單層指標本身的記憶體位址，它允許修改p單層指標的內容（即其儲存的地址）。
- 修改後的變化已經體現在記憶體中，無需回傳更新的目標變數地址或數值。
- 節點和一般簡單變數的差異
- 節點可以用來動態分配簡單變數的記憶體空間。
- 一般的簡單變數如整數或浮點數都是靜態需告的,除非使用指標去動態修改其記憶體位址。
- **甚麼時候需要使用單層指標?**
> 單層指標是用來對資料`Read`和`Write`
- **甚麼時候需要使用雙重層指標?**
> 當需要改變每個結構體時`change memory address spaces`

## 資料結構
## 流程控制
```
scanf("%[^\n]%*c", s);
```
- `%[`代表從第一個輸入字元開始輸入
- `^\n]`代表識別輸入除了`\n`換行符號以外的字串
- `%*c`代表不儲存一個字元符號,這邊是不儲存`\n`換行符號,目的是防止後續輸入字串出現錯誤
- 所以`%[^\n]%*c`代表從第一個輸入字元開始識別輸入,輸入除了`\n`換行符號以外的輸入字元,最後部儲存換行符號`\n`
## 函式
