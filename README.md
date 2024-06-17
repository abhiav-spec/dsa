# dsa
This is simplest code of mergesort.
#include <iostream>
using namespace std;

void merge(int arr[],int s,int e){
   int mid = (s+e)/2;

    int len1 = mid - s + 1;
    int len2 = e - mid;

    int *first = new int[len1];
    int *second = new int[len2];

    
    int mainArrayIndex = s;
    for(int i=0; i<len1; i++) {
        first[i] = arr[mainArrayIndex++];
    }

    mainArrayIndex = mid+1;
    for(int i=0; i<len2; i++) {
        second[i] = arr[mainArrayIndex++];
    }

   
    int index1 = 0;
    int index2 = 0;
    mainArrayIndex = s;

    while(index1 < len1 && index2 < len2) {
        if(first[index1] < second[index2]) {
            arr[mainArrayIndex++] = first[index1++];
        }
        else{
            arr[mainArrayIndex++] = second[index2++];
        }
    }   

    while(index1 < len1) {
        arr[mainArrayIndex++] = first[index1++];
    }

    while(index2 < len2 ) {
        arr[mainArrayIndex++] = second[index2++];
    }

    delete []first;
    delete []second;

 
}


 void mergesort(int a[],int s,int e){
     
     if(s>=e){
         return;
     }
     int mid =(s+e)/2;
     
     mergesort(a,s,mid);
     
     mergesort(a,mid+1,e);
     
     merge(a,s,e);
 }
int main() {
   int x;
   cout<<"enter the length of array  : ";
   cin>>x;
   
   int a[x];
   cout<<"enter the  elements of array ."<<endl;
   for(int i=0;i<x;i++){
       cout<<"enter : ";
       cin>>a[i];
   }

cout<<"array : "<<endl;
for(int i=0;i<x;i++){
     cout<<a[i];
}
    return 0;
}

