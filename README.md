1,21,26,30 fcfs
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int RQ[100], i, n, THM = 0, initial;
    printf("Enter the no. of Request: ");
    scanf("%d", &n);
    
    printf("Enter the Request sequence\n");
    for(i = 0; i < n; i++)
        scanf("%d", &RQ[i]);
    
    printf("Enter initial head position: ");
    scanf("%d", &initial);
    
    for(i = 0; i < n; i++) {
        THM = THM + abs(RQ[i] - initial);
        initial = RQ[i];
    }

    printf("Total head moment is: %d", THM);
    
    return 0;
}


2,3,10,12,28 M1.c
#include <stdio.h>
#include <stdlib.h>
#include <mpi.h>

void allocate(int a[], int n) {
    int i;
    for (i = 0; i < n; i++) {
        a[i] = rand() % 50;
    }
}

int main(int argc, char *argv[]) {
    int rank, size, n, sum = 0, count, *a = NULL;
    float average;

    MPI_Init(&argc, &argv);
    MPI_Comm_size(MPI_COMM_WORLD, &size);
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);

    n = atoi(argv[1]);
    printf("\nSize=%d, Rank=%d, n=%d\n", size, rank, n);

    count = n / size;

    if (rank == 0) {
        a = (int *)malloc(n * sizeof(int));
        allocate(a, n);
    }

    for (int i = 0; i < count; i++) {
        printf("\t%d", a[i]);
        sum += a[i];
    }

    // After sum calculation, calculate the average (only on root process)
    if (rank == 0) {
        average = (float)sum / n;  // Calculate average
        printf("\nSum = %d", sum);
        printf("\nAverage = %f", average);  // Print the average
    }

    MPI_Finalize();
}

2 link.c
//Program to implement the linked allocation method
//of file allocation.
#include <stdio.h>
#include <stdlib.h>

#define SIZE 100
#define NEWNODE (struct direntry *)malloc(sizeof(struct direntry))
#define NEWBLK (struct blknode *)malloc(sizeof(struct blknode))

struct blknode
{
  int bno;
  struct blknode *next;
} *curr,*prev;

struct direntry
{
 char fname[14];
 int start,end;
 struct blknode *blist;
 struct direntry *next;
}
*dirst=NULL,*dirend=NULL;


int bitvector[SIZE];

void main()
{
int ch1=0,i,j,n;
char fname[14];
struct direntry *t1,*t2;

rand()%2;
for(i=0;i<SIZE;i++)
  bitvector[i]=rand()%2;


do
{
  printf("\n\n1. Print Bit Vector");
  printf("\n2. Create File");
  printf("\n3. Print Directory");
  printf("\n4. Exit");
  printf("\nEnter Your Choice : ");
  scanf("%d",&ch1);
  switch(ch1)
  {
   case 1 :
    for(i=0;i<SIZE;i++)
    printf("%4d",bitvector[i]);
    break;
   case 2 :
    if(dirst==NULL)
      dirst=dirend=NEWNODE;
    else
      {
       dirend->next=NEWNODE;
       dirend=dirend->next;
      }
    dirend->next=NULL;
    printf("\nEnter A Filename : ");
    scanf("%s",dirend->fname);
    printf("\nEnter The Number of Blocks To Allocate : ");
    scanf("%d",&n);
    dirend->blist=NULL;
    i=0;
    while(n>0)
    {
     if(bitvector[i]==1) //found ith block free
     {
       curr=NEWBLK;
       curr->bno=i; curr->next=NULL;
       if(dirend->blist==NULL)
       { dirend->start=i;
     dirend->blist=curr;
     prev=curr;
       }
       else
       { prev->next=curr;
     prev=curr;
       }
       bitvector[i]=0; //mark ith block allocated
       n--;
       if(n==0)
     break;
     }
     i++;
    }
    dirend->end=i;
    break;
  case 3 :
    printf("\nDirectory : ");
    printf("\n--------------------------");
    printf("\nFilename        Start  End");
    printf("\n--------------------------");
    for(t1=dirst;t1!=NULL;t1=t1->next)
    {
     printf("\n%-14s  %5d  %3d",t1->fname,t1->start,t1->end);
     printf(" (");
     for(curr=t1->blist;curr!=NULL;curr=curr->next)
      printf("%3d",curr->bno);
     printf(")");
    }

    printf("\n--------------------------");
    break;
case 4:printf("\n Exit...");
    break;
  
  }
}while(ch1!=4);
}

1,4,11 b.1
#include <stdio.h>
#include <stdlib.h>

int n = 5, m = 3, p, r, reqp;
int avail[] = {3, 3, 2};  // Available resources
int max[][3] = {{9, 5, 1}, {4, 6, 0}, {7, 5, 2}, {2, 4, 4}, {5, 5, 5}};  // Max matrix
int alloc[][3] = {{2, 3, 2}, {4, 0, 0}, {5, 0, 4}, {3, 3, 2}, {2, 2, 4}};  // Allocation matrix
int need[10][10];  // Need matrix

void find_avail_need();
void display_matrices();
void display_available();
void accept_available();
void display_need();

int main() {
    int choice;

    // Initialize need matrix
    find_avail_need();

    do {
        // Menu for the user to choose actions
        printf("\nMenu:\n");
        printf("1. Accept Available Resources\n");
        printf("2. Display Allocation, Max\n");
        printf("3. Display Need Matrix\n");
        printf("4. Display Available Resources\n");
        printf("5. Exit\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                accept_available();
                break;
            case 2:
                display_matrices();
                break;
            case 3:
                display_need();
                break;
            case 4:
                display_available();
                break;
            case 5:
                printf("\nExiting the program...\n");
                break;
            default:
                printf("\nInvalid choice. Please try again.\n");
        }

    } while(choice != 5);

    return 0;
}

void find_avail_need() {
    // Calculate available resources by subtracting allocated resources
    for (r = 0; r < m; r++) {
        avail[r] = avail[r];
        for (p = 0; p < n; p++) {
            avail[r] -= alloc[p][r];
        }
    }

    // Calculate Need matrix
    for (p = 0; p < n; p++) {
        for (r = 0; r < m; r++) {
            need[p][r] = max[p][r] - alloc[p][r];
        }
    }
}

void display_matrices() {
    // Display Allocation Matrix
    printf("\nAllocation Matrix:\n");
    for (p = 0; p < n; p++) {
        printf("P%d: ", p);
        for (r = 0; r < m; r++) {
            printf("%d ", alloc[p][r]);
        }
        printf("\n");
    }

    // Display Max Matrix
    printf("\nMax Matrix:\n");
    for (p = 0; p < n; p++) {
        printf("P%d: ", p);
        for (r = 0; r < m; r++) {
            printf("%d ", max[p][r]);
        }
        printf("\n");
    }
}

void display_need() {
    // Display Need Matrix
    printf("\nNeed Matrix:\n");
    for (p = 0; p < n; p++) {
        printf("P%d: ", p);
        for (r = 0; r < m; r++) {
            printf("%d ", need[p][r]);
        }
        printf("\n");
    }
}

void display_available() {
    // Display Available Resources
    printf("\nAvailable Resources: ");
    for (r = 0; r < m; r++) {
        printf("%d ", avail[r]);
    }
    printf("\n");
}

void accept_available() {
    // Accept Available Resources from the user
    printf("\nEnter the Available Resources (A B C): ");
    for (r = 0; r < m; r++) {
        scanf("%d", &avail[r]);
    }
    find_avail_need();
}

4,7,13,18,20 scan.c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int RQ[100], i, j, n, THM = 0, initial, size, move;
    
    printf("Enter the number of Requests:\n");
    scanf("%d", &n);

    printf("Enter the Request sequence:\n");
    for (i = 0; i < n; i++)
        scanf("%d", &RQ[i]);

    printf("Enter the initial head position:\n");
    scanf("%d", &initial);

    printf("Enter total disk size:\n");
    scanf("%d", &size);

    printf("Enter the head movement direction (1 for high, 0 for low):\n");
    scanf("%d", &move);

    // Sorting the request array
    for (i = 0; i < n; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (RQ[j] > RQ[j + 1]) {
                int temp = RQ[j];
                RQ[j] = RQ[j + 1];
                RQ[j + 1] = temp;
            }
        }
    }

    int index;
    for (i = 0; i < n; i++) {
        if (initial < RQ[i]) {
            index = i;
            break;
        }
    }

    if (move == 1) {
        for (i = index; i < n; i++) {
            THM += abs(RQ[i] - initial);
            initial = RQ[i];
        }
        THM += abs(size - RQ[i - 1] - 1);
        initial = size - 1;
        for (i = index - 1; i >= 0; i--) {
            THM += abs(RQ[i] - initial);
            initial = RQ[i];
        }
    } else {
        for (i = index - 1; i >= 0; i--) {
            THM += abs(RQ[i] - initial);
            initial = RQ[i];
        }
        THM += abs(RQ[i + 1] - 0);
        initial = 0;
        for (i = index; i < n; i++) {
            THM += abs(RQ[i] - initial);
            initial = RQ[i];
        }
    }

    printf("Total Head Movement is: %d\n", THM);
    return 0;
}

5,11,16,20,27,30 m2.c
#include <stdio.h>
#include <mpi.h>
#include <stdlib.h>

void allocate(int a[], int n) {
    int i;
    for (i = 0; i < n; i++) {
        a[i] = rand() % 50;
    }
}

int main(int argc, char *argv[]) {
    int rank, size, n, max = 0, min = 5, count, *a = NULL;
    
    MPI_Init(&argc, &argv);
    MPI_Comm_size(MPI_COMM_WORLD, &size);
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    
    n = atoi(argv[1]);
    printf("\n Rank=%d n=%d\n", rank, n);
    
    count = n / size;
    
    if (rank == 0) {
        a = (int *)malloc(n * sizeof(int));
        allocate(a, n);
    }

    for (int i = 0; i < count; i++) {
        printf("\t%d\n", a[i]);

        if (a[i] > max) max = a[i];
        if (a[i] < min) min = a[i];
    }

    printf("\n Max=%d Min=%d", max, min);
    
    MPI_Finalize();
}

8,14,16,22 conti.c
//Program to implement the contigious allocation method
//of file allocation.

#include <stdio.h>
#include <stdlib.h>
#define SIZE 100

#define NEWNODE (struct direntry *)malloc(sizeof(struct direntry))

struct direntry
{
char fname[14];
int start,count;
struct direntry *next;
}
*dirst=NULL,*dirend=NULL;

int bitvector[SIZE];

void main()
{
int ch1=0,i,j,k,n,flag;
char fname[14];
struct direntry *t1,*t2;
rand()%2;
for(i=0;i<SIZE;i++)
{ bitvector[i]=rand()%2;
}

do
{
  printf("\n\n1. Print Bit Vector");
  printf("\n2. Create File");
  printf("\n3. Print Directory");
  printf("\n4. Exit");
  printf("\nEnter Your Choice : ");
  scanf("%d",&ch1);
  switch(ch1)
  {
    case 1 :
      for(i=0;i<SIZE;i++)
    printf("%4d",bitvector[i]);
      break;
    case 2 :
      if(dirst==NULL)
    dirst=dirend=NEWNODE;
      else
      {
    dirend->next=NEWNODE;
    dirend=dirend->next;
      }
      dirend->next=NULL;
      printf("\nEnter A Filename : ");
      scanf("%s",dirend->fname);
      printf("\nEnter The Number of Blocks To Allocate : ");
      scanf("%d",&n);
      dirend->count=n;
      for(i=0;i<100;i++)
      {
       if(bitvector[i]==1) //found free block
       {
    for(j=i;j<i+n;j++) //find next n free blocks
    {
     if(bitvector[j]!=1)//not free
      break;
    }//for

    if(j==i+n) //found n contiguous free blocks
    {
     dirend->start=i;
     for(k=i;k<j;k++) //allocate block
      bitvector[k]=0;
     break;
    }//if
       }//outer if
      }
      break;
  case 3 :
     printf("\nDirectory : ");
     printf("\n--------------------------");
     printf("\nFilename     Start  Count");
     printf("\n--------------------------");
     for(t1=dirst;t1!=NULL;t1=t1->next)
      printf("\n%-10s %5d %5d",t1->fname,t1->start,t1->count);
     printf("\n--------------------------");
     break;
  case 4 :printf("\n Exit..");
          break;
    
   }
 }while(ch1!=4);

}
