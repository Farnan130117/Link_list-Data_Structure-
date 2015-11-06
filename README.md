# Link_list-Data_Structure-
//Link_list(Data_Structure)

#include <stdio.h>
#include <stdlib.h>

struct node
{
    int val;
    struct node *next;
};
struct node *head=NULL, *last=NULL;

void insert( int value)
{
    struct node *tmp;
    tmp=(struct node *)malloc(sizeof(struct node));
    tmp->val=value;
    tmp->next=NULL;
    if( head == NULL )
    {
        head=tmp;
        last=tmp;
    }
    else
    {
        last->next=tmp;
        last=tmp;
    }
}

void printlist()
{
    struct node *tmp=head;
    printf("The list is:");
    while( tmp != NULL )
    {
        printf(" %d", tmp->val);
        tmp=tmp->next;
    }
    printf("\n");
}
void search( )
{
    printf("Which value to Search?");
    int n, k=0;
    scanf("%d",&n);
    struct node *tmp=head;
    while( tmp != NULL )
    {
        if( tmp->val == n )
            k=1;
        tmp=tmp->next;
    }
    if( k )
        printf("Yes\n");
    else
        printf("No\n");
}
void deletenode( )
{
    int n, posi;
    printf("Where to Delete?\n");
    printf("1\tFirst Position\n");
    printf("2\tLast Position\n");
    printf("3\tAny Desired Position\n");
    scanf("%d",&n);
    if( n == 1 )
    {
        struct node *tmp=head;
        tmp=tmp->next;
        head=tmp;
        printlist();
    }
    else if( n == 2 )
    {
        struct node *tmp=head ;
        while( 1 )
        {
            if( tmp->next->next == NULL )
            {
                tmp->next=NULL;
                break;
            }
            else
                tmp=tmp->next;
        }
        printlist();
    }
    else if( n == 3 )
    {
        int i=1;
        printf("Enter Position: ");
        scanf("%d",&posi);
        struct node *tmp=head;
        while( tmp->next != NULL && i <= posi )
        {
            if( i+1 == posi )
            {
                tmp->next=tmp->next->next;
                break;
            }
            else
            {
                i++;
                tmp=tmp->next;
            }
        }
        printlist();
    }
}

void ins()
{
    int n, v, posi;
    printf("Where to insert?\n");
    printf("1\tFirst Position\n");
    printf("2\tLast Position\n");
    printf("3\tAny Desired Position\n");
    scanf("%d",&n);
    if( n == 1 )
    {
        printf("Enter value: ");
        scanf("%d",&v);
        struct node *tmp;
        tmp=(struct node *)malloc( sizeof(struct node));
        tmp->val=v;
        tmp->next=head;
        head=tmp;
        printlist();
    }
    else if( n == 2 )
    {
        printf("Enter value: ");
        scanf("%d",&v);
        struct node *tmp;
        tmp=(struct node *)malloc(sizeof(struct node));
        tmp->val=v;
        tmp->next=NULL;
        last->next=tmp;
        last=tmp;
        printlist();
    }
    else if(n == 3 )
    {
        int i=1;
        printf("Enter position: ");
        scanf("%d",&posi);
        printf("\nEnter value: ");
        scanf("%d",&n);
        struct node *tmp1, *tmp=head, *tmp2;
        tmp1=(struct node *)malloc(sizeof(struct node));
        tmp1->val=n;
        tmp1->next=NULL;
        while( tmp->next != NULL && i <= posi)
        {
            if( i+1 == posi )
            {
                tmp2=tmp->next;
                tmp->next=tmp1;
                tmp1->next=tmp2;
            }
            i++;
            tmp=tmp->next;
        }
        printlist();
    }
}
int main()
{
    int n;
    printf("Enter value & Enter -1 to exit.\n");
    while( 1 )
    {
        scanf("%d",&n);
        if( n < 0 )
            break;
        insert(n);
    }
    printlist();
    printf("Enter choice:\n\n");
    printf("1\tInsert\n");
    printf("2\tDelete\n");
    printf("3\tSearch\n");
    printf("4\tExit\n");
    scanf("%d",&n);
    if( n == 1 )
        ins();
    else if( n == 2 )
        deletenode();
    else if( n == 3 )
        search();
    else if( n == 4 )
        return 0;
    return 0;
}


