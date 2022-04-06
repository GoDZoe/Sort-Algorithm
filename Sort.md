<font size='5'>
# C++算法十大排序
## 1.选择排序  
选择排序算法就是两个遍历，从前往后找到最小值再和当前值交换位置，代码如下：  
```C++
//选择排序
void chooseSort(vector<int>& arr){
    
    int n=arr.size();
    for(int i=0;i<n;++i){
        int mini=i;
        for(int j=i+1;j<n;++j){
            if(arr[mini]>arr[j]) mini=j;
        }
        swap(arr[i],arr[mini]);
    }
}
```  
## 2.冒泡排序 bubbleSort  
冒泡排序就是两个循环遍历，找到最小值交换位置，代码如下:  
```C++
//冒泡排序
void bubbleSort(vector<int>& arr){
    for(int i=0;i<arr.size();++i){
        for(int j=i+1;j<arr.size();++j){
            if(arr[i]>arr[j]){swap(arr[i],arr[j]);}
        }
    }
}
```  
## 3.插入排序  
插入排序就是从当前位置开始往后找，找到一个值插入前面已排好的区域，同时前面的每一个值都往后退一步，代码如下：  
```C++
//插入排序
void insertSort(vector<int>& arr){
    for(int i=1;i<arr.size();++i){
        int key=arr[i];
        int j=i-1;
        while(j>=0&&key<arr[j]){
            arr[j+1]=arr[j];
            j--;
        }
        arr[j+1]=key;
    }
}
```  
## 4.归并排序  
归并排序就是分治，通过dfs将一个序列分成不可再分的地步，再通过解决子问题来解决整体排序问题，代码如下：  
```C++
//归并排序
void merge(vector<int>&,int ,int ,int );  //先声明merge
void mergeSort(vector<int>& arr,int left,int right){
    int mid=left+(right-left)/2;
    if(left<right){
        mergeSort(arr,left,mid); //先处理左边
        mergeSort(arr,mid+1,right); //在处理右边
        merge(arr,left,mid,right);
    }
}

void merge(vector<int>& arr,int left,int mid,int right){
    //临时数组存放这一部分内容
    vector<int> temp(right-left+1);
    int i=left,j=mid+1;
    int index=0;
    while(i<=mid&&j<=right){
        if(arr[i]<arr[j]){
            temp[index++]=arr[i++];
        }else{
            temp[index++]=arr[j++];
        }
    }
    //处理剩下的数据
    while(i<=mid){
        temp[index++]=arr[i++];
    }
    while(j<=right){
        temp[index++]=arr[j++];
    }
    //存放入原数组中
    for(int k=0;k<temp.size();++k){
        arr[left+k]=temp[k];
    }

}
```