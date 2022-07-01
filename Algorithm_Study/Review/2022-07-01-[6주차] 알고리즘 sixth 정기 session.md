# ✏️ <u>Advanced Topological Sort + BFS</u>  



## 📝 Advanced Topological Sort + BFS

저번 시간에 다양한 네트워크 서버들의 연결과 같은 관계성을 나타낸 그래프가 주어지고 `source`와 `destination`이 있을 때, **<u>Topological Sort</u>**는 갈 수 있는 방법, 어떤 식으로 순서를 정해야 하느냐 등의 문제에 필요한 **"REARRANGE"**를 하는 것이라고 배웠다.     

저번 강의 정리 링크 : [요기 !](https://swiftie1230.github.io/algorithm_study/알고리즘활용-TopologicalSort_BFS-정리/)

그렇다면 이번에는 조금 더 심화된, **우선순위가 주어져 있을 때, 그들 사이의 scheduling을 해보는 것**이다.      

예를 들어, 그래프의 모든 `[pre, post]` 들이  `[[math1, math2], [math0, math2], [math2, math3]]` 로 주어졌다고 가정해보자. (`pre`를 거친 후에야 `post`가 가능하다. 즉, 위 예시에서는 `math1`과 `math0`을 거쳐야 `math2`를 거칠 수 있는 것!)         

그렇다면 우리는 위 우선순위를 만족시키는 scheduling을 찾아 return 하는 알고리즘을 짜는 것이다.     
예를 들면 한가지 schedule은 `math0 → math1 → math2 → math3`가 있을 수 있겠지.    

이때 사용하는 방법이 바로 조금 더 심화된! **`Advanced Topological Sort + BFS`**다!



* * *



그럼 이제 본격적으로 Advanced Topological Sort + BFS를 사용하는 실전 문제를 접해보자!   
실제로 강의해 주시며 예시로 들으셨던 문제였다 🌝    

## 💬 Problem

### 📄 문제 설명   

모든 `[pre, from]` 들이 `2D array`로 주어졌다고 가정해보자.     

```python
[["math1", "math2"], ["math0", "math2"], ["math2", "math3"], ["math0", "math4"], ["math3", "math5"], ["math4", "math5"]]
```

이렇게 input이 주어졌을 때, 여기서 새롭게 생각해봐야 할 건 **<u>우선순위</u>**다. 이 문제에서 보면 `math1`과 `math0`가 선행되어야지만 `math2`를 거칠 수 있는 반면, `math4`는 `math0`만 거치면 가능하다. 따라서 이렇게 기존 topological sort 후, **<u>선행되어야 하는 노드들을 레벨별로 구분하여 큐에 넣어주고 schedule해야 한다</u>**는 것을 알 수 있다. 이 과정에서 **<u>BFS</u>**를 사용하는데, 이 때 큐에 다음으로 넣어주는 조건은 incoming, 여기서는 **<u>`pre`의 값이 `0`</u>이 되기 전까지는 넣어주지 않다가, 0이 되면 넣어주어야 한다**. (즉, **<u>그 전에 선행되어야 하는 노드들을 모두 거친 것을 확인한 후</u>에야 큐에 넣어준다**는 뜻.)                   

그렇다면 해결하기 위해 해야 할 일은 크게 아래 두 단계라는 건 알겠지? 또한 우리가 전에 배운 알고리즘에서 좀 더 심화하여 수정해야 할 부분은 BFS 단계라는 것 역시 인지할 수 있을 것이다.         

1. **First Step : <u>Topological Sort</u>**
2. **Second Step : <u>BFS</u>**


<div class="notice--primary" markdown="1">
🙋🏻‍♀️ <strong><u>여기서 잠깐!</u></strong>    

이 심화된 <strong><u>Advanced Topological Sort + BFS 문제</u></strong>가 Top 2에 들 정도로 어렵고, 그만큼 알아놓아야 할 주제라니까 꼭 꼼꼼히 공부해두기 ~ 👩🏻‍💻   
    
</div>


이제 코드를 작성해보자.        
일단 input 2D array 먼저!        

```python
inputs = [['S', 'J'], ['S', 'I'], ['J', 'Mex'], ['J', 'Mor'], ['Mor', 'H'], ['Mor', 'Jap'], ['Mex', 'Jap'], ['Jap', 'E'], ['Jap', 'C'], ['Jap', 'F'], ['I', 'F']]
```

우리는 이 문제를 해결하기 위해 네 가지 함수를 작성할 것이다! `solution`, `topological_sort`, `BFS`, 그리고 `find_the_source`까지.          

**`solutionAdvanced`은 우리가 말 그대로 이 문제를 수행하기 위해 처음 부르는 함수**. 일반 프로그램들의 `main`함수라고 생각하면 이해하기 쉬울 것.        

**`topologicalAdvanced`은 `topological sort`을 사용하여 `input`으로 주어진 `2D array`를 traversing 할 수 있도록 `dictionary(graph)`로 변환하여 리턴하는 함수**이다.     

다음으로 **`find_the_source`는 변환한 `dictionary`를 이용해 "Source"를 찾아 리턴하는 함수**이고, **`BFSAdvanced`는 선행되어야 하는 노드들을 레벨별로 구분하여 큐에 넣어주고 schedule하여 리턴하는 함수**!      


<div class="notice--primary" markdown="1">
🙋🏻‍♀️ <strong><u>여기서 잠깐!</u> : <u>왜 이렇게 굳이 많은 함수들을?</u></strong>    

매번 강조하고, 갈수록 뼈저리게 느끼고 있는 부분이다...😭          
<strong>우리가 function이라고 정해 놓은 것들은 <u>정확하게 주어진 기능만, 즉, 내가 이름을 정한 것만  수행</u>해야 한다!</strong> 그래야 좋은 코드, 가독성이 좋고 깔끔한 코드가 될 수 있겠지. 그 이상을 함수가 수행하게 되면 코드는 복잡해지고, 지저분해질 수밖에 없음..       

귀찮지만! 매우 좋은 연습이니, <strong><u>breakdown</u></strong>하는 것에 익숙해지자 👩🏻‍💻
    
</div>

이제 한 번 코드를 작성해보자.    
자세한 내용은 주석을 참고!   

```python
# topological에서 리턴할 dict형태를 만들어줄 때 필요한 defaultdict import
from collections import defaultdict

# BFS에서 필요한 queue 때문에 deque import
from collections import deque

# 그래프 형태를 2D array로 입력받는다.
inputs = [["math1", "math2"], ["math0", "math2"], ["math2", "math3"], ["math0", "math4"], ["math3", "math5"], ["math4", "math5"]]

def solutionAdvanced(list):
    if len(list) == 0:
        return []
	
    adjacency_list = topologicalAdvanced(list)
    
    return BFSAdvanced(adjacency_list)
	

# input으로 주어진 2D array를 내가 현재 traversing 할 수 있도록 dictionary(graph)를 만들어주었다!   
def topologicalAdvanced(list):
    route = lambda:{'pre': 0, 'post': []}
    
    map = defaultdict(route)
    
    for i in range(len(list)):
        pre_node = list[i][0]
        post_node = list[i][1]

	    # pre_node는 나가는 것이 하나 있다는 뜻이므로 post에 append	
        map[pre_node]['post'].append(post_node)
	
	    # post_node는 들어오는 것이 하나 있다는 뜻이므로 pre 1 증가	
        map[post_node]['pre'] += 1
		
    return map

    
def BFSAdvanced(graph):
    result = ""

    source = find_the_source(graph)

    if not source:
        return 'We cannot find the source'
    
    queue = deque([source])

    # while and queue
    while queue:
        currentLevel = queue.popleft()
        nextLevel = []
        
        for i in range(len(currentLevel)):
            key = currentLevel[i]
            children = graph[key]['post']

            if result == "":
                result += key
            else:
                result += ' -> ' + key

            for j in range(len(children)):
                child = children[j]
                graph[child]['pre'] -= 1
                
                if graph[child]['pre'] == 0:
                    nextLevel.append(child)
        
        if len(nextLevel) > 0:
            queue.append(nextLevel)

    return result

					

def find_the_source(graph):
    sources = []
    for key, val in graph.items():
        if val['pre'] == 0:
            sources.append(key)
    
    return sources
		

print(solutionAdvanced(inputs))
```


<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>다시 보며 헷갈렸거나 새로웠던 내용</u></strong>        

1. Topological Sort         
2. Advanced BFS        

</div>
