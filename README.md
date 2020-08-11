#include <iostream>
#include <stdlib.h>

using namespace std;

void merge(int arr[], int l, int m, int r)
{
   int i, j, k;
   int sizeofl = m - l + 1;
   int sizeofm = r - m;

   /* create left, right array */
   int L[sizeofl], R[sizeofm];

   /* Copy data to temp arrays L[] and R[] */
   for (i = 0; i < sizeofl; i++)
       L[i] = arr[l + i];
   for (j = 0; j < sizeofm; j++)
       R[j] = arr[m + 1 + j];

  
   i = 0;
   j = 0;
   k = l;
   while (i < sizeofl && j < sizeofm) {
       if (L[i] <= R[j]) {
           arr[k] = L[i];
           i++;
       }
       else {
           arr[k] = R[j];
           j++;
       }
       k++;
   }
   while (i < sizeofl) {
       arr[k] = L[i];
       i++;
       k++;
   }
   while (j < sizeofm) {
       arr[k] = R[j];
       j++;
       k++;
   }
}

void mergeSort(int arr[], int l, int r)
{
   if (l < r) {
       // Same as (l+r)/2, but avoids overflow for
       // large l and h
       int m = l + (r - l) / 2;

       // Sort first and second halves
       mergeSort(arr, l, m);
       mergeSort(arr, m + 1, r);
       merge(arr, l, m, r);
   }
}


/* Driver program */
int main()
{
   int arr_size;
   cout<<"Give the size of array : ";
   cin>>arr_size;
   int arr[arr_size];
   cout<<"Enter Array : ";
   for(int i=0;i<arr_size;i++)
   {
       cin>>arr[i];
   }
   mergeSort(arr, 0, arr_size - 1);

   cout<<"\nSorted array is \n";
   for (int i = 0; i < arr_size; i++)
       cout<<arr[i]<<" ";
   printf("\n");
}


