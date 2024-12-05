# Linked List鏈結串列
> 鏈結串列主要分為四個步驟

> create-->add-->insert-->delete

> create是從0到1去建立鏈結串列

> add是已經在1(初始化鏈結串列)之後要加入新的節點

> insert是在已經建立完的鏈結串列之下,指定節點去加入新節點

> delete是刪除已經建立好的鏈結串列裡面的指定節點

> 像這種鏈結串列需要用到雙重指標,因為他是先使用指標先製作一個串列,再讓每個節點都帶上一個位址。
## 鏈結串列製作流程
- **Create linked list 建立鏈結串列**:初始化鏈結串列(0-1)
```
head -> NULL
```
- **Add Node新增節點**:在create完成後的鏈結串列之後再加入新的節點
```
head -> 10 -> NULL
```
- Add了第二個的時候
```
head -> 	10     ->     20        ->      30        ->   NULL
          First:1001        Second:1005
        (memory address)  (memory address)
```
## 描述程式碼的運作流程
- 主程式初始化head
```
#include<stdio.h>
#include<stdlib.h>
int main(){
	//define a enter space,every add should use head to insert new node! 
	node* head = NULL;
	
	return 0;
}
```
- 使用typedef定義結構方便後續使用結構
```
typedef struct node {
	int data;
	struct node* next_mem;
};
```
- 定義一個新增節點的函數
- add(&head,data)
- head是不變的,功能是告訴add函式head是最前面的入口,沒有這個head入口是無法添加或修改任何節點的,data是你想要放入的數據
```
void add(node** head,int data){
	//to go to the next node
	node* new_node = (node*)malloc(sizeof(node));
	//to input the data in new node
	new_node->data = data;
	//the next_mem coolumn of the last node must be empty including the new node you add!
	new_node->next_mem = NULL;
	
	
	
	if(*head == NULL){
		*head = new_node;
		return;
	}
	//to find the last one node to add!
	node* current = *head;
	while(current->next_mem!=NULL){
		current = current->next_mem;
	}
	current->next_mem = new_node;
}
```
