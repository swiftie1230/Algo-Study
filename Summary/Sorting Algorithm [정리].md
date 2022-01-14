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

Idea:

- Divide the unsorted list into N sublists, each containing 1 element.
- Take adjacent pairs of two singleton lists and merge them to form a list of 2 elements. N will now convert into N/2 lists of size 2.
- Repeat the process till a single sorted list of obtained.

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

#### 🔮 Performance 

The list of size N is divided into a max of logN parts, and the merging of all sublists into a single list takes O(N) time, the worst case run time of this algorithm is <strong><u>O(N*logN)</u></strong>

### [5] Quick Sort


### [6] Heap Sort


	
	
### 🔗 출처	
* [Sorting Algorithms 참고 사이트 1](https://www.hackerearth.com/practice/algorithms/sorting/bubble-sort/tutorial/)
* [Sorting Algorithms 참고 사이트 2](https://ko.wikipedia.org/wiki/정렬_알고리즘)


