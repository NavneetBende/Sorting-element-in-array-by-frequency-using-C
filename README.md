Sorting element in array by frequency in C
Here we will learn about Sorting element in array by frequency in C programming language. To sort an array based on its frequency means we need to sort the given element in descending order of their frequency. We are given an array and we have to sort the array based on their frequency.

Sorting element in array by frequency in C
Example

Input :arr[6]=[3, 2, 3, 1, 2, 2]
Output: 2 2 2 3 3 1
Method : 1
First we declare an array.
Declare two 2d array arr[MAX][2] and brr[MAX][2].
Store 1d array in 0th index of arr array.
Set arr[][1] = 0for all indexes upto n.
Now, count the frequency of elements of the array.
If element is unique the push it at brr[][0] array, and its frequency will represent by brr[][1].
Now, sort the brr on the basis of frequency.
Print the brr array on basis of their frequency.
In this method we first count the frequency of each elements, so to know more about the algorithm for finding the frequency of elements of the array. You can check out the page given below,

C Program to Count the Frequency
Related Pages
Sort the elements of an array

Finding the frequency of elements in an array

Finding the Longest Palindrome in an Array

Counting Distinct Elements in an Array

Finding  Repeating elements in an Array

Code in C
Run
#include<stdio.h>
#define MAX 256
int main ()
{
     int a[]={1, 2, 1, 1, 2, 3, 3, 3, 3, 0};
     int n = sizeof(a)/sizeof(a[0]);
     int arr[MAX][2], brr[MAX][2];
     int k = 0, temp, count;
     for (int i = 0; i < n; i++)
     {
        arr[i][0] = a[i];
        arr[i][1] = 0;
     }
     // Unique elements and its frequency are stored in another array
     for (int i = 0; i < n; i++)
     {
         if (arr[i][1])
          continue;
         count = 1;
         for (int j = i + 1; j < n; j++)
         {
             if (arr[i][0] == arr[j][0])
             {
                 arr[j][1] = 1;
                 count++;
             }
         }
         brr[k][0] = arr[i][0];
         brr[k][1] = count;
         k++;
     }
     n = k;

     //Store the array and its frequency in sorted form
     for (int i = 0; i < n - 1; i++)
     {
         temp = brr[i][1];
         for (int j = i + 1; j < n; j++)
         {
             if (temp < brr[j][1])
             {
                temp = brr[j][1];
                brr[j][1] = brr[i][1];
                brr[i][1] = temp;

                temp = brr[j][0];
                brr[j][0] = brr[i][0];
                brr[i][0] = temp;
             }
         }
      }
      for (int i = 0; i < n; i++)
      {
            while (brr[i][1] != 0)
            {
                 printf (" %d ", brr[i][0]);
                 brr[i][1]--;
            }
      }
return 0;
}
Output
3 3 3 3 1 1 1 2 2 0
