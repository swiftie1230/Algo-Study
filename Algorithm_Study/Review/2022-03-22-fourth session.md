# ✏️ <u>Binary Search</u> & <u>BFS</u> 

**Binary Search를 사용할 수 밖에 없는 상황! Binary Search가 많이 사용되는 상황**은 언제일까?   

일단, binary search는 **정렬되어 있는, array**에서 사용한다. 단, **반드시 모두 정렬되어 있을 필요는 없음**! **<u>부분적으로 정렬되어 있는 array</u>**가 조건이라고 생각하면 된다.          


## 📝 Binary Search

### 📌 <u>이미 모든 원소가 정렬되어 있는 Array</u>에 대해

첫 번째로 생각해야 하는 것은 바로 while loop!   

대부분의 binary search는 while loop이 들어간다.   
그럼 이를 생각하며 binary_search라는 함수를 직접 구현해보자.      

```python
def binary_search(arr, target):
	leftIdx = 0
	rightIdx = len(arr) - 1
	
	while(leftIdx <= rightIdx):
		midIdx = leftIdx + ((rightIdx - leftIdx)/2)
		
		if arr[midIdx] == target:
			returm midIdx
		else if(arr[midIdx] < target);
			leftIdx = midIdx + 1
		else:
			rightIdx = midIdx - 1
```

<div class="notice--primary" markdown="1">
🙋🏻‍♀️ <strong><u>여기서 잠깐!</u> <u>midIdx = left + ((right - left)/2)</u>로 구하는 이유는?</strong>    

보통 우리는 mid를 구할 때 (rightIdx + leftIdx) / 2로 구한다. 그런데 왜 여기서 굳이? left + ((right - left)/2) 이렇게..?    

Reason은 바로 <strong><u>Overflow 방지</u>! ✔️</strong>    

그냥 (rightIdx + leftIdx) / 2 이렇게 구해버리면, rightIdx + leftIdx를 했을 때 array 범위를 벗어날 수도 있기 때문!   
예를 들어 현재 array의 길이가 python에서 제공할 수 있는 array의 최대 길이라고 가정해보자. 이 상태에서 leftIdx가 중간 값, rightIdx가 가장 오른쪽 끝 값이라면, 둘을 더한 값은 array 범위의 값을 벗어나게 됨! 🙅🏻‍♀️          

따라서 이와 같은 <strong><u>overflow를 방지</u>하고자, left에 right의 반을 더해주는 과정, <u>left + ((right - left)/2)</u>을 거치는 것</strong>이다. 이렇게 하면 절대! 범위를 벗어나지 않겠지!    

사실 (rightIdx + leftIdx) / 2 이렇게 구해도 웬만한 대부분의 경우 문제가 되지 않는 건 사실이다. 그러나 혹시 모를 미연의 에러를 방지하기 위해! 이런 <strong><u>safe or guarded statement를 사용하는 것에 익숙해지기</u>!</strong>   

그리고 뭔가 다른, 좋은 impression을 줄 수도 있으니!(오..코딩 좀 하는데..?라는..👀)    
</div>


### 📌 <u>부분적으로 정렬된 Array</u>에 대해

위에서도 잠깐 언급한 내용이지만, **Binary Search는 무조건 모든 원소가 정렬되어 있을 때만 가능한 것이 아니다**! 고정관념을 버려야 함.    

**<u>Binary Search는 부분적으로 정렬된(Partially sorted) Array에서도 적용이 가능</u>**하다.       

예를 들어보자.  

부분적으로 정렬된 array `[5, 6, 7, 8, 9, 1, 2, 3, 4]`가 있고, 여기서 우리는 `3`이라는 수를 찾고 싶고,(즉, `3`이 `target`) 첫번째 middle 숫자는 `9`라고 가정한다.    

그러면 `9`를 기준으로 `3`이라는 숫자가 왼쪽에 있는지, 오른쪽에 있는지를 판별하기 위해서는 어떻게 하면 될까?   

찬찬히 생각해보면 그리 어렵지 않다! `middle` 숫자도 물론 중요하지만, 우리가 여기서 중요하게 보아야 할 부분은 바로 `leftIdx`와 `rightIdx`! 왜냐하면 그것이 바로 우리가 볼 마지노선이기 때문 :)     

우선, **`leftIdx`와 `middleIdx` 사이가 정렬이 되어 있는지를 체크**해야한다. 이 체크는 어떻게 할까. 바로 **`leftIdx`가 `middleIdx`보다 작은지를 체크**! **만약 `leftIdx`가 `rightIdx`보다 작다면 왼쪽 부분은 정렬이 되어 있는 것. 만약 아니라면 오른쪽 부분이 정렬되어 있는 것이겠지!**       

이제 둘 중에 어느 한 부분이 정렬되어 있는지 찾았다. 그런 다음에는? **<u>타겟이 정렬되어 있는 쪽의 범위 내에 있는지를 구분</u>**해야겠지. 만약 **정렬되어 있는 쪽의 범위 내에 있다면 우리는 그 범위로 좁히면 되는 거고, 없다면 반대쪽으로 좁히면 끝!**    

이 알고리즘을 우선 수도코드로 한 번 간단하게만 정리해보자.    

```python
if(l < m):
	# left side is sorted
	# check whether the target is in the range left
	if (target >= l && target < m):
		right = m - 1
	else:
		left = m + 1
else:
	# right side is sorted
	# check whether the target is in the range right
	if(target > m && target <= right):
		left = m + 1
	else:
		right = m - 1
```

이제 함수를 본격적으로 작성해보자! 이름하여 `tweak_binary_search()`.    

```python
def tweak_binary_search(arr, target):
	leftIdx = 0
	rightIdx = len(arr) - 1
	
	while(leftIdx <= rightIdx):
		midIdx = leftIdx + ((rightIdx - leftIdx)/2)
		
		if arr[midIdx] == target:
			returm midIdx
		
		# 확인해보는 용도
		print(arr[midIdx])
			
		if(arr[leftIdx] < arr[midIdx]):
			// left side is sorted
			if(target < arr[midIdx] && target >= arr[leftIdx]):
				rightIdx = midIdx - 1
			else:
				leftIdx = midIdx + 1
		else:
			// right side is sorted
			if(target > arr[midIdx] && target <= arr[rightIdx]):
				leftIdx = midIdx + 1
			else:
				rightIdx = midIdx - 1
	
	# while loop을 다 돌았는데도 못 찾았다면 -1 리턴
	return - 1
```

재밌다..뿌듯하고. 🌝

그럼 이 알고리즘의 Time Complexity는 어떻게 될까?    
당연히 O(logN)이겠지? 매번 탐색하는 범위가 반씩 줄게 되니까!   


### 📌 <u>값이 array에 있지 않고, 가장 가까운 값을 찾는 Algorithm</u>

- 숙제 아직 진행중..!

## 📝 BFS

DFS, BFS 주로 사용되는 경우는..항상 always 문제 풀거나 판단할 때 유용하니까 적어두기➰     

<div class="notice--primary" markdown="1">
🌟 <strong><u>Important!</u> : <u>DFS & BFS</u></strong>

- <strong><u>DFS 주로</u> 사용할 때</strong> (선택하는 reason) : <strong>visit entire graph</strong> (그래프에서 갈 수 있는 모든 노드를 가고(들러 보고) 싶을 때)     

- <strong><u>BFS 주로</u> 사용할 때</strong> (선택하는 reason) : <strong>Shortest path</strong> (특정 노드에서 다른 노드 사이의 최단거리를 찾을 때, 모든 노드들을 들를 필요 없음, 목표가 정해져 있다!)  

</div>   

너비 우선 탐색이란 루트 노드(혹은 다른 임의의 노드)에서 시작해서 인접한 노드를 먼저 탐색하는 방법이다!        

시작 정점으로부터 가까운 정점을 먼저 방문하고 멀리 떨어져 있는 정점을 나중에 방문하는 순회 방법으로, 깊게(deep) 탐색하기 전에 넓게(wide) 탐색한다.     

두 노드 사이의 최단 경로 혹은 임의의 경로를 찾고 싶을 때 이 방법을 선택한다.       

예를 들어, 지구상에 존재하는 모든 친구 관계를 그래프로 표현한 후 Ash와 Vanessa 사이에 존재하는 경로를 찾으려 할 때, 깊이 우선 탐색의 경우에는 모든 친구 관계를 다 살펴봐야 할지도 모름. But 너비 우선 탐색의 경우 Ash와 가까운 관계부터 탐색한다.       

Also 너비 우선 탐색(BFS)이 깊이 우선 탐색(DFS)보다 좀 더 복잡하다.

### 📌 <u>BFS의 특징</u>

BFS는 재귀적으로 동작하지 않는다.     

또한, 이 알고리즘을 구현할 때 가장 큰 차이점은, 그래프 탐색의 경우 어떤 노드를 방문했었는지 여부를 반드시 검사 해야 한다는 것이다. 이를 검사하지 않을 경우 무한루프에 빠질 위험이 있음!     

BFS는 방문한 노드들을 차례로 저장한 후 꺼낼 수 있는 자료 구조인 큐(Queue)를 사용한다.
즉, 선입선출(FIFO) 원칙으로 탐색하며, 일반적으로 큐를 이용해서 반복적 형태로 구현하는 것이 가장 잘 동작한다.

‘Prim’, ‘Dijkstra’ 알고리즘과 유사하다.


**BFS**는 **<u>level-by-level operation</u>**이다.    
**DFS가 위에서 아래로라면, BFS는 좌에서 우로 이동하며 탐색!**     

<img width="223" alt="Screen Shot 2022-03-11 at 6 46 58 PM" src="https://user-images.githubusercontent.com/63195670/157842991-0e56eae8-0069-45a7-88be-37a67db176ac.png">   

예를 들어 위와 같은 그래프에서는 `3 → 5 → 1 → 6 → 2 → 0 → 8 → 7 → 4` 순서로 진행하는 것!
	
### 📌 <u>BFS 구현</u>

물론 BFS는 최단 거리, 경로에 많이 사용하긴 하지만, 이번 세션에는 시간이 부족했던 터라 target 값을 찾는, 간단한 BFS를 구현해 보았다.    

```python

def BFS(root, target):
	if not root:
		return root
	
	queue = [root]
	
	while (queue.length):
		current = queue.dequeue()
		
		if current.val == target:
			return true
		
		if current.left:
			queue.enqueue(curren.left)
		if current.right:
			queue.enqueue(current.right)
			
	return false
```

### 📌 <u>BFS의 시간 복잡도</u> 🌟

- 인접 리스트로 표현된 그래프: O(N+E)

- 인접 행렬로 표현된 그래프: O(N^2)

- 깊이 우선 탐색(DFS)과 마찬가지로 그래프 내에 적은 숫자의 간선만을 가지는 희소 그래프(Sparse Graph) 의 경우 인접 행렬보다 인접 리스트를 사용하는 것이 유리하다!
      


<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>다시 보며 헷갈렸거나 새로웠던 내용</u></strong>        

1. BS 다양한 응용들까지!       
2. BFS
3. Queue : Dequeue, Enqueue

</div>


## 🔗 참고 사이트  

- [BFS](https://gmlwjd9405.github.io/2018/08/15/algorithm-bfs.html)     
