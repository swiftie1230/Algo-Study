# Non-Linear Data Structure ✍🏻

<div class="notice--primary" markdown="1">
Nonlinear data structures are those data structures in which <strong><u>data items are not arranged in a sequence</u></strong>.
</div>



## 📌 Characteristics

Unlike Linear Data Structure, which every item is related to its previous and next time, **in Non-Linear Data Structure, <u>every item is attached with many other items</u>.**    

Also, **data is <u>not arranged in sequence</u>, and <u>cannot be traversed in a single run</u>.**    

**<u>Implementation is difficult</u> but <u>memory utilization is effective</u>** compared with Linear Data Structure.    

## 📌 List of data structure in a non-linear type of data structure

### [1] Graph

- 단순히 노드(N, node)와 그 노도를 연결하는 간선(E, edge)을 하나로 모아 놓은 자료 구조

- 그래프는 여러 개의 고립된 부분 그래프 (Isolated Subgraphs)로 구성될 수 있다.

<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>오일러 경로(Eulerian tour)</u></strong>   

<strong>그래프에 존재하는 <u>모든 간선(edge)을 한 번만 통과</u>하면서 <u>처음 정점(vertex)으로 되돌아오는 경로</u></strong>를 말한다.    
<strong>그래프의 모든 정점에 연결된 <u>간선의 개수가 짝수일 때</u>만 오일러 경로가 존재</strong>한다.

</div>

#### ✏️ <u>그래프와 관련된 용어</u>

> **정점(vertex)** : 위치라는 개념. (node 라고도 부름)   
> 
> **간선(edge)** : 위치 간의 관계. 즉, 노드를 연결하는 선 (link, branch 라고도 부름)   
> 
> **인접 정점(adjacent vertex)** : 간선에 의해 직접 연결된 정점   
> 
> **<u>정점의 차수(degree)</u>** : <u>무방향 그래프</u>에서 하나의 정점에 인접한 정점의 수   
> 	- 무방향 그래프에 존재하는 정점의 모든 차수의 합 = 그래프의 간선 수의 2배     
> 
> **<u>진입 차수(in-degree)</u>** : <u>방향 그래프</u>에서 <u>외부에서 오는 간선</u>의 수 (내차수 라고도 부름)   
> 
> **<u>진출 차수(out-degree)</u>** : <u>방향 그래프</u>에서 <u>외부로 향하는 간선</u>의 수 (외차수 라고도 부름)   
> 	- 방향 그래프에 있는 정점의 진입 차수 또는 진출 차수의 합 = 방향 그래프의 간선의 수(내차수 + 외차수)    
> 
> **<u>경로 길이(path length)</u>** : 경로를 구성하는 데 사용된 간선의 수   
> 
> **<u>단순 경로(simple path)</u>** : 경로 중에서 <u>반복되는 정점이 없는 경우</u>   
> 
> **<u>사이클(cycle)</u>** : 단순 경로의 시작 정점과 종료 정점이 동일한 경우   


#### ✏️ <u>그래프의 기본적인 성질 & 특징</u>

- 그래프는 네트워크 모델 이다.

- 2개 이상의 경로가 가능하다.
	- 즉, 노드들 사이에 무방향/방향에서 <u>양방향 경로</u>를 가질 수 있다.

- self-loop 뿐 아니라 loop/circuit 모두 가능하다.

- **<u>루트 노드라는 개념이 없다</u>.**

- **<u>부모-자식 관계라는 개념이 없다</u>.**

- **순회는 <u>DFS</u>나 <u>BFS</u>로 이루어진다.**

- **그래프는 <u>순환(Cyclic)</u> 혹은 <u>비순환(Acyclic)</u>이다.**

- **그래프는 크게 <u>방향 그래프</u>와 <u>무방향 그래프</u>가 있다.**

- 간선의 유무는 그래프에 따라 다르다.


#### ✏️ <u>그래프의 종류</u>

##### 🔮 <u>무방향 그래프 & 방향 그래프</u>

- **무방향 그래프 (Undirected Graph)**
	- 무방향 그래프의 간선은 간선을 통해서 양 방향으로 갈 수 있다.
	- 정점 A와 정점 B를 연결하는 간선은 (A, B)와 같이 정점의 쌍으로 표현한다.
		- (A, B)는 (B, A) 동일
	- Ex) 양방향 통행 도로

- **방향 그래프 (Directed Graph)**
	- 간선에 방향성이 존재하는 그래프
	- A → B로만 갈 수 있는 간선은 `<A, B>`로 표시한다.
		- `<A, B>`는 `<B, A>`는 다름

	- Ex) 일방 통행

	
##### 🔮 <u>가중치 그래프</u>

- **간선에 <u>비용이나 가중치가 할당</u>된 그래프**
- ‘네트워크(Network)’ 라고도 한다.
	- Ex) 도시-도시의 연결, 도로의 길이, 회로 소자의 용량, 통신망의 사용료 등


##### 🔮 <u>연결 그래프 & 비연결 그래프</u>

- **연결 그래프 (Connected Graph)**
	- **무방향 그래프에 있는 모든 정점쌍에 대해서 항상 경로가 존재하는 경우**
	- Ex) 트리(Tree): 사이클을 가지지 않는 연결 그래프

- **비연결 그래프 (Disconnected Graph)**
	- **무방향 그래프에서 <u>특정 정점쌍 사이에 경로가 존재하지 않는 경우</u>**


##### 🔮 <u>사이클 & 비순환 그래프</u>

- **사이클 (Cycle)**
	- 단순 경로의 시작 정점과 종료 정점이 동일한 경우
		- 단순 경로 (Simple Path) : 경로 중에서 반복되는 정점이 없는 경우

- **비순환 그래프 (Acyclic Graph)**
	- 사이클이 없는 그래프

##### 🔮 <u>완전 그래프</u>

- 그래프에 속해 있는 모든 정점이 서로 연결되어 있는 그래프
- 무방향 완전 그래프
	- 정점 수: n이면 간선의 수: n * (n-1) / 2


#### ✏️ <u>그래프의 구현 및 탐색</u> : <u>아래 링크 참고!</u>

[그래프의 구현 및 탐색 관련 my 정리 링크](https://swiftie1230.github.io/algorithm_study/알고리즘활용-BFS&DFS-정리/)

[그래프의 구현 및 탐색 관련 외부 정리 링크](https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html)



### [2] 트리(Tree)

- 노드로 이루어진 자료 구조로, 노드(node)들과 노드들을 연결하는 링크(간선)[link(edge)]들로 구성됨.

- 비선형 자료구조로 계층적 관계를 표현한다. Ex) 디렉터리 구조, 조직도

- 그래프의 한 종류
	- 사이클(cycle)이 없는 하나의 연결 그래프(Connected Graph)
	- 또는 DAG(Directed Acyclic Graph, 방향성이 있는 비순환 그래프)의 한 종류

#### ✏️ <u>트리와 관련된 용어</u>

<img width="746" alt="Screen Shot 2022-01-11 at 4 48 56 PM" src="https://user-images.githubusercontent.com/63195670/148904402-5eb3058f-996a-468d-9a97-94c5cad59610.png">

> **루트 노드(root node)** : 부모가 없는 노드, 트리는 하나의 루트 노드만을 가진다.   
> 
> **단말 노드(leaf node)** : 자식이 없는 노드, ‘말단 노드’ 또는 ‘잎 노드’라고도 부른다.  
>  
> **내부(internal) 노드** : 단말 노드가 아닌 노드    
> 
> **간선(edge)** : 노드를 연결하는 선 (link, branch 라고도 부름)   
> 
> **형제(sibling)** : 같은 부모를 가지는 노드   
> 
> **<u>노드의 크기(size)</u>** : 자신을 포함한 (자신 아래) 모든 자손 노드의 개수   
> 
> **<u>노드의 깊이(depth)</u>** : <u>루트에서 어떤 노드에 도달하기 위해 거쳐야 하는 간선의 수</u>   
> 
> **<u>노드의 레벨(level)</u>** : 트리의 특정 깊이를 가지는 노드의 집합   
> 
> **<u>노드의 차수(degree)</u>** : 하위 트리 개수 / 간선 수 (degree) = <u>각 노드가 지닌 가지의 수</u>   
> 
> **<u>트리의 차수(degree of tree)</u>** : 트리의 최대 차수   
> 
> **<u>트리의 높이(height)</u>** : 루트 노드에서 가장 깊숙히 있는 노드의 깊이   


#### ✏️ <u>트리의 기본적인 성질 & 특징</u>

- 트리는 하나의 루트 노드를 갖는다. 

- 루트 노드는 0개 이상의 자식 노드를 갖고 있다. 

- 그 자식 노드 또한 0개 이상의 자식 노드를 갖고 있고, 이는 반복적으로 정의된다.

- **<u>트리에는 사이클(cycle)이 존재할 수 없다</u>.**

- 노드들은 특정 순서로 나열될 수도 있고 그럴 수 없을 수도 있다.

- 각 노드는 부모 노드로의 연결이 있을 수도 있고 없을 수도 있다.

- **<u>각 노드는 어떤 자료형으로도 표현 가능하다</u>.**

- 그래프의 한 종류이다. ‘최소 연결 트리’ 라고도 불린다.

- 트리는 계층 모델 이다.

- **트리는 <u>DAG(Directed Acyclic Graphs, 방향성이 있는 비순환 그래프)</u>의 한 종류**이다.
	- loop나 circuit이 없다. 당연히 self-loop도 없다.
	- **즉, <u>사이클이 없다</u>.**

- **노드가 N개인 트리는 항상 N-1개의 간선(edge)을 가진다.**
	- 즉, **<u>간선</u>은 항상 <u>(정점의 개수 - 1)</u>만큼을 가진다**.

- **루트에서 어떤 노드로 가는 경로는 유일하다.**
	- 임의의 두 노드 간의 경로도 유일하다. 즉, **<u>두 개의 정점 사이에 반드시 1개의 경로만을 가진다</u>.**

- **<u>한 개의 루트 노드만이 존재</u>하며 <u>모든 자식 노드는 한 개의 부모 노드만을 가진다</u>.**
	- 부모-자식 관계이므로 흐름은 top-bottom 아니면 bottom-top으로 이루어진다.

- **<u>순회</u>는 <u>Pre-order</u>, <u>In-order</u> 아니면 <u>Post-order</u>로 이루어진다.** 이 3가지 모두 DFS/BFS 안에 있다.

- 트리는 **이진 트리, 이진 탐색 트리, 균형 트리(AVL 트리, red-black 트리), 이진 힙(최대힙, 최소힙) 등이 있다**.



#### ✏️ <u>트리의 종류</u>

##### 🔮 <u>이진트리</u> (Binary Tree)

- **각 노드가 <u>최대 두 개의 자식</u>**을 갖는 트리
- 모든 트리가 이진 트리는 아니다.
- 이진 트리 순회 
	- 중위 순회(in-order traversal) 
	<img width="243" alt="Screen Shot 2022-01-11 at 7 02 43 PM" src="https://user-images.githubusercontent.com/63195670/148922063-934b0fa7-0af9-40a1-a0c3-db3275e41dad.png">

		```
		void inOrderTraversal(TreeNode node) {
	  		if(node != null) {
	   			inOrderTraversal(node.left);	// 왼쪽
	   			visit(node);	// 중앙
	   			inOrderTraversal(node.right);	// 오른쪽
	  		}
		}
		```		


	- 전위 순회(pre-order traversal)
	<img width="245" alt="Screen Shot 2022-01-11 at 6 54 43 PM" src="https://user-images.githubusercontent.com/63195670/148920817-1eb14c14-d318-4169-9209-04bf5e698a9b.png">
		
		```
		void preOrderTraversal(TreeNode node) {
  			if(node != null) {
   				visit(node);	// 중앙
   				preOrderTraversal(node.left);	// 왼쪽
   				preOrderTraversal(node.right);	// 오른쪽
 			}
		}
		```
			
	- 후위 순회(post-order traversal)
	<img width="285" alt="Screen Shot 2022-01-11 at 7 19 10 PM" src="https://user-images.githubusercontent.com/63195670/148924624-b5402cdd-2721-4bcd-9b38-fe44d63cf639.png">
		
		```
		void postOrderTraversal(TreeNode node) {
	  		if(node != null) {
	   			postOrderTraversal(node.left);	// 왼쪽
	   			postOrderTraversal(node.right);	// 오른쪽
	  			visit(node);	// 중앙
	  		}
		}
		```

		
		
##### 🔮 <u>이진 탐색 트리</u> (Binary Search Tree)

- 모든 노드가 아래와 같은 특정 순서를 따르는 속성이 있는 이진 트리

- **<u>모든 왼쪽 자식들 <= `n` < 모든 오른쪽 자식들 (모든 노드에 대해서 반드시 참)</u>**

- **<u>Binary Tree + BST invariant</u>**
	- BST invariant : 왼쪽 subTree 는 더 작은 값을, 오른쪽 subTree은 더 큰 값을 가진다.
	- 중복된 값을 가지고 있다면 나의 정의에 따라 valid를 정한다. BST Operation은 중복된 값을 허용하지만, 보통의 경우 중복되지 않은 원소들을 갖는 트리에 관심이 있다.

- **<u>Adding Elements to BST</u>**
	- 모든 원소들은 comparable 해야함
	- Insert 시 4가지 경우 존재 ( 항상 root에서 시작)
		- **작은 경우** Recurse down left subtree
		- **큰 경우** Recurse down right subtree
		- **같은 경우** Handling
		- **null leaf인 경우** Create new node
	- linear 한 경우( O(n)인 경우)
		- 1,2,3,4,5,6 순으로 adding 하면 직선 형태를 이루면서 최악의 시간복잡도인 O(n)을 가지게 됨!    
		→ 이러한 경우 때문에 **balanced binary search tree**가 개발됨.

- **<u>Removing Elements from BST</u>**
	- 2단계로 구성
		- **<u>Find 단계</u>** :   
		Comparator를 통해 root부터 시작해 제거하려는 원소를 찾음    
		( 0 찾음 / 1 더 큼 / -1 더 작음 / null 존재 x)
		- **<u>Remove 단계</u>** :   
		successor를 통해 제거할 노드를 BST invariant를 충족하는 노드와 교체, 4가지 경우 존재
			- **1) 제거하려는 노드가 leaf 인 경우(자식 x)** : 바로 제거
			- **2) left subTree 존재하는 경우** : successor가 subTree의 root를 가리키고 제거하려는 노드 제거 후 그 자리에 successor가 가리키는 노드를 붙임
			- **3) right subTree 존재하는 경우** : successor가 subTree의 root를 가리키고 제거하려는 노드 제거 후 그 자리에 successor가 가리키는 노드를 붙임
			- **4) 두 subTrees 존재하는 경우** : <u>left subTree의 원소들 중 가장 큰 값(가장 오른쪽으로 내려가면 됨)</u>이나 <u>right subTree의 원소들 중 가장 작은 값(가장 왼쪽으로 내려가면 됨)</u>을 successor로 가리키고 그 값을 제거할 노드값에 넣음
→  left subtree의 원소들보다 무조건 크고 right subTree 원소들보다 무조건 작으므로 BST invariant 만족

- **<u>Complexity of BST</u>**
	- **Insert** : 평균 O(logn) / 최악 O(n)
	- **Delete** : 평균 O(logn) / 최악 O(n)
	- **Remove** : 평균 O(logn) / 최악 O(n)
	- **Search** : 평균 O(logn) / 최악 O(n)
	

##### 🔮 <u>균형 트리</u> 

- O(logN) 시간에 insert와 find를 할 수 있을 정도로 **<u>균형이 잘 잡혀 있는 경우</u>**
- Ex) 레드-블랙 트리, AVL 트리


##### 🔮 <u>완전 이진 트리</u> (Complete Binary Tree)

<img width="484" alt="Screen Shot 2022-01-11 at 7 31 55 PM" src="https://user-images.githubusercontent.com/63195670/148926588-e315f68f-eddc-4e3c-90cf-4c4a7ac568c8.png">


- 마지막 레벨을 제외하고 모든 레벨이 완전히 채워져 있다.
- 마지막 레벨은 꽉 차 있지 않아도 되지만 **<u>노드가 왼쪽에서 오른쪽으로 채워져야 한다</u>.**
- 마지막 레벨 h에서 (1 ~ 2h-1)개의 노드를 가질 수 있다.
- 또 다른 정의는 가장 오른쪽의 잎 노드가 (아마도 모두) 제거된 포화 이진 트리다.
- 완전 이진 트리는 탈모 현상 없이 차곡차곡 채워져서 들어오기 때문에 **<u>배열을 사용해 효율적으로 표현 가능</u>**하다.


##### 🔮 <u>전 이진 트리</u> (Full Binary Tree / Strictly Binary Tree)

<img width="484" alt="Screen Shot 2022-01-11 at 7 34 35 PM" src="https://user-images.githubusercontent.com/63195670/148926968-f531beec-45c8-4009-8920-48087b6a55b5.png">

- 모든 노드가 0개 또는 2개의 자식 노드를 갖는 트리.


##### 🔮 <u>포화 이진 트리</u> (Perfect Binary Tree)

<img width="257" alt="Screen Shot 2022-01-11 at 7 35 36 PM" src="https://user-images.githubusercontent.com/63195670/148927104-2909ca11-1e42-4e0c-8f9d-3d0231474fbb.png">


- 전 이진 트리이면서 완전 이진 트리인 경우
- 모든 말단 노드는 같은 높이에 있어야 하며, 마지막 단계에서 노드의 개수가 최대가 되어야 한다.
- 모든 내부 노드가 두 개의 자식 노드를 가진다.
- 모든 말단 노드가 동일한 깊이 또는 레벨을 갖는다.
- 노드의 개수가 정확히 2^(k-1)개여야 한다. (k: 트리의 높이) -> 흔하게 나타나는 경우가 아니다. 즉, 이진 트리가 모두 포화 이진 트리일 것이라고 생각하지 않는다.


##### 🔮 <u>트라이</u> (trie)

- '접두사 트리(Prefix Tree)라고도 부른다.
- n-차 트리(n-ary Tree)의 변종
- 각 노드에 문자를 저장하는 자료구조
- 따라서 트리를 아래쪽으로 순회하면 단어 하나가 나온다.
- **<u>접두사를 빠르게 찾아보기 위한 흔한 방식</u>**으로, 모든 언어를 트라이에 저장해 놓는 방식이 있다.
- **<u>유효한 단어 집합을 이용</u>**하는 많은 문제들은 트라이를 통해 최적화할 수 있다.

#### ✏️ <u>트리의 구현방법</u>

기본적으로 트리는 그래프의 한 종류이므로 그래프의 구현 방법 (인접 리스트 or 인접 배열) 으로 구현할 수 있다.

##### 🔮 **<u>인접 배열 이용</u>**

- 1차원 배열에 자신의 부모 노드만 저장하는 방법
	- Ex) A[i][0]: 왼쪽 자식 노드, A[i][1]: 오른쪽 자식 노드


- 이진 트리의 경우, 2차원 배열에 자식 노드를 저장하는 방법
	- Ex) A[i][0]: 왼쪽 자식 노드, A[i][1]: 오른쪽 자식 노드


##### 🔮 **<u>인접 리스트 이용</u>**

- 가중치가 없는 트리의 경우
	`ArrayList< ArrayList > list = new ArrayList<>();`

- 가중치가 있는 트리의 경우.   
	- 1) `class Node { int num, dist; // 노드 번호, 거리 }` 정의
	- 2) `ArrayList[] list = new ArrayList[정점의 수 + 1];`


<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>그래프와 트리의 차이</u></strong>   

<img width="745" alt="Screen Shot 2022-01-11 at 7 52 14 PM" src="https://user-images.githubusercontent.com/63195670/148929651-9fa3b0c3-9990-425f-850a-cd2dcbaaceee.png">

</div>



### [3] Heap

- 완전 이진 트리의 일종으로 우선순위 큐를 위하여 만들어진 자료구조이다.

<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>우선 순위 큐가 무엇일까?</u></strong>   

우선 순위의 개념을 큐에 도입한 자료 구조이다.    
데이터들이 우선순위를 가지고 있고 우선순위가 높은 데이터가 먼저 나감!    

<img width="408" alt="Screen Shot 2022-01-12 at 11 49 12 AM" src="https://user-images.githubusercontent.com/63195670/149055070-f6fec992-fd0e-4799-92f3-29a10c5b7f79.png">      

📌 <strong><u>우선 순위 큐의 이용사례</u></strong>    
- 시뮬레이션 시스템   
- 네트워크 트래픽 제어    
- 운영 체제에서의 작업 스케쥴링    
- 수치 해석적인 계산    

우선순위 큐는 배열, 연결 리스트, 힙으로 구현이 가능하다. 이 중, 힙(heap)으로 구현하는 것이 가장 효율적이다.     

<img width="398" alt="Screen Shot 2022-01-12 at 11 52 47 AM" src="https://user-images.githubusercontent.com/63195670/149055404-01ffaa3a-a323-4fc9-957f-05ae5985b7a4.png">        

<a href = "https://chanhuiseok.github.io/posts/ds-4/"> 자세한 정리 링크  </a>
</div>

- 여러 개의 값들 중에서 최댓값이나 최솟값을 빠르게 찾아내도록 만들어진 자료구조이다.

- 힙은 일종의 **<u>반정렬 상태(느슨한 정렬 상태)</u>**를 유지한다.
	- 큰 값이 상위 레벨에 있고 작은 값이 하위 레벨에 있다는 정도
	- 간단히 말하면 부모 노드의 키 값이 자식 노드의 키 값보다 항상 큰(작은) 이진 트리를 말한다.

- **힙 트리에서는 중복된 값을 허용한다.(이진 탐색 트리에서는 중복된 값을 허용하지 않는다.)**


#### ✏️ <u>힙(heap)의 종류</u>

##### 🔮 <u>최대 힙(max heap)</u>

- 트리의 마지막 단계에서 오른쪽 부분을 뺀 나머지 부분이 가득 채워져 있는 **<u>완전 이진 트리</u>**
- 각 노드의 원소가 자식들의 원소보다 작다.
- 즉, **<u>key(부모노드) <= key(자식노드)</u>**인 완전 이진 트리
- 가장 작은 값이 루트 노드이다.
- N개가 힙에 들어가 있으면 높이는 log(N)

##### 🔮 <u>최소 힙(min heap)</u>

- **원소가 <u>내림차순</u>으로 정렬**되어 있다는 점에서만 최소힙과 다르다.
- 부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리
- key(부모 노드) <= key(자식 노드)

<img width="771" alt="Screen Shot 2022-01-12 at 12 08 39 PM" src="https://user-images.githubusercontent.com/63195670/149057011-f5c07c20-7db2-4fef-bc10-2521b75e7b9f.png">


#### ✏️ <u>힙(heap)의 구현</u>

- **힙을 저장하는 표준적인 자료구조는 <u>배열</u>이다.**
- 구현을 쉽게 하기 위하여 **배열의 첫 번째 인덱스인 <u>0은 사용되지 않는다</u>.**
- **특정 위치의 노드 번호는 새로운 노드가 추가되어도 변하지 않는다.**
	- 예를 들어 루트 노드의 오른쪽 노드의 번호는 항상 3이다.
- **<u>힙에서의 부모 노드와 자식 노드의 관계</u>**
	- **왼쪽 자식의 인덱스**= (부모의 인덱스) * 2
	- **오른쪽 자식의 인덱스** = (부모의 인덱스) * 2 + 1
	- **부모의 인덱스** = (자식의 인덱스) / 2

<img width="686" alt="Screen Shot 2022-01-12 at 12 18 05 PM" src="https://user-images.githubusercontent.com/63195670/149057869-aa5f0e0e-9549-44a9-b759-f6e3c74be498.png">   

##### 🔮 <u>c언어를 이용한 힙(heap)의 구현</u>

```
# define MAX_ELEMENT 200 // 힙 안에 저장된 요소의 개수
	
typedef struct{
 	int key;
} element;

typedef struct{
	element heap[MAX_ELEMENT];
	int heap_size;
} HeapType;

# 힙의 생성
HeapType heap1;
```

#### ✏️ <u>힙(heap)의 삽입</u>


1. 힙에 새로운 요소가 들어오면, 일단 새로운 노드를 힙의 마지막 노드에 이어서 삽입한다.
2. 새로운 노드를 부모 노드들과 교환해서 힙의 성질을 만족시킨다.

##### 🔮 <u>예시</u> : <u>최대 힙(max heap)에 새로운 요소 삽입</u> 

아래의 최대 힙(max heap)에 새로운 요소 8을 삽입해보자.

<img width="558" alt="Screen Shot 2022-01-12 at 12 40 27 PM" src="https://user-images.githubusercontent.com/63195670/149059830-973d6f17-2775-4489-bc84-68b453e448f8.png">

##### 🔮 <u>c언어를 이용한 최대 힙(max heap) 삽입 연산</u>

```
/* 현재 요소의 개수가 heap_size인 힙 h에 item을 삽입한다. */
// 최대 힙(max heap) 삽입 함수
void insert_max_heap(HeapType *h, element item){
  int i;
  i = ++(h->heap_size); // 힙 크기를 하나 증가

  /* 트리를 거슬러 올라가면서 부모 노드와 비교하는 과정 */
  // i가 루트 노트(index: 1)이 아니고, 삽입할 item의 값이 i의 부모 노드(index: i/2)보다 크면
  while((i != 1) && (item.key > h->heap[i/2].key)){
    // i번째 노드와 부모 노드를 교환환다.
    h->heap[i] = h->heap[i/2];
    // 한 레벨 위로 올라단다.
    i /= 2;
  }
  h->heap[i] = item; // 새로운 노드를 삽입
}
```

##### 🔮 <u>java언어를 이용한 최대 힙(max heap) 삽입 연산</u>

```
/* 최대힙 삽입 */
void insert_max_heap(int x){
maxHeap[++heapSize] = x; // 힙 크기를 하나 증가하고 마지막 노드에 x를 넣는다.

for (int i=heapSize; i>1; i/=2) {
  // 마지막 노드가 자신의 부모 노드보다 크면 swap
  if (maxHeap[i/2] < maxHeap[i]) {
    swap(i/2, i);
  } else {
    break;
  }
}
}
```


#### ✏️ <u>힙(heap)의 삭제</u>


1. 최대 힙에서 최댓값은 루트 노드이므로 루트 노드가 삭제된다.
	- 최대 힙(max heap)에서 삭제 연산은 최댓값을 가진 요소를 삭제하는 것이다.
2. **삭제된 <u>루트 노드에는 힙의 마지막 노드를 가져온다</u>.**
3. **힙을 재구성**한다.

##### 🔮 <u>예시</u> : <u>최대 힙(max heap)에서 최댓값 삭제</u> 

아래의 최대 힙(max heap)에서 최댓값을 삭제해보자.

<img width="543" alt="Screen Shot 2022-01-12 at 12 49 24 PM" src="https://user-images.githubusercontent.com/63195670/149060691-855d584c-6d63-40c4-8beb-50b1bc8873a1.png">   

##### 🔮 <u>c언어를 이용한 최대 힙(max heap) 삽입 연산</u>

```
// 최대 힙(max heap) 삭제 함수
element delete_max_heap(HeapType *h){
  int parent, child;
  element item, temp;

  item = h->heap[1]; // 루트 노드 값을 반환하기 위해 item에 할당
  temp = h->heap[(h->heap_size)--]; // 마지막 노드를 temp에 할당하고 힙 크기를 하나 감소
  parent = 1;
  child = 2;

  while(child <= h->heap_size){
    // 현재 노드의 자식 노드 중 더 큰 자식 노드를 찾는다. (루트 노드의 왼쪽 자식 노드(index: 2)부터 비교 시작)
    if( (child < h->heap_size) && ((h->heap[child].key) < h->heap[child+1].key) ){
      child++;
    }
    // 더 큰 자식 노드보다 마지막 노드가 크면, while문 중지
    if( temp.key >= h->heap[child].key ){
      break;
    }

    // 더 큰 자식 노드보다 마지막 노드가 작으면, 부모 노드와 더 큰 자식 노드를 교환 -> 어차피 삭제하고 temp 값을 넣을 것이므로 괜찮음!
    h->heap[parent] = h->heap[child];
    // 한 단계 아래로 이동
    parent = child;
    child *= 2;
  }

  // 마지막 노드를 재구성한 위치에 삽입
  h->heap[parent] = temp;
  // 최댓값(루트 노드 값)을 반환
  return item;
}
```

##### 🔮 <u>java언어를 이용한 최대 힙(max heap) 삽입 연산</u>

```
/* 최대힙 삭제 */
int delete_max_heap(){
if (heapSize == 0) // 배열이 빈 경우
  return 0;

int item = maxHeap[1]; // 루트 노드의 값을 저장한다.
maxHeap[1] = maxHeap[heapSize]; // 마지막 노드의 값을 루트 노드에 둔다.
maxHeap[heapSize--] = 0; // 힙 크기를 하나 줄이고 마지막 노드를 0으로 초기화한다.

for (int i=1; i*2<=heapSize;) {
  // 마지막 노드가 왼쪽 노드와 오른쪽 노드보다 크면 반복문을 나간다.
  if (maxHeap[i] > maxHeap[i*2] && maxHeap[i] > maxHeap[i*2+1]) {
    break;
  }
  // 왼쪽 노드가 더 큰 경우, 왼쪽 노드와 마지막 노드를 swap
  else if (maxHeap[i*2] > maxHeap[i*2+1]) {
    swap(i, i*2);
    i = i*2;
  }
  // 오른쪽 노드가 더 큰 경우, 오른쪽 노드와 마지막 노드를 swap
  else {
    swap(i, i*2+1);
    i = i*2+1;
  }
}
return item;
}
```



<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>What is the difference between linear and non-linear data structures?</u></strong>   

The following illustrates the significant differences between the linear and non-linear data structures:   

🏹 <strong><u>Linear Data Structure</u></strong>  
1. In linear data structures, each element is linearly connected to each other having reference to the next and previous elements.  
2. Implementation is quite easy as only a single level is involved.   
3. Wastage of memory is much more common in linear data structures.   
4. Stacks, Queues, Arrays, and Linked lists are all examples of linear data structures.   

🏹 <strong><u>Non-Linear Data Structure</u></strong>   
1. In non-linear data structures, the elements are connected in a hierarchical manner.   
2. Implementation is much more complex as multiple levels are involved.   
3. Memory is consumed wisely and there is almost no wastage of memory.   
4. Graphs and trees are examples of non-linear data structures.   
</div>

DS는 여기서 끝 〰️
	
	
### 🔗 출처	
* [Non-Linear Data Structure 참고 사이트](https://alldifferences.net/difference-between-linear-and-non-linear-data-structure/)
* [Graph 참고 사이트](https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html)
* [Tree 참고 사이트 1](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html)     
* [Tree 참고 사이트 2](https://jiwondh.github.io/2017/10/15/tree/)
* [Tree 참고 사이트 3](https://velog.io/@huttels/Binary-Trees-Binary-Search-TreesBST)
* [힙 참고 사이트 1](https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html)
* [힙 참고 사이트 2](https://velog.io/@kjh107704/Heap)
