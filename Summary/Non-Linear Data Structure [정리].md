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



### [2] 트리(Tree)

- 노드로 이루어진 자료 구조로, 노드(node)들과 노드들을 연결하는 링크(간선)[link(edge)]들로 구성됨.

- 비선형 자료구조로 계층적 관계를 표현한다. Ex) 디렉터리 구조, 조직도

- 그래프의 한 종류
	- 사이클(cycle)이 없는 하나의 연결 그래프(Connected Graph)
	- 또는 DAG(Directed Acyclic Graph, 방향성이 있는 비순환 그래프)의 한 종류

#### ✏️ 트리와 관련된 용어

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


#### ✏️ 트리의 기본적인 성질 & 특징

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



#### ✏️ 트리의 종류

##### 🔮 **<u>이진트리(Binary Tree)</u>** 

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

		
		
##### 🔮 **<u>이진 탐색 트리(Binary Search Tree)</u>** 

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
	

##### 🔮 **<u>균형 트리</u>** 

- O(logN) 시간에 insert와 find를 할 수 있을 정도로 **<u>균형이 잘 잡혀 있는 경우</u>**
- Ex) 레드-블랙 트리, AVL 트리


##### 🔮 **<u>완전 이진 트리(Complete Binary Tree)</u>**

<img width="484" alt="Screen Shot 2022-01-11 at 7 31 55 PM" src="https://user-images.githubusercontent.com/63195670/148926588-e315f68f-eddc-4e3c-90cf-4c4a7ac568c8.png">


- 마지막 레벨을 제외하고 모든 레벨이 완전히 채워져 있다.
- 마지막 레벨은 꽉 차 있지 않아도 되지만 **<u>노드가 왼쪽에서 오른쪽으로 채워져야 한다</u>.**
- 마지막 레벨 h에서 (1 ~ 2h-1)개의 노드를 가질 수 있다.
- 또 다른 정의는 가장 오른쪽의 잎 노드가 (아마도 모두) 제거된 포화 이진 트리다.
- 완전 이진 트리는 탈모 현상 없이 차곡차곡 채워져서 들어오기 때문에 **<u>배열을 사용해 효율적으로 표현 가능</u>**하다.


##### 🔮 **<u>전 이진 트리(Full Binary Tree / Strictly Binary Tree)</u>**

<img width="484" alt="Screen Shot 2022-01-11 at 7 34 35 PM" src="https://user-images.githubusercontent.com/63195670/148926968-f531beec-45c8-4009-8920-48087b6a55b5.png">

- 모든 노드가 0개 또는 2개의 자식 노드를 갖는 트리.


##### 🔮 **<u>포화 이진 트리(Perfect Binary Tree)</u>**

<img width="257" alt="Screen Shot 2022-01-11 at 7 35 36 PM" src="https://user-images.githubusercontent.com/63195670/148927104-2909ca11-1e42-4e0c-8f9d-3d0231474fbb.png">


- 전 이진 트리이면서 완전 이진 트리인 경우
- 모든 말단 노드는 같은 높이에 있어야 하며, 마지막 단계에서 노드의 개수가 최대가 되어야 한다.
- 모든 내부 노드가 두 개의 자식 노드를 가진다.
- 모든 말단 노드가 동일한 깊이 또는 레벨을 갖는다.
- 노드의 개수가 정확히 2^(k-1)개여야 한다. (k: 트리의 높이) -> 흔하게 나타나는 경우가 아니다. 즉, 이진 트리가 모두 포화 이진 트리일 것이라고 생각하지 않는다.


##### 🔮 **<u>이진 힙(최소힙과 최대힙)</u>**

- **<u>최소힙(Min Heap)</u>**
	- 트리의 마지막 단계에서 오른쪽 부분을 뺀 나머지 부분이 가득 채워져 있는 **<u>완전 이진 트리</u>**
	- 각 노드의 원소가 자식들의 원소보다 작다.
	- 즉, **<u>key(부모노드) <= key(자식노드)</u>**인 완전 이진 트리
	- 가장 작은 값이 루트 노드이다.
	- N개가 힙에 들어가 있으면 높이는 log(N)

- **<u>최대힙(Max Heap)</u>**
	- **원소가 <u>내림차순</u>으로 정렬**되어 있다는 점에서만 최소힙과 다르다.
	- 각 노드의 원소가 자식들의 원소보다 크다.


##### 🔮 **<u>트라이(trie)</u>**

- '접두사 트리(Prefix Tree)라고도 부른다.
- n-차 트리(n-ary Tree)의 변종
- 각 노드에 문자를 저장하는 자료구조
- 따라서 트리를 아래쪽으로 순회하면 단어 하나가 나온다.
- **<u>접두사를 빠르게 찾아보기 위한 흔한 방식</u>**으로, 모든 언어를 트라이에 저장해 놓는 방식이 있다.
- **<u>유효한 단어 집합을 이용</u>**하는 많은 문제들은 트라이를 통해 최적화할 수 있다.

#### ✏️ 트리의 구현방법

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
* [Tree 참고 사이트 1](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html)     
* [Tree 참고 사이트 2](https://jiwondh.github.io/2017/10/15/tree/)
* [Tree 참고 사이트 3](https://velog.io/@huttels/Binary-Trees-Binary-Search-TreesBST)
