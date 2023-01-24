#include <inttypes.h>
#include <stdio.h>
#include <stdlib.h>
typedef struct Node {
    int data;
    struct Node* nxp;
}Node;
struct Node* XOR(struct Node* a,struct Node* b)
{
    return (struct Node*)((uintptr_t)(a) ^ (uintptr_t)(b));
}
struct Node* insert(struct Node** head,int value, int position)
{
    if (*head == NULL) {
        if (position == 1) {
            struct Node* node = (struct Node*)malloc(sizeof(struct Node));
            node->data = value;
            node->nxp = XOR(NULL, NULL);
            *head = node;
        }
        else {
            printf("Invalid Position\n");
        }
    }
    else {
        int Pos = 1;
        struct Node* curr = *head;
        struct Node* prev = NULL;
        struct Node* next = XOR(prev, curr->nxp);
        while (next != NULL && Pos < position - 1) {
            prev = curr;
            curr = next;
            next = XOR(prev, curr->nxp);
            Pos++;
        }
        if (Pos == position - 1) {
            struct Node* node = (struct Node*)malloc(sizeof(struct Node));
            struct Node* temp = XOR(curr->nxp, next);
            curr->nxp = XOR(temp, node);
            if (next != NULL) {
                next->nxp = XOR(node, XOR(next->nxp, curr));
            }
            node->nxp = XOR(curr, next);
            node->data = value;
        }
        else if (position == 1) {
            struct Node* node = (struct Node*)malloc(sizeof(struct Node));
            curr->nxp = XOR(node, XOR(NULL, curr->nxp));
            node->nxp = XOR(NULL, curr);
            *head = node;
            node->data = value;
        }
        else {

            printf("Invalid Position\n");
        }
    }

    return *head;
}
void printList(struct Node** head)
{
    struct Node* curr = *head;
    struct Node* prev = NULL;
    struct Node* next;
    while (curr != NULL) {
        printf("%d ", curr->data);
        next = XOR(prev, curr->nxp);
        prev = curr;
        curr = next;

    }
}
int delete(Node** head, int key) {
    if((*head) == NULL)
        return -1;
    if((*head)->data==key) {
        Node* next = XOR(NULL, (*head)->nxp);
        if(next!=NULL) {
            next->nxp = XOR(NULL,XOR(next->nxp, (*head)));
        }
        free(*head);
        *head = next;
        return 0;
    }
    struct Node* curr = *head;
    struct Node* prev = NULL;
    while(curr!=NULL && curr->data!=key){
        Node* temp = curr;
        curr = XOR(curr->nxp, prev);
        prev = temp;
    }
    if(curr==NULL) // key not found in list
        return -1;
    Node* prevPrev = XOR(prev->nxp, curr);
    Node* next = XOR(curr->nxp, prev);
    prev->nxp = XOR(prevPrev, next);
    if(next!=NULL)
        next->nxp = XOR(XOR(next->nxp, curr), prev);
    free(curr);
    return 0; // successful
}

int main()
{
    struct Node* head = NULL;
    int data,pos,ch,ret;
    while(1){
    printf("\nEnter your choice: 1. Insert 2. Display 3. Delete 4. Exit\n");
    scanf("%d",&ch);
    switch(ch){
    case 1:  printf("Enter the value:");
    scanf("%d",&data);
    printf("Enter the position:");
    scanf("%d",&pos);
    insert(&head, data, pos);
    break;
    case 2: printList(&head);
    break;
    case 3:  printf("\nEnter data to delete from the list : ");
    scanf("%d", &data);
    ret = delete(&head, data);
    if(ret==-1)
     printf("\n%d not found in list", data);
    else
     printf("\n%d deleted from the list", data);
    break;
    case 4: exit(0);
    }
    }
}
