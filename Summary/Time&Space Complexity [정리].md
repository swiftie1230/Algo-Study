# 시간복잡도와 공간복잡도 ✍🏻


So, before knowing the data structure(Algorithm), you should know about Time and Space complexity because of it you can analyze your algorithm that how fast and how efficient it is (It's very important concept)!

레츠고고 ╰(//´︶`//)╯♡

--


Sometimes, there are more than one way to solve a problem. We need to learn how to compare the performance different algorithms and choose the best one to solve a particular problem. While analyzing an algorithm, we mostly consider time complexity and space complexity.    

Time complexity of an algorithm quantifies the amount of time taken by an algorithm to run as a function of the length of the input. Similarly, Space complexity of an algorithm quantifies the amount of space or memory taken by an algorithm to run as a function of the length of the input.    

Time and space complexity depends on lots of things like hardware, operating system, processors, etc. <strong>However, we don't consider any of these factors while analyzing the algorithm. <u>We will only consider the execution time of an algorithm</u></strong>.


찾아서 공부하다 가장 설명도 깔끔하고 이해도 잘 되어서 바로 가져왔다! 해석은 해 놓겠지만 원문이 뭔가 더 좋고..깔끔하고..그래서 원문을 위에 조심스레 놓아보았음 👀   

아래는 내 번역? 해석!    


종종, 한 문제를 해결하는 데에는 한 개 이상의 방법이 존재한다. 우리는 다른 알고리즘의 성능(Performance)들을 비교하고, 해당 문제를 해결하는 데 최적의 방법을 선택해야 한다. 알고리즘을 분석(평가)할 때 우리는 시간복잡도(Time Complexity)와 공간복잡도(Space Complexity)를 최우선으로 고려한다.      

알고리즘의 시간복잡도(Time Complexity)는 입력(input)의 길이(length)에 대한 함수로 알고리즘을 수행하는 데 걸린 시간을 정량화한다. 비슷하게, 알고리즘의 공간복잡도(Space Complexity)는 입력(input)의 길이(length)에 대한 함수로 알고리즘을 수행 시 사용된 공간 또는 메모리를 정량화한다고 보면 됨.     

시간과 공간 복잡도는 하드웨어, OS(operating system : 운영체제), Processors(컴구 시간에 배웠던 새X..ㅎ..반가워 😶‍🌫️).. 등 많은 것들에 영향을 받는다. 그러나! 버뜨! 알고리즘을 분석(평가)할 때 우리는 이 모든 요인들은 고려하지 않는다. 오직 알고리즘의 실행 시간(Execution time)만이 우리의 관심.


## 📌 효율적인 알고리즘

프로그램의 규모는 시간이 지날수록 방대해지고 있다. 즉, 처리해야하는 데이터의 양이 많아진다는 것.

알고리즘 간의 효율성 차이는 입력하는 데이터의 양이 적은 경우에는 무시해도 크게 상관이 없을 수 있지만, 그 양이 많아지면 무시할 수 없게 된다.

그렇다면 과연 여기서 **효율적인 알고리즘**이란 무엇일까?     
알고리즘이 수행을 시작하여 결과가 도출될 때까지 **실행에 걸리는 시간이 짧고 연산하는 컴퓨터 내의 메모리와 같은 자원을 덜 사용하는 것이 효율적이라고 할 수 있다**.

## 📌 동일한 알고리즘의 효율성에 따른 구분 

또, 동일한 알고리즘도 입력되는 데이터에 따라 다른 실행 시간을 보일 수 있다.

예를 들어, 정렬을 하는 알고리즘에 대부분 정렬이 완료되어 있는 데이터를 입력한다면 뒤죽박죽 섞여있는 데이터 집합보다 더 빨리 정렬이 완료될 것이다.

그래서 알고리즘의 효율성은 **입력되는 데이터의 집합**에 따라 3가지의 경우로 나누어 평가할 수 있음.

> **최선의 경우(Best Case)** : 실행 시간이 가장 적은 경우   
> 
> **평균적인 경우(Average Case)** : 모든 입력을 고려하고 각 입력이 발생하는 확률을 고려한 평균 수행 시간  
> 
> **최악의 경우(Worst case)** : 알고리즘의 수행 시간이 가장 오래 걸리는 경우


언뜻 보면 평균적인 경우의 실행 시간이 가장 좋아보이지만 광범위한 데이터 집합에 대하여 알고리즘을 적용시켜 평균 값을 계산하는 것은 매우 어려울 수도 있다. 따라서 시간 복잡도의 척도를 계산할 때는 최악의 경우를 주로 사용 (O-notation)한다.    


<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>Notation에 대해 알아보자!</u></strong>   

역시 정리된 원문을 가져왔다.    

<strong><u>Order of growth</u></strong> is how the time of execution depends on the length of the input. Order of growth will help us to compute the running time with ease. We will ignore the lower order terms, since the lower order terms are relatively insignificant for large input. We use different notation to describe limiting behavior of a function.

- <strong><u>O-notation(Big-0 notation)</u></strong> :
To denote asymptotic upper bound, we use O-notation. Big O notation specifically describes worst case scenario.   

- <strong><u>Ω-notation(Omega notation)</u></strong> :
To denote asymtptotic lower bound, we use Ω-notation. Omega(Ω) notation specifically describes best case scenario.   

- <strong><u>Θ-notation(Theta notation)</u></strong> :
To denote asymptotic tight bound, we use Θ-notation. This notation represents the average complexity of an algorithm. 
</div>


## 📌 시간복잡도와 시간복잡도 함수

시간 복잡도(Time Complexity)는 알고리즘의 절대적인 실행 시간을 나타내는 것이 아닌 알고리즘을 수행하는 데 연산들이 몇 번 이루어지는 지를 숫자로 표기한다. 여기서 연산의 종류는 산술, 대입, 비교, 이동을 말한다. 그런데 **연산(Operation)의 실행 횟수는 보편적으로 그 값이 변하지 않는 상수(Constant)가 아니라 입력한 데이터의 개수를 나타내는 n에 따라 변함**.   

**연산의 개수를 입력한 데이터의 개수 n의 함수로 나타낸 것을 시간 복잡도 함수라고 말한다**.

##  📌 공간복잡도

공간 복잡도(Space Complexity)란, 프로그램을 실행시킨 후 완료하는 데 필요로 하는 자원 공간의 양을 말한다.

**총 공간 요구 = 고정 공간 요구 + 가변 공간 요구**로 나타낼 수 있으며 수식으로는 S(P) = c + S<sub>p</sub>(n) 으로 표기한다.

여기서 **고정 공간**은 **입력과 출력의 횟수나 크기와 관계없는 공간의 요구**(코드 저장 공간, 단순 변수, 고정 크기의 구조 변수, 상수)를 말함.

**가변 공간**은 **해결하려는 문제의 특정 인스턴스에 의존하는 크기를 가진 구조화 변수들을 위해서 필요로 하는 공간, 함수가 순환 호출을 할 경우 요구되는 추가 공간, 그러니까 동적으로 필요한 공간**을 말한다.

## 📌 Time Complexity vs Space Complexity

시간 복잡도는 “얼마나 빠르게 실행되느냐” 그리고 공간 복잡도는 “얼마나 많은 자원이 필요한가?” 

정리해보자면, 좋은 알고리즘이란, “시간도 적게 걸리고 자원의 사용도 적어야 하는 것”

하지만, 시간과 공간은 반비례적인 경향이 있기 때문에 **알고리즘의 척도는 시간 복잡도를 위주로 판단**한다.
그러니까 시간 복잡도만 괜찮다면 공간 복잡도는 어느 정도 이해를 해준다는 것! 특히나 요즘과 같은 대용량 시대에는!
	
	
###  # 출처	
* [알고리즘 로드맵 사이트](https://dev.to/suchitra_13/complete-roadmap-to-learn-data-structure-and-algorithms-1pka)
* [원문 사이트](https://www.hackerearth.com/practice/basic-programming/complexity-analysis/time-and-space-complexity/tutorial/)     
* [시간복잡도 및 공간복잡도 참고 사이트](https://madplay.github.io/post/time-complexity-space-complexity)
