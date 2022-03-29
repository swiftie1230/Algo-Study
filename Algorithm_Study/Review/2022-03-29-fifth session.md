# ✏️ <u>Topological Sort</u> + <u>BFS</u>  



## 📝 Topological Sort

Topological Sort, BFS가 제일 많이 쓰이는 곳과, 대표적으로 많이 나오는 문제 유형은 일단 **<u>네트워크</u>**!              

Tolpological Sort를 할 때 중요한 것이 몇 가지가 있는데, 이에 대해서 먼저 알아보자.    

1. It has to be a **<u>directed graph</u>**! : bi-directed graph에 대해서는 topological sort를 적용할 수가 없음!     

2. **<u>adjacency matrix</u>** : topological sort는 **<u>matrix</u> 형식**으로 되어 있어야 한다.

보통 Topological Sort 관련 문제들에서는 아래와 같은 형태의 `array`로 그래프가 주어진다.    

```python
[[from, to], [from, to], ....]
```

그런데 이 상태로는, 이것만 가지고는 우리가 그래프 문제를 풀기가 어려움 T^T     
그렇기에 **우리가 원하는 방식대로, 최대한 우리가 DFS나 BFS를 돌릴 수 있게 만들어주는, 과정을 거쳐야 하는데, 이게 바로 Topological Sort**!     
그리고 해당 과정을 거친 후, adjacency matrix로 표현이 되야 하는 거겠지?         

예를 들어 다양한 네트워크 서버들의 연결과 같은 관계성을 나타낸 그래프가 주어지고 `source`와 `destination`이 있을 때, **<u>Topological Sort</u>**는 갈 수 있는 방법, 어떤 식으로 순서를 정해야 하느냐 등의 문제에 필요한 **"REARRANGE"**를 하는 것이라고 할 수 있다.    



* * *



그럼 이제 본격적으로 Topological Sort와 BFS를 사용하는 실전 문제를 접해보자!   
실제로 강의해 주시며 예시로 들으셨던 문제였다 🌝    

## 💬 Problem

### 📄 문제 설명

<img width="457" alt="Screen Shot 2022-03-29 at 9 50 07 PM" src="https://user-images.githubusercontent.com/63195670/160614916-5edbd9b0-542c-425f-807a-b2e4f9b6a273.png">    

이 그래프들의 모든 `[from, to]` 들이 `2D array`로 주어졌다고 가정해보자.    

이렇게 input이 주어졌을 때, 처음 생각해봐야 할 건 바로 **<u>SOURCE</u>**다. SOURCE의 정확한 뜻은 **들어오는 게 없다**는 걸 의미!     
또, 반대로 **나가는 게 없는 것**들은 **<u>SINK</u>**라고 하고, 여기서는 이 둘을 찾는 게 중요하다.      

그런 후, SOURCE에서 SINK까지의 모든 경로를 찾을 때 DFS를 사용하거나, 가장 빠른 경로를 찾을 때 BFS를 사용하는 것!    

이 문제에서는 최단 경로의 길이를 찾기 위해 BFS를 사용해 코드를 작성해 보자.     
해결하기 위해 해야 할 일은 크게 아래 두 단계라는 건 이제 알겠지?    

1. **First Step : <u>Topological Sort</u>**
2. **Second Step : <u>BFS</u>**


<div class="notice--primary" markdown="1">
🙋🏻‍♀️ <strong><u>여기서 잠깐!</u></strong>    

그리고 참고로 덧붙이자면, 이 예제에서는 <code>airport들</code>로 명시했지만 이름만 바꾸면 바로 네트워크 문제가 되는 것을 확인할 수 있다.   
이런 문제들 네이버, 카카오에서 하나 이상은 꼭 나온다고 하니 꼭 정확하게, 자세히 짚고 넘어가자 👩🏻‍💻   
    
</div>


이제 코드를 작성해보자.        
일단 input 2D array 먼저!        

```python
inputs = [['S', 'J'], ['S', 'I'], ['J', 'Mex'], ['J', 'Mor'], ['Mor', 'H'], ['Mor', 'Jap'], ['Mex', 'Jap'], ['Jap', 'E'], ['Jap', 'C'], ['Jap', 'F'], ['I', 'F']]
```

우리는 이 문제를 해결하기 위해 네 가지 함수를 작성할 것이다! `solution`, `topological_sort`, `BFS`, 그리고 `find_the_source`까지.          

**`solution`은 우리가 말 그대로 이 문제를 수행하기 위해 처음 부르는 함수**. 일반 프로그램들의 `main`함수라고 생각하면 이해하기 쉬울 것.        

**`topological_sort`은 `topological sort`을 사용하여 `input`으로 주어진 `2D array`를 traversing 할 수 있도록 `dictionary(graph)`로 변환하여 리턴하는 함수**이다.     

다음으로 **`find_the_source`는 변환한 `dictionary`를 이용해 "Source"를 찾아 리턴하는 함수**이고, **`BFS`는 순환을 돌려 이 문제에서의 답, 즉, 최단 거리를 리턴하는 함수**!      


<div class="notice--primary" markdown="1">
🙋🏻‍♀️ <strong><u>여기서 잠깐!</u> : <u>왜 이렇게 굳이 많은 함수들을?</u></strong>    

<strong>우리가 function이라고 정해 놓은 것들은 <u>정확하게 주어진 기능만, 즉, 내가 이름을 정한 것만  수행</u>해야 한다!</strong> 그래야 좋은 코드, 가독성이 좋고 깔끔한 코드가 될 수 있겠지. 그 이상을 함수가 수행하게 되면 코드는 복잡해지고, 지저분해질 수밖에 없음..       

귀찮지만! 매우 좋은 연습이니, breakdown하는 것에 익숙해지자 👩🏻‍💻
    
</div>

이제 한 번 코드를 작성해보자.    
자세한 내용은 주석을 참고!   

```python
# topological에서 리턴할 dict형태를 만들어줄 때 필요한 defaultdict import
from collections import defaultdict

# BFS에서 필요한 queue 때문에 deque import
from collections import deque

# 그래프 형태를 2D array로 입력받는다.
inputs = [['S', 'J'], ['S', 'I'], ['J', 'Mex'], ['J', 'Mor'], ['Mor', 'H'], ['Mor', 'Jap'], ['Mex', 'Jap'], ['Jap', 'E'], ['Jap', 'C'], ['Jap', 'F'], ['I', 'F']]

def solution(list, target):
    if len(list) == 0:
        return []
	
    adjacency_list = topological_sort(list)
    
    return BFS(adjacency_list)
	
# input으로 주어진 2D array를 내가 현재 traversing 할 수 있도록 dictionary(graph)를 만들어주었다!   
def topological_sort(list):
    route = lambda:{'incoming': 0, 'dest': []}
    
    map = defaultdict(route)
    
    for i in range(len(list)):
        from_node = list[i][0]
        to_node = list[i][1]
	
	# 도착지 dest에 append	
        map[from_node]['dest'].append(to_node)
	
	# to_node는 들어오는 것이 하나 있다는 뜻이므로 1 증가	
	map[to_node]['incoming'] += 1
		
    return map


    
def BFS(graph, target):
    source = find_the_source(graph)

    if not source:
        return 'We cannot find the source'
    
    # source에서의 initial_depth = 0 (마치 source가 root인 트리처럼 생각하는 것)
    queue = deque([[source, 0]])

    # while and queue
    while queue:
        [key, current_depth] = queue.popleft()
        current_node = graph[key]

        children = current_node['dest']

        if key == target:
            return current_depth
        
        for i in range(len(children)):
            queue.append([children[i], current_depth+1])

    return -1
					

def find_the_source(graph):
    for key, val in graph.items():
        if val['incoming'] == 0:
            return key
    
    # edge case
    return None
		

print(solution(inputs, 'F'))
```

<div class="notice--primary" markdown="1">
🙋🏻‍♀️ <strong><u>여기서 잠깐!</u> : <u><code>route = lambda:{'incoming': 0, 'dest': []}</code></u> 이건 뭐죠? </strong>     

그냥 <code>route = {'incoming': 0, 'dest': []}</code> 로 선언하여 사용했을 경우, <code>TypeError: first argument must be callable or None</code>라는 오류가 발생했다.     

당황해서 찾아보니, 이런 이유라고 함.     

<strong><u>For a defaultdict the default value is usually not really a value, it a factory</u>: a method that generates a new value.</strong> You can solve this issue by using a lambda expression that generates whatever you wanted.      

나는 여기서. <code> {'incoming': 0, 'dest': []} </code>라는 특정 <code>dictionary</code>를 default 인수로 하는 <code>defaultdict</code>를 만들고자 했으므로, <code>lambda:{'incoming': 0, 'dest': []}</code>라고 작성하면 되는 것이다!       

혹여나 defaultdict가 뭔지 모른다! 혹은 잊어버렸다! 의 경우라면 <a href="https://dongdongfather.tistory.com/69">"이 링크"</a>를 참고하자!       
    
</div>


그럼 만약 최단 경로의 길이가 아닌, **<u>최단 경로체자체를 리턴</u>하고 싶다**면 어떻게 하면 될까?      
간단하다. BFS 함수에서 `depth` 대신 `path`를 기록하면 됨!     

     
```python           
def BFS(graph, target):
    source = find_the_source(graph)

    if not source:
        return 'We cannot find the source'
    
    path = source
    
    queue = deque([[source, path]])

    while queue:
        key, current_path = queue.popleft()
        
        current_node = graph[key]

        children = current_node['dest']

        if key == target:
            return current_path
        
        for i in range(len(children)):
            queue.append([children[i], current_path + ' -> ' + children[i]])       
        

    return -1
```




<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>다시 보며 헷갈렸거나 새로웠던 내용</u></strong>        

1. Topological Sort         
2. BFS    
3. Queue : [] 주의!    
4. defaultdict     
5. defaultdict 안에 defaultdict 넣기!    

</div>
