//JOEL ANANTH A - 2021503022
//SONG QUEUE USING LINKED LIST

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<math.h>

typedef struct Node
{
    char song[100];
    struct Node* next;
}*NODE;

NODE makeNode(char song[])
{
    NODE t;
    t=(NODE)malloc(sizeof(struct Node));
    strcpy(t->song,song);
    t->next=NULL;
    return t;
}

void display(NODE l,int i)
{
    if(l)
    {
        printf("%d) %s\n",i,l->song);
        display(l->next,i+1);
    }
}

NODE insertHead(NODE l,char song[])
{
    NODE t=makeNode(song);
    t->next=l;
    return t;
}

NODE insertEnd(NODE l,char song[])
{
    if(!l)
    {
        return makeNode(song);
    }
    l->next=insertEnd(l->next,song);
    return l;
}

NODE insertAt(NODE l,char song[],int pos,int cp)
{
    if(!l)
        return makeNode(song);
    if(cp==pos)
    {
        NODE t;
        t=makeNode(song);
        t->next=l;
        return t;
    }
    l->next=insertAt(l->next,song,pos,cp+1);
    return l;
}

NODE deleteHead(NODE l)
{
    if(l)
        return l->next;
}

NODE deleteEnd(NODE l)
{
    if(!l)
        return NULL;
    if(!l->next)
        return NULL;
    NODE t=l;
    while(t->next->next!=NULL)
        t=t->next;
    t->next=NULL;
    return l;
}

NODE deleteAt(NODE l,int pos,int cp)
{
    if(!l)
        return NULL;
    if(cp==pos)
        return l->next;
    l->next=deleteAt(l->next,pos,cp+1);
    return l;
}

void currentSong(NODE l)
{
    if(!l)
    {
        return NULL;
    }
    printf("%s\n\n",l->song);
}

int countSongs(NODE l)
{
    int i=0;
    while (l->next!=NULL)
    {
        l=l->next;
        i++;
    }
    i++;
    return i;
}

void disRandom(NODE l)
{
    char a[100];
    if(!l)
       return;
    srand(time(NULL));
    strcpy(a,l->song);
    NODE t= l;
    int n;
    for (n=2; t!=NULL; n++)
    {
        if (rand()%n==0)
           strcpy(a,t->song);
        t = t->next;
    }
    printf("Randomly selected Song is %s\n", a);
}

void main()
{
    NODE n=NULL;
    int c,x;
    char a[100];
    n=insertHead(n,"Azhagae");
    n=insertHead(n,"wasted");
    n=insertHead(n,"engaeyo");
    while(1)
    {
        printf("1. Display song queue \n");
        printf("2. Show current song \n");
        printf("3. Add song to the queue\n");
        printf("4. Add song to play next\n");
        printf("5. Add song in between the queue \n");
        printf("6. Delete last song from the queue \n");
        printf("7. Delete current song \n");
        printf("8. Delete song in between the queue \n");
        printf("9. Number of songs in the queue \n");
        printf("10. Play a song randomly \n");
        printf("11. Exit \n\n");
        printf("Enter your choice :  ");
        scanf("%d",&c);
        printf("\n");

        switch(c)
        {
        case 1:
            printf("SONG QUEUE:\n");
            display(n,1);
            printf("\n\n\n");
            break;

        case 2:
            printf("CURRENT SONG:\n");
            currentSong(n);
            printf("\n\n\n");
            break;

        case 3:
            printf("Enter name of the song: ");
            scanf("%s",a);
            n=insertEnd(n,a);
            printf("\n\n\n");
            break;

        case 4:
            printf("Enter the name of the song: ");
            scanf("%s",a);
            n=insertAt(n,a,2,1);
            printf("\n\n\n");
            break;

        case 5:
            printf("Enter the name of the song: ");
            scanf("%s",a);
            printf("\n");
            printf("Enter the position to be added to: ");
            scanf("%d",&x);
            n=insertAt(n,a,x,1);
            printf("\n\n\n");
            break;

        case 6:
            n=deleteEnd(n);
            printf("Song has been deleted");
            printf("\n\n\n");
            break;

        case 7:
            n=deleteHead(n);
            printf("Song has been deleted");
            printf("\n\n\n");
            break;

        case 8:
            printf("Enter the position of the song to be deleted to: ");
            scanf("%d",&x);
            n=deleteAt(n,x,1);
            printf("Song has been deleted");
            printf("\n\n\n");
            break;

        case 9:
            printf("Number of songs in the queue is: \n");
            printf("%d",countSongs(n));
            printf("\n\n\n");
            break;

        case 10:
            disRandom(n);
            printf("\n\n\n");
            break;

        case 11:
            printf("\n\n\t\t\tThank You !\n\n\n");
            exit(0);
        }
    }

}
