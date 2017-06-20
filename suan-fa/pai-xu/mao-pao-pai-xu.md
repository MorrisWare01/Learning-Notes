冒泡排序（Bubble Sort）的基本思想：两两比较待排序记录的关键字，发现两个记录的次序相反时即进行交换，直到没有反序的记录为止。

```
void bubbleSort(int[] A,int n){
    for(int i = n - 1;i > 0;i--){
        for(int j = 0;j < i;j++){
            if(A[j] > A[j + 1]){
                swap(A,j,j+1);
            }            
        }
    }
}

void swap(int[] A,int a,int b){
    int temp = A[a];
    A[a] = A[b];
    A[b] = temp;
}
```



