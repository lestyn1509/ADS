#include<stdio.h>
#include<stdlib.h>
struct BTnode
{
int keyVal;
struct BTnode *leftNode;
struct BTnode *rightNode;
};
struct BTnode *getNode(int value)
{
struct BTnode *newNode = malloc(sizeof(struct BTnode));
newNode->keyVal = value;
newNode->leftNode = NULL;
newNode->rightNode = NULL;
return newNode;
}
struct BTnode *insert(struct BTnode *rootNode, int value)
{
if(rootNode == NULL)
return getNode(value);
if(rootNode->keyVal < value)
rootNode->rightNode = insert(rootNode->rightNode,value);
else if(rootNode->keyVal > value)
rootNode->leftNode = insert(rootNode->leftNode,value);
return rootNode;
}
void insertorder(struct BTnode *rootNode)
{
if(rootNode == NULL)
return;
insertorder(rootNode->leftNode);
printf("%d ",rootNode->keyVal);
insertorder(rootNode->rightNode);
}
int main()
{
struct BTnode *rootNode = NULL;
int n,ch;
while(1){
printf("\nEnter your choice 1.Insert 2.Exit\n");
scanf("%d",&ch);
switch(ch){
case 1:printf("\nEnter the element to insert:");
    scanf("%d",&n);
    rootNode = insert(rootNode,n);
    insertorder(rootNode);
    break;
case 2: exit(0);
}
}
}
