# lecture-64
#include <iostream>
using namespace std;
void merge(int *arr, int start, int end){
    int mid = (start+end)/2;
    int len1, len2;
    len1 = mid -start +1;
    len2 = end-mid;
    int *arr1 = new int[len1];
    int *arr2 = new int[len2];
    int mainindex=start;
    int i ;
    for(i=0;i<len1;i++){
        arr1[i] = arr[mainindex];
        mainindex++;
    }
    for(i =0; i<len2;i++){
        arr2[i] = arr[mainindex];
        mainindex++;
    }

    int index_1, index_2;
    index_1 = 0 ;
    index_2 = 0;
    mainindex = start ;
    while(index_1<len1 && index_2<len2){
        if(arr1[index_1]<arr2[index_2]){
            arr[mainindex]=arr1[index_1];
            mainindex++;
            index_1++;
        }
        else{
            arr[mainindex]=arr2[index_2];
            mainindex++;
            index_2++;
        }
    }
    while(index_1<len1){
        arr[mainindex]=arr1[index_1];
            mainindex++;
            index_1++;
    }
    while(index_2<len2){
        arr[mainindex]=arr2[index_2];
            mainindex++;
            index_2++;
    }
}
void mergeSort(int *arr, int start, int end){
    if(start>=end){
        return;
    }   
    int mid;
    mid= (start+end)/2;
    mergeSort(arr,start,mid);
    mergeSort(arr,mid+1,end);
    merge(arr,start,end);
}
int main(){
    int size;

    int arr[5]= {1,5,3,10,4};
    size = 5;
    mergeSort(arr,0,size-1);
    int k ;
    for( k = 0; k<size;k++){
        cout<<arr[k]<<" ";
    }
    

}
