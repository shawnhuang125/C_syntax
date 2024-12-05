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
head -> 	10     ->     20        ->   NULL
          First:1001        Second:1005
        (memory address)  (memory address)
```
## 程式碼編寫
- 使用struct定義結構方便後續使用結構體
	```
	struct node {
		int data;
		struct node* next_mem;
	};
	```
- 主程式初始化head

	- 正確寫法
	```
	int main(){
		//初始化linked list的head
		struct node* head = NULL;
		return 0;
	}
	```
	- 為甚麼要初始化head?因為如果沒有head,linked list將無法借助任何指標當作起點來輸入數據,沒有這個將會顯示錯誤
	```
	[ERROR] 'head' was not declared in this scope
	```
- 定義一個新增節點的函數
	- 程式碼重點:只要會用到結構體的變數一定要用struct
	 ```
 	struct node* [variable]
	```
  	- 一定要想清楚適用原本的指標還是搜尋後已經更新的指標
  	```
   	*head = newnode; or temp->next = newnode;
   	```
	- 如果head指向的下一個位址為NULL則新增結點到head後面,反之就一直往下搜尋node值到最後一個node的指向位址為NULL
	```
 	struct node* createnode(int node_data){
 	struct node* newnode = (struct node*)malloc(sizeof(struct node));
 	if(newnode==NULL){
 		printf("memory allocation failed!");
 	}
 	newnode->data = node_data;
 	newnode->next = NULL;
 	return newnode;
	}
	int AddEnd(struct node** head,int node_data){
		//node**是指標的指標,第一層指標是node(每個節點)第二層指標是node->next(結點內部的next指標)
		struct node* newnode = createnode(node_data);
		if(*head==NULL){
			//如果節點為空就在head後新增節點
			*head = newnode;
		}else{
			//反之如果節點的指標都不為空搜尋最後一個node(因為最後一個node的next為NULL)
			struct node* temp = *head;
			while(temp->next!=NULL){
				temp = temp->next;
			}
			//搜尋到最後一個node->next指標為NULL的時候就加入新節點
			temp->next = newnode;	
		}
	
	}
	```
- 列印linked list
	```
	int PrintList(struct node* head){
		printf("head   --->   ");
		struct node* temp = head;
		while(temp!=NULL){
			printf("%d   --->   ",temp->data);
			temp = temp->next;
		}
 		printf("NULL\n");
	
	}
	```
 - 主程式呼叫
	```
	int main(){
		//定義linked list的初始值 
		struct node* head = NULL;
		AddEnd(&head,10);
		AddEnd(&head,20);
		AddEnd(&head,30);
		PrintList(head);
		return 0;
	} 
	```
 - 輸出結果
	```
	10  --->   20  --->   30  --->   NULL
	```
