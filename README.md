// Struct-Array-Char-Sorting
// Sorting with bubble sort method, and with the special case when strcmp(struct1.element1, struct2.element1) == 0

#include<stdio.h>
#include<string.h> // using string.h to generate strcmp() function

// abstract data typr using struct
struct nama{
// with 2 elements
   char name[100];
   char add[100];
};

/* make struct temp for each struct replacement
so that we can allocate the element befor replace it place*/
struct nama temp;

int main(){
   int i,j,n;
   // make struct mhs with size of 100
   struct nama mhs[100];
   
   // enter the limit of names and addresses we want to make
   printf("Enter number of names and addresses :\n");
   scanf("%d",&n);
   //enter the name, thus the address
   printf("Enter names and addresses in any order :\n");
   for(i=0;i<n;i++){
      scanf("%s", &mhs[i].name);
      scanf("%s", &mhs[i].add);
   }
   
   // this is where the fun part begin
   for(i=0;i<n;i++){
      for(j=i+1;j<n;j++){
         if(strcmp(mhs[i].name, mhs[j].name)>0){ // strcmp() < 0 means that mhs[i].name and mhs[j].name elements are not equal
            temp = mhs[i];
            mhs[i] = mhs[j];
            mhs[j] = temp;
         }
         // if something else occur, in this case the value of strcmp == 0
         else if(strcmp(mhs[i].name, mhs[j].name)==0){
         // fortunately if another element such as add (abbreviation of address) has strcmp() of not 0
            if(strcmp(mhs[i].add, mhs[j].add)>0){
               temp = mhs[i];
               mhs[i] = mhs[j];
               mhs[j] = temp;
            }
         }
      }
   }
   // finally, we can print the value of each struct mhs after being sorted
   printf("\nThe sorted order of names are:\n");
   for(i=0;i<n;i++){
      printf("%s\n",mhs[i].name);
      printf("%s\n",mhs[i].add);
   }
   return 0;
}
