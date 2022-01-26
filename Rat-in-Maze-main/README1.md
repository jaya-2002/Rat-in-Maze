
#include <stdio.h>
#define N 5
#define true 1
#define false 0

int maze[N][N];     //matrix to store the maze
int solution[N][N];  //matrix to store the solution




//function to print the solution matrix
void printsolution() 
{
 int i,j,cost=0;
 printf("\n\n The Path travelled is Represented by ' 1 ' \n");
 for(i=0;i<N;i++) 
  {  for(j=0;j<N;j++)
      { printf(" %d ",solution[i][j]);
           if(solution[i][j]==1)
              {
                 cost= cost+i+j;
               }
       }
       
     printf("\n");
  }
  
 printf("\n\nCost of this path is: %d",cost); 
}




int solvemaze(int r, int c) {

 if((r==0) && (c==N-1)==1) {
 solution[r][c] = 1;
 return true;
 }
 
 if((r>=0 && r<N )&& (c>=0 && c<N )&& (maze[r][c] == 0&& solution[r][c] == 0)){

 solution[r][c] = 1;          // valid or not
 
 if(solvemaze(r+1, c)==1)     //traversing down
     return true;
 
 if(solvemaze(r, c+1)==1)     //traversing right
     return true;

 if(solvemaze(r-1, c)==1)     //traversing up
     return true;
 
 if(solvemaze(r, c-1)==1)     //traversing left
     return true; 
 
 solution[r][c] = 0;       //backtracking
    return false;
    
 }
 return false;
}



int main() 
{
 
 int i,j;
 
 for(i=0;i<N;i++)
  { for(j=0;j<N;j++)
     { printf("Enter maze[%d][%d]:-",i,j); // entering values into maze matrix
       scanf("%d",&maze[i][j]);
       solution[i][j]=0;                   //making all elements of the solution matrix 0
     }
     printf("\n");
  }
 
 printf("\n The maze you entered is :\n");
 for(i=0;i<N;i++)
  { for(j=0;j<N;j++)
     { printf(" %d ", maze[i][j]);
     }
     printf("\n");
  }
 
 
 
 if (solvemaze(N-1,0)==1)   // if true then call print solution.
      {  
          printsolution();
      }
 else
    {
 printf("\n No solution \n");    // else print No solution.
     } 
     
 return 0;
}


