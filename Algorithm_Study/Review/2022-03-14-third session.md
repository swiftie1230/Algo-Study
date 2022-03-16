# ✏️ <u>Top-Down / Bottom Up Approach</u>

3주차에는 Top-Down / Bottom-Up Approach에 대해 공부하는 시간을 가졌다.     
더 자세하게 in-order, pre-order, post-order, level-order 그리고 depth & height of the tree 등의 내용도 알게 되었고, 이에 대해 한 번 리마인드용 정리를 해 보려 한다.     

사실 이번 주차는 이 외에도 BFS까지가 목표였지만, 포니콘&유니콘 멘토링 세션으로 일단 여기까지!    
나머지는 주중 하루에 또 세션을 가진다 하셨는데..아직 어떻게 될지는 모르겠음 🌝   

DFS, BFS 주로 사용되는 경우는..항상 always 문제 풀거나 판단할 때 유용하니까 적어두기➰     

<div class="notice--primary" markdown="1">
🌟 <strong><u>Important!</u> : <u>DFS & BFS</u></strong>

- <strong><u>DFS 주로</u> 사용할 때</strong> (선택하는 reason) : <strong>visit entire graph</strong> (그래프에서 갈 수 있는 모든 노드를 가고(들러 보고) 싶을 때)     

- <strong><u>BFS 주로</u> 사용할 때</strong> (선택하는 reason) : <strong>Shortest path</strong> (특정 노드에서 다른 노드 사이의 최단거리를 찾을 때, 모든 노드들을 들를 필요 없음, 목표가 정해져 있다!)  

</div> 

## 📝 트리 순회 (Tree-Traversing)

### 📌 <u>중위 순회</u> (<u>in - order traversing</u>)   

코테에서 나오는 대부분의 traversing 방법. **<u>Most-common</u>**하다.    

**<u>`left` 자식 노드</u>, <u>부모 노드</u>, <u>`right` 노드</u>** 순으로 traverse하는 방식이다 (`left`, `parent`, `right`).     

<img width="223" alt="Screen Shot 2022-03-11 at 6 46 58 PM" src="https://user-images.githubusercontent.com/63195670/157842991-0e56eae8-0069-45a7-88be-37a67db176ac.png">     

예를 들어 위 그림과 같은 그래프를 `in-order` 방식으로 traversing 했을 경우, `6 → 5 → 7 → 2 → 4 → 3 → 0 → 1 → 8` 순인 것이다.  

그럼 이 트리(그래프)를 일단 한 번 생성해 보자.

```python
class Node: 
	def__init__(self, item):
		self.item = item
		self.left = None
		self.right = None
class BinaryTree():
	def__init__(self):
		self.root = None
```
본격적으로 위 노드 값들을 해당 트리에 맞게 정렬해 보자.     

```python
# 각 노드 생성
n1 = Node(3)
n2 = Node(5)
n3 = Node(1)
n4 = Node(6)
n5 = Node(2)
n6 = Node(7)
n7 = Node(4)
n8 = Node(0)
n9 = Node(8)

# 순서에 맞게 노드를 엮어보자.
tree = BinaryTree()
tree.root = n1
n1.left = n2
n1.right = n3
n2.left = n4
n2.right = n5
n5.left = n6
n5.right = n7
n3.left = n8
n3.right = n9
```


이 `in-order` traversing 방법을 사용하여 DFS를 실행하는 함수를 만들어 보면 다음과 같다.      

```python
arr = []

def dfs(currentNode):
	if !currentNode:
		return
	
	#left
	dfs(currentNode.left)
	#parent
	arr.append(currentNode)
	#right
	dfs(currentNode.right)
	return
```

이제 이 트리가 dfs 함수를 거칠 때의 stack의 상태를 한 번 생각해 보면 다음과 같다.     
매우 어지러워 보이지만, 차근차근 생각하며 따라가다 보면 쉽고 명확하게 이해할 수 있을 것! 🥰              

`node 3 , node 5, node 6, null(node 6의 left)` → `return` + `array`에 `node 6` append →` node 3 , node 5, node 6, null(node 6의 right)` → `return`+ `array`에 `node 5` append → `node 3 , node 5, node 2, node 7, null(node 7의 left)`→ `return` + `array`에 `node 7` append → `node 3 , node 5, node 2, node 7, null(node 7의 right)` → `return`+ `array`에 `node 2` append → `node 3 , node 5, node 2, node 4, null(node 4의 left)` → `return`+ `array`에 `node 4` append → `node 3, node 5, node 2, node 4, null(node 4의 right)`→ `return`→ `return` → `return` → `array`에 `node 3` append → `node 3 , node 1, node 0, null(node 0의 left)`→ `return` + `array`에 `node 0` append →` node 3 , node 1, node 0, null(node 0의 right)` → `return`+ `array`에 `node 1` append → `node 3 , node 1, node 8, null(node 8의 left)`→ `return` + `array`에 `node 8` append →` node 3 , node 1, node 8, null(node 8의 right)` → `return`  → `return` → `return`    


### 📌 <u>전위 순회</u> (<u>pre - order traversing</u>)

**<u>자기 자신을 먼저 출력</u>하고 <u>자식 노드를 호출</u>한다.**

- 자기 자신 출력

- 왼쪽 서브 트리 호출

- 오른쪽 서브 트리 호출   

```python
arr = []

def dfs(currentNode):
	if !currentNode:
		return
	
	#parent
	arr.append(currentNode)
	#left
	dfs(currentNode.left)
	#right
	dfs(currentNode.right)
	return
```



### 📌 <u>후위 순회</u> (<u>post - order traversing</u>)

**<u>자기 자신 출력</u>을 <u>가장 나중에</u> 한다.**

- 왼쪽 서브 트리 호출

- 오른쪽 서브 트리 호출

- 자기 자신 출력 


```python
arr = []

def dfs(currentNode):
	if !currentNode:
		return
	
	#left
	dfs(currentNode.left)
	#right
	dfs(currentNode.right)
	return
	#parent
	arr.append(currentNode)
```

### 📌 <u>레벨 순회</u> (<u>Level - order</u>)

**<u>깊이(레벨) 단위로 출력</u>하는 것으로, 그 순서는 깊이가 낮은 순서이다.**

호출될 때마다 자식 노드를 선입선출 구조인 큐로 구현하여 따로 저장한다. 

```python
arr = []

def levelOrder(currentNode):
	q = []
	q.append(currentNode)
	while q:
		t = q.pop()
		print(t.item,'',end='')
		if t.left != None:
			q.append(t.left)
		if t.right != None:
			q.append(t.right)
```



## 📝 트리에서의 깊이와 높이 (Depth & height)
	
### 📌 <u>노드의 깊이 (Depth)</u>

트리에서의 노드의 깊이는 간단하다. **위에서부터 몇 층(?)에 있는지**를 의미!     

<img width="223" alt="Screen Shot 2022-03-11 at 6 46 58 PM" src="https://user-images.githubusercontent.com/63195670/157842991-0e56eae8-0069-45a7-88be-37a67db176ac.png">     

예를 들어 위 트리에서 노드 3의 깊이는 0, 노드 5의 깊이는 1, 노드 6의 깊이는 2인 것이다.     

### 📌 <u>노드의 높이 (Height)</u>: <u>똑바로 알고 가기</u> 🌟

노드의 깊이와 다르게, **<u>leaf node에서부터</u> 세는 것**이 바로 **<u>노드의 높이</u>, <u>height</u>** 이다.    
이 때 **만약 <u>두 자식 노드의 height이 서로 다르다</u>면 어떻게 세야 할까?** 예를 들어,     

<img width="223" alt="Screen Shot 2022-03-11 at 6 46 58 PM" src="https://user-images.githubusercontent.com/63195670/157842991-0e56eae8-0069-45a7-88be-37a67db176ac.png">       

이 트리에서 자식 노드 6에서 보면 1, 자식 노드 2에서 보면 2인 **노드 5의 height**은 어떻게 계산하냐 이말이다!      
간단하다. 생각하는 바로 그대로. **<u>"두 자식 노드들의 height 중 큰 숫자를 take해서 +1"</u>**하면 끝! 👀       
그래서 노드 5의 height는 2이다.    


<div class="notice--primary" markdown="1">
🌟 <strong><u>Important!</u> : <u>Approach와 이들의 관계</u></strong>

여기서 <strong><u>노드의 깊이(depth)</u>는 <u><code>top-down approach</code></u></strong>와, <strong><u>노드의 높이(height)</u>는 <u><code>bottom-up approach</code></u></strong>와 비슷하다고 생각하면 된다.  

</div> 


## 📝 Top-Down & Bottom Up Approach

### 📌 <u>Getting Depth with Top-Down Approach</u> 

```python

def topDownDepth(root):
	longestDepth = []
	dfs(root, longestDepth, 0)
	return longestDepth[0]
	
def dfs(currentNode, depth, currentDepth):
	if !currentNode.left and !currentNode.right:
		depth[0] = max(depth[0], currentDepth)
	
	dfs(currentNode.left, currentDepth+1)
	dfs(currentNode.right, currentDepth+1)
	return

``` 

<div class="notice--primary" markdown="1">
🌟 <strong><u>Important!</u> : <u>여기서 longestDepth array를 사용한 이유?</u></strong>

여기서 <code>longestDepth</code>라는 숫자 (현재까지 가장 깊은 깊이)를 저장할 것이기 때문에 <code>array</code>를 사용하는 대신 그냥 <code>int</code> 자료형을 사용하면 되지 않나? 라고 생각할 수 있다.     

결론은 안된다.   
자, 찬찬히 생각해보면 만약 그냥 value를 넣어준다면 설령 이 value를 업데이트해야 하는 상황, 즉, 더 깊은 깊이를 찾은 상황에서도 dfs stack에서 나가버리는 순간 이 value를 기억하고 이를 업데이트 해줄 수가 없다. 물론 하나하나 반환하고 이를 저장할 수는 있겠지만..매우 복잡해질 수 밖에 없다. 🤦🏻‍♀️      

그러나 array를 선언하여 이 memory address를 참조하는 형식으로 가면, 이 주소는 어디에서나 접근가능하고, 그 값도 어디에서나 변경할 수 있는 것!      

따라서 <strong><u>top-down</u>을 사용할 시, 직접적인 value 대신 <u>레퍼런스</u>를 사용하자!</strong>

</div> 

### 📌 <u>Getting Height with Bottom-Up Approach</u>

```python

def bottomUpHeight(root):
	if !root:
		return 0
		
	return dfsBottomUp(currentNode)
		
	
def dfsBottomUp(currentNode):
	if !currentNode:
		return 0
	
	# 자식 노드들의 Height를 가져와 각각 left, right에 넣어준다.
	left = dfsBottomUp(currentNode.left)
	right = dfsBottomUp(currentNode.right)
	
	# 비교하여 더 큰 값 + 1 리턴
	return max(left, right) + 1

```    

<div class="notice--primary" markdown="1">
🌟 <strong><u>Important!</u> : <u>어떤 걸 사용하는 게 좋을까?</u></strong>

좋다는 말이 어울릴지는 모르겠다.    
사실 Top-Down Approach를 사용하는 경우가 많고, 나 또한 이렇게 많이 문제를 접근했다.  
But 될 수 있다면 Bottom-Up Approach로 풀어라!! 🤫   
문제가 어려워지면 어려워질수록 Bottom-up Approach로 쉽게 접근, 풀 수 있다!    

</div> 



<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>다시 보며 헷갈렸거나 새로웠던 내용</u></strong>        

1. Top-Down & Bottom-up          
2. 트리순회
3.  깊이와 높이

</div>
