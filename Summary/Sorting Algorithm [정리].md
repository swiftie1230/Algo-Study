# Algorithms ✍🏻

<div class="notice--primary" markdown="1">
• Definition    
: An algorithm is a finite set of instructions that accomplishes a particular task.   

• All algorithms must satisfy the following criteria:   
	•	<strong><u>Input</u></strong> : There are zero or more quantities that are externally supplied    
	•	<strong><u>Output</u></strong> : At least one quantity is produced    
	•	<strong><u>Definiteness</u></strong> : Each instruction is clear and unambiguous   
	•	<strong><u>Finiteness</u></strong> : If we trace out the instructions of an algorithm, then for all cases, the algorithm terminates after a finite number of step    
	•	<strong><u>Effectiveness</u></strong> : Every instruction must be basic enough to be carried out. It must be feasible    
</div>



## 📌 Sorting Algorithms

Sorting Algorithms are concepts that every competitive programmer must know. Sorting algorithms can be used for collections of numbers, strings, characters, or a structure of any of these types.   

정렬 알고리즘(sorting algorithm)이란 원소들을 번호순이나 사전 순서와 같이 일정한 순서대로 열거하는 알고리즘이다.   
효율적인 정렬은 탐색이나 병합 알고리즘처럼 (정렬된 리스트에서 바르게 동작하는) 다른 알고리즘을 최적화하는 데 중요하다. 또 정렬 알고리즘은 데이터의 정규화나 의미있는 결과물을 생성하는 데 흔히 유용하게 쓰인다. 이 알고리즘의 결과는 반드시 다음 두 조건을 만족해야 한다.

1. 출력은 비 내림차순(각각의 원소가 전 순서 원소에 비해 이전의 원소보다 작지 않은 순서)이다.   
2. 출력은 입력을 재배열하여 만든 순열이다.    

대부분 정렬의 시간복잡도는 <strong><u>O(n*logn)와 O(n^2)사이</u></strong>임. 
특별한 경우 O(n)까지 가능.

Internal sorting – main memory에서 일어나는 정렬
External sorting – secondary storage(하드디스크)에서 일어나는 정렬


## 📌 Sorting Algorithm methods

**<u>Merge Sort</u>** and **<u>Quick Sort</u>** are the most popular algorithms.

### [1] Bubble Sort

Bubble sort is based on the idea of repeatedly comparing pairs of adjacent elements and then swapping their positions if they exist in the wrong order.   

<img width="206" alt="image" src="https://user-images.githubusercontent.com/63195670/149430315-b2b532ec-6ad4-427d-8a59-d60bbaec0044.png">

이웃되는 값끼리 비교하여 자리를 변경해나가는 방식!    
약간 남아있는 비교 대상 중 가장 큰 값을 마지막에 배치하는 것을 반복하는 느낌이라고 생각하면 될 듯?   

#### 🔮 Implementation

Assume that 
A[] is an unsorted array of n elements. This array needs to be sorted in ascending order. The pseudo code is as follows:

```cpp
void bubble_sort( int A[ ], int n ) {
    int temp;
    for(int k = 0; k< n-1; k++) {
        // (n-k-1) is for ignoring comparisons of elements which have already been compared in earlier iterations

        for(int i = 0; i < n-k-1; i++) {
            if(A[ i ] > A[ i+1 ] ) {
                // here swapping of positions is being done.
                temp = A[ i ];
                A[ i ] = A[ i+1 ];
                A[ i + 1 ] = temp;
            }
        }
    }
}
```

Lets try to understand the pseudo code with an example: A [ ] = { 7, 4, 5, 2 }   

<img width="710" alt="Screen Shot 2022-01-14 at 9 38 13 AM" src="https://user-images.githubusercontent.com/63195670/149431193-f674e858-9e3c-4745-ae9a-8f0d6910946c.png">

#### 🔮 Performance 

The complexity of bubble sort is O(n^2) in both worst and average cases, because the entire array needs to be iterated for every element.   

→ 기본적으로 O(n^2). 이미 정렬이 되어 있을 경우는 O(n).  


### [2] Selection Sort

The Selection sort algorithm is based on the idea of finding the minimum or maximum element in an unsorted array and then putting it in its correct position in a sorted array.   

Assume that the array A = [7, 5, 4, 2] needs to be sorted in ascending order.

The minimum element in the array (i.e. 2) is searched for and then swapped with the element that is currently located at the first position (i.e. 7). Now the minimum element in the remaining unsorted array is searched for and put in the second position, and so on.    

<img width="202" alt="image" src="https://user-images.githubusercontent.com/63195670/149432662-7f609e0a-1360-47a5-a4cb-de442cd3e645.png">

또는 array에서 가장 큰 수를 찾은 다음, 찾은 수를 어레이의 맨 끝인 n자리에 놓는다. 
다음 큰 수를 찾은 다음, 어레이의 n-1자리에 넣는다. 이 때 찾은 수와 해당 자리에 있는 수의 자리를 바꾼다.   

#### 🔮 Implementation 

```cpp
void selection_sort (int A[ ], int n) {
        // temporary variable to store the position of minimum element

        int minimum;        
        // reduces the effective size of the array by one in  each iteration.

        for(int i = 0; i < n-1 ; i++)  {

           // assuming the first element to be the minimum of the unsorted array .
             minimum = i ;

          // gives the effective size of the unsorted  array .

            for(int j = i+1; j < n ; j++ ) {
                if(A[ j ] < A[ minimum ])  {                //finds the minimum element
                minimum = j ;
                }
             }
          // putting minimum element on its proper position.
          swap ( A[ minimum ], A[ i ]) ; 
        }
   }
```
At ith iteration, elements from position 0 to i-1 will be sorted.   

<img width="697" alt="Screen Shot 2022-01-14 at 10 00 05 AM" src="https://user-images.githubusercontent.com/63195670/149433085-35f3e3b5-5f59-443e-874e-48717d5ea68f.png">

#### 🔮 Performance 

To find the minimum element from the array of N elements, N − 1 comparisons are required. After putting the minimum element in its proper position, the size of an unsorted array reduces to  
N − 1 and then N − 2 comparisons are required to find the minimum in the unsorted array.

Therefore (N − 1) + (N − 2) + ....... +  1 = (N ⋅ (N − 1))/2 comparisons and N swaps result in the overall complexity of O(N^2).

O(n^2)의 performance가 나옴. -> bubble sort와 똑같이 O(n^2)이지만 bubble sort에 비해 값의 교환 수가 적음. 이미 정렬이 되어 있어도 O(n^2)임.   


### [3] Insertion Sort

Insertion sort is based on the idea that one element from the input elements is consumed in each iteration to find its correct position i.e, the position to which it belongs in a sorted array.

It iterates the input elements by growing the sorted array at each iteration. It compares the current element with the largest value in the sorted array. If the current element is greater, then it leaves the element in its place and moves on to the next element else it finds its correct position in the sorted array and moves it to that position. This is done by shifting all the elements, which are larger than the current element, in the sorted array to one position ahead

<img width="199" alt="image" src="https://user-images.githubusercontent.com/63195670/149433655-9c2bfee1-6582-47c0-b496-9db14220583a.png">

새로운 키를 넣을 때, 정렬을 하고 있는 array에서 자신이 어디에 들어가야 할지 결정한 다음 맞는 자리에 넣는다.

#### 🔮 Implementation 

```cpp
void insertion_sort (int A[ ], int n) 
{
     for( int i = 0 ;i < n ; i++ ) {
    /*storing current element whose left side is checked for its 
             correct position .*/

	      int temp = A[ i ];    
	      int j = i;

       /* check whether the adjacent element in left side is greater or
            less than the current element. */

          while( j > 0  && temp < A[ j -1 ]) {

           // moving the left side element to one position forward.
                A[ j ] = A[ j-1 ];   
                j= j - 1;

           }
         // moving current element to its  correct position.
           A[ j ] = temp;       
     }  
}
```
Take array A[] = [7,4,5,2].   

<img width="700" alt="Screen Shot 2022-01-14 at 10 14 26 AM" src="https://user-images.githubusercontent.com/63195670/149434276-3b893c69-6e15-46a3-9733-f287538d99d6.png">   


#### 🔮 Performance 

In worst case,each element is compared with all the other elements in the sorted array. For N elements, there will be N^2 comparisons. Therefore, the time complexity is O(n^2).

→ O(n^2). 이미 모든 키가 정렬되어 있으면 O(n)  
짧은 list에서 단순하고 좋음.   
이미 부분적으로 정렬이 되어 있는 경우에 좋다.   


<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>Selection Sort vs Insertion Sort</u></strong>   

Selection sort는 정렬되어 있지 않은 수를 전부 확인해 가장 큰 수를 찾아야 함. 정렬이 전부 되어 있어도 모든 수를 비교!     
Insertion sort는 정확한 위치에 들어가는 것을 결정하기 위해 정렬 중인 array를 확인해야 함. 필요한 값만 읽고 정렬된 리스트에서 비교!   

N개의 element가 있다고 가정할 때,  Selection은 n번만 쓰면 됨. 뒤에서부터 쓰기 때문에 어레이의 key들이 이동할 필요가 없지만, Insertion은 key들이 전부 이동할 수도 있기 때문에 write가 더 많이 일어남. 
예를 들어, 2, 3, 4, 5, 1의 값을 insertion sort로 정렬한다고 하면, 마지막 1을 정렬하기 위해 2, 3, 4, 5의 값이 한 칸씩 이동해야 함.
만약 write비용이 비쌀 경우 (예를 들어 flash memory) insertion sort보단 selection sort가 더 좋음.
</div>


<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>SUMMARY (Bubble, selection, insertion sort)</u></strong> 

Bubble, selection, insertion sort의 시간복잡도 worst case는 O(n^2).   
만약 전부 정렬된 리스트를 비교한다면 bubble, insertion sort는 O(n)이지만 selection은 여전히 O(n^2).
</div>


### [4] Merge Sort

Merge sort is a **<u>divide-and-conquer algorithm</u> based on the idea of <u>breaking down a list into several sub-lists</u> until each sublist consists of a <u>single element</u> and merging those sublists in a manner that results into a sorted list.**

**<u>Idea</u>**:

- Divide the unsorted list into N sublists, each containing 1 element.
- Take adjacent pairs of two singleton lists and merge them to form a list of 2 elements. N will now convert into N/2 lists of size 2.
- Repeat the process till a single sorted list of obtained.

**<u>과정 설명</u>** : 

- 리스트의 길이가 0 또는 1이면 이미 정렬된 것으로 본다. 그렇지 않은 경우에는
- 정렬되지 않은 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다.
- 각 부분 리스트를 재귀적으로 합병 정렬을 이용해 정렬한다.
- 두 부분 리스트를 다시 하나의 정렬된 리스트로 합병한다.

1. 분할(Divide): 입력 배열을 같은 크기의 2개의 부분 배열로 분할한다.

2. 정복(Conquer): 부분 배열을 정렬한다. 부분 배열의 크기가 충분히 작지 않으면 순환 호출을 이용하여 다시 분할 정복 방법을 적용한다.

3. 결합(Combine): 정렬된 부분 배열들을 하나의 배열에 합병한다.


While comparing two sublists for merging, the first element of both lists is taken into consideration. While sorting in ascending order, the element that is of a lesser value becomes a new element of the sorted list. This procedure is repeated until both the smaller sublists are empty and the new combined sublist comprises all the elements of both the sublists.

<img width="713" alt="Screen Shot 2022-01-14 at 10 31 27 AM" src="https://user-images.githubusercontent.com/63195670/149435842-e0efc4b6-ce1e-460c-887c-5d16039b1d63.png">

#### 🔮 Implementation 

```cpp
void merge(int A[ ] , int start, int mid, int end) {
 //stores the starting position of both parts in temporary variables.
	int p = start ,q = mid+1;
	
	int Arr[end-start+1] , k=0;
	
	for(int i = start ;i <= end ;i++) {
	    if(p > mid)      //checks if first part comes to an end or not .
	       Arr[ k++ ] = A[ q++] ;
	
	   else if ( q > end)   //checks if second part comes to an end or not
	       Arr[ k++ ] = A[ p++ ];
	
	   else if( A[ p ] < A[ q ])     //checks which part has smaller element.
	      Arr[ k++ ] = A[ p++ ];
	
	   else
	      Arr[ k++ ] = A[ q++];
	 }
	  for (int p=0 ; p< k ;p ++) {
	   /* Now the real array has elements in sorted manner including both 
	        parts.*/
	     A[ start++ ] = Arr[ p ] ;                          
	  }
}
```

💡 **<u>2개의 정렬된 리스트를 합병(merge)하는 과정</u>**

1. 2개의 리스트의 값들을 처음부터 하나씩 비교하여 두 개의 리스트의 값 중에서 더 작은 값을 새로운 리스트(sorted)로 옮긴다.

2. 둘 중에서 하나가 끝날 때까지 이 과정을 되풀이한다.

3. 만약 둘 중에서 하나의 리스트가 먼저 끝나게 되면 나머지 리스트의 값들을 전부 새로운 리스트(sorted)로 복사한다.

4. 새로운 리스트(sorted)를 원래의 리스트(list)로 옮긴다.


2 branched recursive function :

```cpp
void merge_sort (int A[ ] , int start , int end )
{
	if( start < end ) {
		int mid = (start + end ) / 2 ;           // defines the current array in 2 parts .
		merge_sort (A, start , mid ) ;                 // sort the 1st part of array .
		merge_sort (A,mid+1 , end ) ;              // sort the 2nd part of array.

         // merge the both parts by comparing elements of both the parts.
          merge(A,start , mid , end );   
   }                    
}
```

#### 🔮 합병 정렬 (merge sort) 알고리즘의 특징

💬 **<u>단점</u>**  

- 만약 레코드를 **<u>배열(Array)</u>**로 구성하면, 임시 배열이 필요하다.   
	- **<u>제자리 정렬(in-place sorting)</u>**이 아니다.   
- 레크드들의 크기가 큰 경우에는 이동 횟수가 많으므로 매우 큰 시간적 낭비를 초래한다.    

💬 **<u>장점</u>**

- 안정적인 정렬 방법   
	- 데이터의 분포에 영향을 덜 받는다. 즉, 입력 데이터가 무엇이든 간에 정렬되는 시간은 동일하다. (O(nlog₂n)로 동일)   
- 만약 레코드를 **<u>연결 리스트(Linked List)</u>**로 구성하면, 링크 인덱스만 변경되므로 **<u>데이터의 이동은 무시할 수 있을 정도로 작아진다</u>**.   
	- **<u>제자리 정렬(in-place sorting)로 구현</u>**할 수 있다.   
- 따라서 **크기가 큰 레코드를 정렬할 경우에 <u>연결 리스트를 사용</u>한다면, 합병 정렬은 퀵 정렬을 포함한 <u>다른 어떤 졍렬 방법보다 효율적</u>이다.**   


#### 🔮 Performance 

The list of size N is divided into a max of logN parts, and the merging of all sublists into a single list takes O(N) time, the worst case run time of this algorithm is <strong><u>O(N*logN)</u></strong>

- **<u>분할 단계</u>**
	- 비교 연산과 이동 연산이 수행되지 않는다.
- **<u>합병 단계</u>**
	- **<u>비교 횟수</u>**   
		<img width="475" alt="Screen Shot 2022-01-17 at 1 09 29 PM" src="https://user-images.githubusercontent.com/63195670/149706814-5875246c-c8a9-421c-af2f-a05f259d92ef.png">   

		- 순환 호출의 깊이 (합병 단계의 수)
			- 레코드의 개수 n이 2의 거듭제곱이라고 가정(n=2^k)했을 때, **<u>n=2^3의 경우</u>**, 2^3 -> 2^2 -> 2^1 -> 2^0 순으로 줄어들어 순환 호출의 깊이가 3임을 알 수 있다. 이것을 일반화하면 **n=2^k의 경우, <u>k(k=log₂n)</u>임**을 알 수 있다.
			- **<u>k=log₂n</u>**

		- 각 합병 단계의 비교 연산
			- 크기 1인 부분 배열 2개를 합병하는 데는 최대 2번의 비교 연산이 필요하고, 부분 배열의 쌍이 4개이므로 24=8번의 비교 연산이 필요하다. 다음 단계에서는 크기 2인 부분 배열 2개를 합병하는 데 최대 4번의 비교 연산이 필요하고, 부분 배열의 쌍이 2개이므로 4X2=8번의 비교 연산이 필요하다. 마지막 단계에서는 크기 4인 부분 배열 2개를 합병하는 데는 최대 8번의 비교 연산이 필요하고, 부분 배열의 쌍이 1개이므로 8X1=8번의 비교 연산이 필요하다. 이것을 일반화하면 하나의 합병 단계에서는 최대 n번의 비교 연산을 수행함을 알 수 있다.
			- **<u>최대 n번</u>**
		- 순환 호출의 깊이 만큼의 합병 단계 * 각 합병 단계의 비교 연산 = **<u>nlog₂n</u>**

	- **<u>이동 횟수</u>**
		- 순환 호출의 깊이 (합병 단계의 수)
			- k=log₂n
		- 각 합병 단계의 이동 연산
			- 임시 배열에 복사했다가 다시 가져와야 되므로 이동 연산은 총 부분 배열에 들어 있는 요소의 개수가 n인 경우, 레코드의 이동이 2n번 발생한다.
		- 순환 호출의 깊이 만큼의 합병 단계 * 각 합병 단계의 이동 연산 = 2nlog₂n
- T(n) = nlog₂n(비교) + 2nlog₂n(이동) = 3nlog₂n = **<u>O(nlog₂n)</u>**



### [5] Quick Sort

Quick sort is based on the divide-and-conquer approach based on the idea of **<u>choosing one element as a pivot element and partitioning the array around it</u>** such that: Left side of pivot contains all the elements that are less than the pivot element Right side contains all elements greater than the pivot

It reduces the space complexity and removes the use of the auxiliary array that is used in merge sort. Selecting a random pivot in an array results in an improved time complexity in most of the cases.

- 분할 정복 알고리즘의 하나로, 평균적으로 매우 빠른 수행 속도를 자랑하는 정렬 방법
	- 합병 정렬(merge sort)과 달리 퀵 정렬은 리스트를 비균등하게 분할한다.
	
	
**<u>과정 설명</u>** :    

- 리스트 안에 있는 한 요소를 선택한다. 이렇게 고른 원소를 피벗(pivot) 이라고 한다.
- 피벗을 기준으로 피벗보다 작은 요소들은 모두 피벗의 왼쪽으로 옮겨지고 피벗보다 큰 요소들은 모두 피벗의 오른쪽으로 옮겨진다. (피벗을 중심으로 왼쪽: 피벗보다 작은 요소들, 오른쪽: 피벗보다 큰 요소들)
- 피벗을 제외한 왼쪽 리스트와 오른쪽 리스트를 다시 정렬한다.
	- 분할된 부분 리스트에 대하여 순환 호출 을 이용하여 정렬을 반복한다.
	- 부분 리스트에서도 다시 피벗을 정하고 피벗을 기준으로 2개의 부분 리스트로 나누는 과정을 반복한다.
- 부분 리스트들이 더 이상 분할이 불가능할 때까지 반복한다.
	- 리스트의 크기가 0이나 1이 될 때까지 반복한다.

1. 분할(Divide): 입력 배열을 피벗을 기준으로 비균등하게 2개의 부분 배열(피벗을 중심으로 왼쪽: 피벗보다 작은 요소들, 오른쪽: 피벗보다 큰 요소들)로 분할한다.   
2. 정복(Conquer): 부분 배열을 정렬한다. 부분 배열의 크기가 충분히 작지 않으면 순환 호출 을 이용하여 다시 분할 정복 방법을 적용한다.   
3. 결합(Combine): 정렬된 부분 배열들을 하나의 배열에 합병한다.    

순환 호출이 한번 진행될 때마다 최소한 하나의 원소(피벗)는 최종적으로 위치가 정해지므로, 이 알고리즘은 반드시 끝난다는 것을 보장할 수 있다.   

#### 🔮 Implementation 


**A[]** : array whose elements are to be sorted

**start** : Leftmost position of the array

**end** : Rightmost position of the array

**i** : Boundary between the elements that are less than pivot and those greater than pivot

**j** : Boundary between the partitioned and unpartitioned part of array

**piv** : Pivot element

```cpp
int partition ( int A[],int start ,int end) {
    int i = start + 1;
    int piv = A[start] ;            //make the first element as pivot element.
    for(int j =start + 1; j <= end ; j++ )  {
    /*rearrange the array by putting elements which are less than pivot
       on one side and which are greater that on other. */

          if ( A[ j ] < piv) {
                 swap (A[ i ],A [ j ]);
            i += 1;
        }
   }
   swap ( A[ start ] ,A[ i-1 ] ) ;  //put the pivot element in its proper place.
   return i-1;                      //return the position of the pivot
}
```

the recursive function Quick_sort :

```cpp
void quick_sort ( int A[ ] ,int start , int end ) {
   if( start < end ) {
        //stores the position of pivot element
         int piv_pos = partition (A,start , end ) ;     
         quick_sort (A,start , piv_pos -1);    //sorts the left side of pivot.
         quick_sort ( A,piv_pos +1 , end) ; //sorts the right side of pivot.
   }
}
```

Here we find the proper position of the pivot element by rearranging the array using partition function. Then we divide the array into two halves left side of the pivot (elements less than pivot element) and right side of the pivot (elements greater than pivot element) and apply the same step recursively.

Below `randpartition()` function chooses pivot randomly.

Let’s see the randomized version of the partition function :

```cpp
int rand_partition ( int A[ ] , int start , int end ) {
    //chooses position of pivot randomly by using rand() function .
     int random = start + rand( )%(end-start +1 ) ;

      swap ( A[random] , A[start]) ;        //swap pivot with 1st element.
     return partition(A,start ,end) ;       //call the above partition function
}
```
Use randpartiton() instead of partition() function in quicksort() function to reduce the time complexity of this algorithm!    


#### 🔮 퀵 (Quick sort) 알고리즘의 특징

💬 **<u>단점</u>**  

- 정렬된 리스트에 대해서는 퀵 정렬의 불균형 분할에 의해 오히려 수행시간이 더 많이 걸린다.

💬 **<u>장점</u>**   

- 속도가 빠르다.
	- 시간 복잡도가 O(nlog₂n)를 가지는 다른 정렬 알고리즘과 비교했을 때도 가장 빠르다.
- 추가 메모리 공간을 필요로 하지 않는다.
	- 퀵 정렬은 O(log n)만큼의 메모리를 필요로 한다.

💬 퀵 정렬의 불균형 분할을 방지하기 위하여 피벗을 선택할 때 더욱 리스트를 균등하게 분할할 수 있는 데이터를 선택한다.

- EX) 리스트 내의 몇 개의 데이터 중에서 크기순으로 중간 값(medium)을 피벗으로 선택한다.



#### 🔮 Performance 

The worst case time complexity of this algorithm is O(N^2), but as this is randomized algorithm, its time complexity fluctuates between O(N^2) and O(NlogN) and mostly it comes out to be O(NlogN).

- **<u>최선의 경우</u>**
	- **<u>비교 횟수</u>**   
		<img width="463" alt="Screen Shot 2022-01-17 at 1 36 46 PM" src="https://user-images.githubusercontent.com/63195670/149708777-c59b0a5d-9143-4938-8c0c-a1f34d80510f.png">   

		- 순환 호출의 깊이
			- 레코드의 개수 n이 2의 거듭제곱이라고 가정(n=2^k)했을 때, n=2^3의 경우, 2^3 -> 2^2 -> 2^1 -> 2^0 순으로 줄어들어 순환 호출의 깊이가 3임을 알 수 있다. 이것을 일반화하면 n=2^k의 경우, **<u>k(k=log₂n)</u>**임을 알 수 있다.
			- **<u>k=log₂n</u>**
		- 각 순환 호출 단계의 비교 연산
			- 각 순환 호출에서는 전체 리스트의 대부분의 레코드를 비교해야 하므로 평균 n번 정도의 비교가 이루어진다.
			- **<u>평균 n번</u>**
		- 순환 호출의 깊이 * 각 순환 호출 단계의 비교 연산 = **<u>nlog₂n</u>**
	- **<u>이동 횟수</u>**
		- **비교 횟수보다 적으므로 <u>무시할 수 있다</u>**.
	- 최선의 경우 T(n) = O(nlog₂n)

- **<u>최악의 경우</u>**
	: 리스트가 계속 불균형하게 나누어지는 경우 (특히, 이미 정렬된 리스트에 대하여 퀵 정렬을 실행하는 경우)   

	<img width="283" alt="Screen Shot 2022-01-17 at 1 37 26 PM" src="https://user-images.githubusercontent.com/63195670/149708838-25f7ac6d-1f57-46aa-b4e6-98d7c5a411e3.png">   

	- **<u>비교 횟수</u>**
		- 순환 호출의 깊이
			- 레코드의 개수 n이 2의 거듭제곱이라고 가정(n=2^k)했을 때, 순환 호출의 깊이는 n임을 알 수 있다.
			- **<u>n</u>**
		- 각 순환 호출 단계의 비교 연산
			- 각 순환 호출에서는 전체 리스트의 대부분의 레코드를 비교해야 하므로 평균 n번 정도의 비교가 이루어진다.
			- **<u>평균 n번</u>**
		- 순환 호출의 깊이 * 각 순환 호출 단계의 비교 연산 = **<u>n^2</u>**
	- **<u>이동 횟수</u>**
		- 비교 횟수보다 적으므로 무시할 수 있다.
		- 최악의 경우 **<u>T(n) = O(n^2)</u>**

- **<u>평균</u>**
	- 평균 T(n) = <u>O(nlog₂n)</u>
	- 시간 복잡도가 O(nlog₂n)를 가지는 다른 정렬 알고리즘과 비교했을 때도 가장 빠르다.
	- 퀵 정렬이 **불필요한 데이터의 이동을 줄이고 먼 거리의 데이터를 교환할 뿐만 아니라, 한 번 결정된 피벗들이 추후 연산에서 제외되는 특성** 때문이다.




### [6] Heap Sort

Heaps can be used in sorting an array. In max-heaps, maximum element will always be at the root. Heap Sort uses this property of heap to sort the array.   

Consider an array Arr which is to be sorted using Heap Sort.   

최대 힙 트리나 최소 힙 트리를 구성해 정렬을 하는 방법
내림차순 정렬을 위해서는 최대 힙을 구성하고 오름차순 정렬을 위해서는 최소 힙을 구성하면 된다.

**<u>Idea</u>**:   

- **<u>Initially build a max heap</u> of elements in Arr.**
- The root element, that is Arr[1], will contain maximum element of Arr. After that, swap this element with the last element of Arr and heapify the max heap excluding the last element which is already in its correct position and then decrease the length of heap by one.
- Repeat the step 2, until all the elements are in their correct position.   

**<u>과정 설명</u>** : 

- 정렬해야 할 n개의 요소들로 최대 힙(완전 이진 트리 형태)을 만든다.
	- 내림차순을 기준으로 정렬
- 그 다음으로 한 번에 하나씩 요소를 힙에서 꺼내서 배열의 뒤부터 저장하면 된다.
- 삭제되는 요소들(최댓값부터 삭제)은 값이 감소되는 순서로 정렬되게 된다.


#### 🔮 Implementation 

```cpp
void heap_sort(int Arr[ ])

{
	int heap_size = N;
	build_maxheap(Arr);
	for(int i = N; i >= 2 ; i-- )
	{
		swap|(Arr[ 1 ], Arr[ i ]);
		heap_size = heap_size - 1;
		max_heapify(Arr, 1, heap_size);
	}
}
```


#### 🔮 힙 정렬 (Heap sort) 알고리즘의 특징  

💬 **<u>장점</u>**

- 시간 복잡도가 좋은편
- 힙 정렬이 가장 유용한 경우는 전체 자료를 정렬하는 것이 아니라 가장 큰 값 몇개만 필요할 때 이다.



#### 🔮 Performance 

max_heapify has complexity O(logN), bulid_maxheap has complexity O(N) and we run max_heapify N-1 times in heap_sort function, therefore complexity of heap_sort function is O(NlogN).

시간복잡도를 계산한다면, 

- 힙 트리의 전체 높이가 거의 log₂n(완전 이진 트리이므로)이므로 하나의 요소를 힙에 삽입하거나 삭제할 때 힙을 재정비하는 시간이 log₂n만큼 소요된다.
- 요소의 개수가 n개 이므로 전체적으로 O(nlog₂n)의 시간이 걸린다.
- T(n) = O(nlog₂n)



### [7] Shell Sort

오름차순을 기준으로 정렬한다.

- ‘Donald L. Shell’이라는 사람이 제안한 방법으로, 삽입정렬을 보완한 알고리즘이다.
- 삽입 정렬이 어느 정도 정렬된 배열에 대해서는 대단히 빠른 것에 착안
	- 삽입 정렬의 최대 문제점: 요소들이 삽입될 때, 이웃한 위치로만 이동
	- 즉, 만약 삽입되어야 할 위치가 현재 위치에서 상당히 멀리 떨어진 곳이라면 많은 이동을 해야만 제자리로 갈 수 있다.
	- 삽입 정렬과 다르게 셸 정렬은 전체의 리스트를 한 번에 정렬하지 않는다.

**<u>과정 설명</u>** : 

- 먼저 정렬해야 할 리스트를 일정한 기준에 따라 분류
- 연속적이지 않은 여러 개의 부분 리스트를 생성
- 각 부분 리스트를 삽입 정렬을 이용하여 정렬
- 모든 부분 리스트가 정렬되면 다시 전체 리스트를 더 적은 개수의 부분 리스트로 만든 후에 알고리즘을 반복
- 위의 과정을 부분 리스트의 개수가 1이 될 때까지 반복


#### 🔮 Implementation 

- 정렬해야 할 리스트의 각 k번째 요소를 추출해서 부분 리스트를 만든다. 이때, k를 ‘간격(gap)’ 이라고 한다.
	- 간격의 초깃값: (정렬할 값의 수)/2
	- **생성된 부분 리스트의 개수는 gap과 같다.**
- **각 회전마다 간격 k를 <u>절반으로 줄인다</u>.** 즉, 각 회전이 반복될 때마다 하나의 부분 리스트에 속한 값들의 개수는 증가한다.
	- **간격은 <u>홀수</u>로 하는 것**이 좋다.
	- 간격을 절반으로 줄일 때 짝수가 나오면 +1을 해서 홀수로 만든다.
- 간격 k가 1이 될 때까지 반복한다.   

<img width="349" alt="Screen Shot 2022-01-17 at 3 18 42 PM" src="https://user-images.githubusercontent.com/63195670/149717751-46d88ed4-e303-465c-9a75-e5f395d2d522.png">    

```cpp
# include <stdio.h>
# define MAX_SIZE 10

// gap만큼 떨어진 요소들을 삽입 정렬
// 정렬의 범위는 first에서 last까지
void inc_insertion_sort(int list[], int first, int last, int gap){
  int i, j, key;

  for(i=first+gap; i<=last; i=i+gap){
    key = list[i]; // 현재 삽입될 숫자인 i번째 정수를 key 변수로 복사

    // 현재 정렬된 배열은 i-gap까지이므로 i-gap번째부터 역순으로 조사한다.
    // j 값은 first 이상이어야 하고
    // key 값보다 정렬된 배열에 있는 값이 크면 j번째를 j+gap번째로 이동
    for(j=i-gap; j>=first && list[j]>key; j=j-gap){
      list[j+gap] = list[j]; // 레코드를 gap만큼 오른쪽으로 이동
    }

    list[j+gap] = key;
  }
}

// 셸 정렬
void shell_sort(int list[], int n){
  int i, gap;

  for(gap=n/2; gap>0; gap=gap/2){
    if((gap%2) == 0)(
      gap++; // gap을 홀수로 만든다.
    )

    // 부분 리스트의 개수는 gap과 같다.
    for(i=0; i<gap; i++){
      // 부분 리스트에 대한 삽입 정렬 수행
      inc_insertion_sort(list, i, n-1, gap);
    }
  }
}

void main(){
  int i;
  int n = MAX_SIZE;
  int list[n] = {10, 8, 6, 20, 4, 3, 22, 1, 0, 15, 16};

  // 셸 정렬 수행
  shell_sort(list, n);

  // 정렬 결과 출력
  for(i=0; i<n; i++){
    printf("%d\n", list[i]);
  }
}
https://gmlwjd9405.github.io/2018/05/08/algorithm-shell-sort.html
```

#### 🔮 셸 정렬 (shell sort) 알고리즘의 특징   

💬 **<u>장점</u>**

- 연속적이지 않은 부분 리스트에서 자료의 교환이 일어나면 더 큰 거리를 이동한다. 따라서 교환되는 요소들이 삽입 정렬보다는 최종 위치에 있을 가능성이 높아진다.

- 부분 리스트는 어느 정도 정렬이 된 상태이기 때문에 부분 리스트의 개수가 1이 되게 되면 셸 정렬은 기본적으로 삽입 정렬을 수행하는 것이지만 삽입 정렬보다 더욱 빠르게 수행된다.

- 알고리즘이 간단하여 프로그램으로 쉽게 구현할 수 있다.



#### 🔮 Performance 

The list of size N is divided into a max of logN parts, and the merging of all sublists into a single list takes O(N) time, the worst case run time of this algorithm is <strong><u>O(N*logN)</u></strong>

시간복잡도를 계산한다면,

- 평균: T(n) = **<u>O(n^1.5)</u>**
- 최악의 경우: T(n) = **<u>O(n^2)</u>**



<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>정렬 알고리즘 시간복잡도 비교</u></strong>   

<img width="555" alt="Screen Shot 2022-01-17 at 1 19 30 PM" src="https://user-images.githubusercontent.com/63195670/149707448-e51a68ea-e42b-4d91-ada2-d78b6984ef1d.png">    

- 단순(구현 간단)하지만 비효율적인 방법 : 삽입 정렬, 선택 정렬, 버블 정렬        
- 복잡하지만 효율적인 방법 : 퀵 정렬, 힙 정렬, 합병 정렬, 기수 정렬
</div>


Sorting Algorithm은 여기서 끝 〰️
	
	
### 🔗 출처	
* [Sorting Algorithms 참고 사이트 1](https://www.hackerearth.com/practice/algorithms/sorting/bubble-sort/practice-problems/)
* [Sorting Algorithms 참고 사이트 2](https://gmlwjd9405.github.io)
* 2학년 1학기 때 배운 자료구조 자료..! 
