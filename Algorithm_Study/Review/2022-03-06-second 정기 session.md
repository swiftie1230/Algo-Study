# 📝 DFS

2주차에는 DFS에 대해 배웠는데, 직접 대표적인 문제 하나를 풀어주시며 설명해주셨다!    

우선 주로 사용되는 경우를 나누어 말씀해 주셨는데..문제 풀거나 판단할 때 유용할 것 같아 여기에 적어두기➰     

<div class="notice--primary" markdown="1">
🌟 <strong><u>Important!</u> : <u>DFS & BFS</u></strong>

- <strong><u>DFS 주로</u> 사용할 때</strong> (선택하는 reason) : <strong>visit entire graph</strong> (그래프에서 갈 수 있는 모든 노드를 가고(들러 보고) 싶을 때)     

- <strong><u>BFS 주로</u> 사용할 때</strong> (선택하는 reason) : <strong>Shortest path</strong> (특정 노드에서 다른 노드 사이의 최단거리를 찾을 때, 모든 노드들을 들를 필요 없음, 목표가 정해져 있다!)  

</div> 

## 그래프 탐색이란 ?

- 하나의 정점으로부터 시작하여 차례대로 모든 정점들을 한 번씩 방문하는 것

	- Ex) 특정 도시에서 다른 도시로 갈 수 있는지 없는지, 전자 회로에서 특정 단자와 단자가 서로 연결되어 있는지

## 깊이 우선 탐색(DFS, Depth-First Search)

### 깊이 우선 탐색이란 ?

**루트 노드(혹은 다른 임의의 노드)에서 시작해서 다음 분기(branch)로 넘어가기 전에 <u>해당 분기를 완벽하게 탐색</u>하는 방법**

- 미로를 탐색할 때 한 방향으로 갈 수 있을 때까지 계속 가다가 더 이상 갈 수 없게 되면 다시 가장 가까운 갈림길로 돌아와서 이곳으로부터 다른 방향으로 다시 탐색을 진행하는 방법과 유사하다.

- 즉, **넓게(wide) 탐색하기 전에 <u>깊게(deep) 탐색</u>하는 것**이다.

- 사용하는 경우: **<u>모든 노드를 방문(visit entire graph)</u>**하고자 하는 경우에 이 방법을 선택한다.

- 깊이 우선 탐색(DFS)이 너비 우선 탐색(BFS)보다 좀 더 간단하다.

- **단순 검색 속도 자체는 너비 우선 탐색(BFS)에 비해서 느리다**.    


### 깊이 우선 탐색(DFS)의 특징

- 자기 자신을 호출하는 **순환 알고리즘의 형태**를 가지고 있다.

- 전위 순회(Pre-Order Traversals)를 포함한 다른 형태의 트리 순회는 모두 DFS의 한 종류이다.

- 이 알고리즘을 구현할 때 가장 큰 차이점은, 그래프 탐색의 경우 **<u>어떤 노드를 방문했었는지 여부</u>를 반드시 검사 해야 한다는 것**이다.
	- 이를 검사하지 않을 경우 무한루프에 빠질 위험이 있다.

<div class="notice--primary" markdown="1">
🙋🏻‍♀️ <strong><u>여기서 잠깐!</u> : <u>그래프 깊이(Depth)</u></strong>

만약, 구현하려고 하는 알고리즘이 트리가 아닌 그래프를 탐색하게 된다면 약간의 변화가 필요하다. 우선적으로는 그래프의 깊이(depth)를 결정할 필요가 있다.      
루트 노드(가상 최상위에 위치한 노드)의 깊이는 0으로 하며, 임의의 노드의 깊이는 이의 '부모 중 가장 깊이가 작은 것'의 깊이에 '1'을 더한 값으로 정의한다.        

</div> 


### 깊이 우선 탐색(DFS)에서의 깊이 제한과 백트래킹

**탐색 과정이 시작 노드에서 한없이 깊이 진행되는 것을 막기 위해 깊이 제한(depth bound)를 사용한다.**      

깊이 제한에 도달할 때까지 목표노드가 발견되지 않으면 최근에 첨가된 노드의 부모노드로 돌아와서, 부모노드에서 이전과는 다른 동작자를 적용하여 새로운 자식노드를 생성한다. 여기서 **부모노드로 되돌아 오는 과정**을 **<u>백트래킹(backtracking)</u>**이라고 한다.
	
### 깊이 우선 탐색(DFS)의 과정

![](https://media.vlpt.us/images/sohi_5/post/221b5009-1002-468c-a68a-415ef78c3cdf/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%206.37.06.png)     

위 사진은 노드 1을 시작으로 차례대로 노드 9까지 순회한다. 진행되는 방향을 보면 한 가지의 끝까지 탐색하고, 그 다음 가지를 순차적으로 탐색한다. 전체적 위에서 아래로 깊게 탐색이 진행되는 것을 볼 수 있다.      

조금 더 해당 트리형태의 그래프의 과정을 자세히 설명해보겠다!    

![](https://media.vlpt.us/images/sohi_5/post/fcbdab2d-9cc6-4bb9-8ec7-7bb28be3bf1c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.05.28.png)      

트리의 루트 노드인 노드 1을 기준으로 탐색을 시작한다. 스택 노드 1을 넣은 후, 노드 1과 연결된 노드 중 방문하지 않은 노드가 있는지 확인한다. 어? 2가 있다.        

![](https://media.vlpt.us/images/sohi_5/post/19026fa3-779d-43db-95e6-2438c48496fd/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.09.37.png)        

노드 2를 스택에 넣어 준 후, 동일하게 노드 2와 연결된 노드 중 방문하지 않은 노드가 있는지 확인한다. 역시 노드 3을 발견할 수 있음.          

![](https://media.vlpt.us/images/sohi_5/post/ecaacfa5-eb94-4177-9f40-70f0f810c22c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.13.17.png)     

이제 노드 3을 스택에 넣어주고, 연결된 노드 중 방문하지 않은 노드가 있는지 확인!    

![](https://media.vlpt.us/images/sohi_5/post/06c1ccf6-383f-4dda-a3ba-b1bd4d4c05af/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.15.53.png)      

But  노드 3과 연결된 노드는 노드 2뿐이며, 이미 방문했으므로 이번 분기의 탐색이 완료된 것이기 때문에 노드 3을 스택에서 빼낸다.         
다음, 스택의 가장 위에 위치한 노드 2와 연결된 아직 방문하지 않은 노드가 있는지 확인한다. 그러나 존재하지 않기 때문에 역시 노드 2도 스택에서 빼냄.      

![](https://media.vlpt.us/images/sohi_5/post/c53e8fd8-0c9a-4e2e-89c3-3b9cc7771b46/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.19.03.png)     

![](https://media.vlpt.us/images/sohi_5/post/209c03f6-77bd-4a35-ac8b-63d35ad7467f/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.23.03.png)    

앞의 과정을 계속 반복하자. 노드 1과 연결된 노드 중 방문하지 않은 노드 4를 스택에 추가하고, 노드 4와 연결된 노드 5 , 노드 5와 연결된 노드 6 역시 다시 스택에 추가한다.     

노드 6와 연결된 노드를 확인한다. 방문하지 않은 노드가 없으므로 스택에서 제거한다. 노드 5도 마찬가지로 스택에서 제거한다.   

이제 노드 4와 연결된 또다른 노드를 확인하자. 7이 있군.      

![](https://media.vlpt.us/images/sohi_5/post/2d80c51f-03a6-46c1-ac88-8431e9ea00b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.25.14.png)         

노드 7을 스택에 추가한다. But 연결된 노드 중 방문하지 않은 것이 없으므로 다시 스택에서 제거하고, 노드 4 역시 동일한 이유로 스택에서 제거!       

![](https://media.vlpt.us/images/sohi_5/post/2d31b1d2-f0d0-4455-968c-53767b6f78d7/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.26.57.png)     

노드 1과 연결된 마지막 노드 8을 스택에 추가하고, 다음 노드를 탐색한다. 9.     

![](https://media.vlpt.us/images/sohi_5/post/5226b43e-219f-4f29-a4fe-a30cb8f43d26/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.29.24.png)        

노드 9를 스택에 추가한다. 방문할 노드가 없으며, 노드 8 또한 마찬가지이므로 스택에서 제거한다.       

![](https://media.vlpt.us/images/sohi_5/post/00d332f2-dc0d-4666-9c35-06d7364c03cd/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-04-21%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%207.30.47.png)       

이제 방문하지 않은 노드가 더 이상 존재하지 않지? 그럼 노드 1을 스택에서 제거해 탐색을 마치면 된다.      

### 깊이 우선 탐색(DFS)의 구현

- 구현 방법  : 순환 호출과 명시적인 스택 이용     
	
	- 의사코드 (pseduocode)

		```python
		def dfs(Node root):
			# 루트 노드 방문
			if not root:
				return
			root.visited = True; # 방문한 노드를 표시
			# 루트 노드와 인접한 정점을 모두 방문
			for Node n in root.adjacent: 
				if n.visited == False: # 방문하지 않은 정점을 찾는다.
					dfs(n) # 루트 노드와 인접한 정점을 시작으로 DFS 시작
		```




### 깊이 우선 탐색(DFS)의 시간 복잡도

- DFS는 그래프(정점의 수 : N, 간선의 수 : E)의 모든 간선을 조회한다.

	- 인접 리스트로 표현된 그래프 : O(N+E)

	- 인접 행렬로 표현된 그래프 : O(N^2)

- 즉, **그래프 내에 적은 숫자의 간선만을 가지는 <u>희소 그래프(Sparse Graph)</u>**의 경우 **인접 행렬보다 <u>인접 리스트</u>를 사용하는 것이 유리**하다.     
	
<div class="notice--primary" markdown="1">
🌟 <strong><u>여기서 잠깐!</u> : <u>인접 리스트와 인접 행렬로 표현된 그래프가 뭐가 달라요?</u></strong>    

사실 정말 별로 어렵지 않은 개념이다! 아래 링크 (예전에 정리해 둔게 있더라고..👀) 참고! 😘     

<strong><a href = "https://swiftie1230.github.io/algorithm_study/알고리즘활용-BFS&DFS-정리/">알고리즘활용-BFS&DFS-정리</a></strong>

</div> 

### 깊이 우선 탐색(DFS)의 장점과 단점

1. 장점

	- 단지 현 경로상의 노드들만을 기억하면 되므로 **저장공간의 수요가 비교적 적다**.
	- 목표노드가 깊은 단계에 있을 경우 해를 빨리 구할 수 있다.

2.  단점

	- **해가 없는 경로에 깊이 빠질 가능성**이 있다. 따라서 깊이제한을 통하여 목표노드를 발견하지 못하면 다음의 경로를 따라 탐색하는 방법이 유용할 수 있다.
	- **얻어진 해가 최단 경로가 된다는 보장이 없다**. 이는 목표에 이르는 경로가 다수인 문제에 대해 깊이우선 탐색은 해에 다다르면 탐색을 끝내버리므로, 이 때 얻어진 해는 최적의 해가 아닐 수 있다는 의미이다.

DFS 정리는 여기서 끝!    

이제 본격적으로 정기세션에서 풀었던 문제를 한 번 보자!    

## 📝 Problem

### 💬 [Leetcode - Number of Islands](https://leetcode.com/problems/number-of-islands/) 

#### 📄 문제 설명  

Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return *the number of islands*.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

#### ⛔️ 제한사항
- `m == grid.length`
- `n == grid[i].length`
- `1 <= m, n <= 300`
- `grid[i][j] is '0'` or `'1'`.

#### 💭 입출력 예

<div class="notice--primary" markdown="1">
🌝 <u>입출력 예 #1</u>     

[입력]   

   ```python
grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
   ```             
      
    
[출력]    

   ```python    
1     
   ```
</div>   


<div class="notice--primary" markdown="1">
🌝 <u>입출력 예 #2</u>     

[입력]   

   ```python
grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
   ```             
      
    
[출력]    

   ```python    
3 
   ```
   
</div>    

### ✏️ Final Code With Explaination

자세한 설명은 주석을 참고하자.

```python  
class Solution(object):
    def numIslands(self, grid):
        # 반환할 값
        result = 0
        
        # 모든 matrix를 돌면서 새로운 island 여부 확인 
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                # 해당 값이 1로, 새로운 island 가능하다면 dfs_recursion 시작
                if grid[i][j] == "1":
                    self.dfs_recursion(grid, i, j)
                    # 모든 recursion 종료되면 하나의 island 찾은 것이므로 result에 1 추가해 준다.
                    result += 1
        
        return result
                                    
    # dfs recursion 진행할 추가 함수    
    def dfs_recursion(self, matrix, current_i, current_j):
        # edge case : recursion을 return할 구실이 되는 조건들
        # matrix 범위 밖이거나, 해당 값이 0일 때
        if (current_i < 0 or current_i >= len(matrix) or current_j < 0 or current_j >= len(matrix[0]) or matrix[current_i][current_j] == "0"):
            return
        
        # mark하기 위해 해당 값은 0으로 교체
        matrix[current_i][current_j] = "0"
        
        direction = [[-1, 0], [0, 1], [1, 0], [0, -1]]
        
        # 있는 곳 기준으로 위아래, 오른쪽, 왼쪽 모두 recursion 진행
        for i in range(len(direction)):
            self.dfs_recursion(matrix, current_i - direction[i][0], current_j - direction[i][1])
```          


<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>다시 보며 헷갈렸거나 새로웠던 내용</u></strong>        

 1. 인접 행렬과 인접 리스트를 사용하는 방법          
 2. Of course, DFS  

</div>
