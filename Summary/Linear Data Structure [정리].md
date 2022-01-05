# Linear Data Structure ✍🏻

<div class="notice--primary" markdown="1">
<u><strong>Reducing space</strong></u> and <u><strong>decreasing the time complexity</strong></u> of different tasks is the <u><strong>main aim of data structures</strong></u>.   

Basically, there are two types of data structure.   

1. Primitive data structure (단순구조) : 프로그래밍에서 사용되는 기본 데이터 타입       
2. Non-primitive data structure (비단순구조) : 단순한 데이터를 저장하는 구조가 아니라, 여러 데이터를 목적에 맞게 효과적으로 저장하는 자료 구조   

The primitive type of data structure is a kind of data structure that stores the data of only one type. It includes the predefined data structures such as char, float, int, and double.   

The non-primitive data structures are used to store the collection of elements. This data structure can be further categorized into   

1. <strong><u>Linear data structure (선형구조)</u></strong> 저장되는 자료의 전 후 관계가 1:1    
2. <strong><u>Non-Linear data structure (비선형구조) : 데이터 항목 사의의 관계가 1:n 또는 n:m</u></strong>    

<img width="645" alt="Screen Shot 2022-01-05 at 5 02 15 PM" src="https://user-images.githubusercontent.com/63195670/148181944-02411bc3-b487-492b-b84d-5182e9c75a2e.png">   

</div>


Linear data structure is a type of data structure where the arrangement of the data follows a linear trend. **The data elements are <u>arranged linearly</u> such that the element is directly linked to its previous and the next elements. As the elements are stored linearly, the structure supports <u>single-level storage of data</u>. And hence, <u>traversal of the data is achieved through a single run</u> only**.

## 📌 Characteristics

- It is a type of data structure where data is stored and managed in a linear sequence. 

- Data elements in the sequence are linked to one after the other.

- <u>Implementation</u> of the linear structure of data in a computer’s memory is <u>easy</u> as the **<u>data is organized sequentially</u>**.

- Array, queue. Stack, linked list, etc. are examples of this type of structure.

- The <u>data elements</u> stored in the data structure have **<u>only one relationship</u>**.

- <u>Traversal of the data elements</u> can be carried out in a **<u>single run</u>** as the data elements are stored in a <u>single level</u>.

- There is <u>poor utilization of the computer memory</u> if a structure storing data linearly is implemented.

- With the **<u>increase in the size of the data structure</u>, the <u>time complexity of the structure increases</u>**.

These structures can therefore be summarized as a type of data structure where the elements are stored sequentially and follow the order where:

- Only one first element is present which has one next element.

- Only one last element is present which has one previous element.

- All the other elements in the data structure have a previous and a next element

## 📌 List of data structure in a linear type of data structure

### [1] Array & List

**데이터 갯수가 확실하게 정해져 있고, 자주 사용된다면, 인덱스가 중요하다면 배열**을 사용, **인덱스가 중요하지 않은 경우에는 리스트**를 사용하는 게 좋음! 

#### ✏️ Arrary (배열)

The array is that type of structure that stores homogeneous elements at memory locations **<u>which are contiguous</u>**. The **<u>same types</u> of objects are stored <u>sequentially</u> in an array**.    
The main idea of an array is that **multiple data of the same type can be stored together**.    
Before storing the data in an array, the **<u>size of the array has to be defined</u>**. Any element in the array can be accessed or modified and the elements stored are **<u>indexed</u>** to identify their locations. Simple traversal of the array can lead to the access of the elements.

- 데이터가 많아지면 그룹 관리의 필요성이 생기는데, 이럴 때 프로그래밍에서 사용

- 여러 데이터를 하나의 이름으로 그룹핑해서 관리 하기 위한 자료구조

- 배열을 이용하면 하나의 변수에 여러 정보를 담을 수 있고, 반복문과 결합 하면 많은 정보도 효율적으로 처리할 수 있다.

- 배열 인덱스는 값에 대한 유일무이한 식별자 (참고로 리스트에서 인덱스는 몇 번째 데이터인가 정도의 의미를 가짐)

- 실제 메모리 옆에 저장되므로 순서가 있고, 인덱싱 가능.

- 데이터를 빨리 읽어야 할 때 쓰기 좋으며, 가장 많이 사용됨.

##### 🤦🏻‍♀️ 배열의 특징

- **크기가 정해져 있다** / 기능이 없다 
(이는 배열의 장점이자 단점으로 배열은 다른 자료구조의 좋은 부품으로 사용될 수 있다.)

- **인덱스를 가지며, element의 인덱스는 변경되지 않는다**. 

- 유관 데이터를 메모리에 **순차적으로 나열**할 수 있다.

- 인덱스를 활용하여 **빠르게 조회**가 가능하다.

- **cache hit** (읭..컴구 시간에 나왔던 친구 안뇽 ･_･)  의 가능성이 커져서 **성능**에 큰 도움이 된다.

- 인덱스를 이용하여 데이터를 가져오려면 데이터에 대한 인덱스 값이 고정되어야 하기에, **삭제된 element의 공간이 그대로 남는다. -> <u>메모리의 낭비 초래 가능</u>**

##### 🤦🏻‍♀️ 배열의 한계

- **배열은 길이를 바꿀 수 없다**. 가변 배열과 같이 길이가 변경 가능한 배열의 경우, 
	- 기존의 배열은 그대로 두고,
	- 새로운 길이로 지정된 배열을 따로 할당 후 (메모리가 있는지 탐색 필요)
	- 데이터의 복사를 진행하고, 
	- 기존의 배열을 삭제한다.
	- 총 3번의 작업 + 메모리 탐색 이 필요하기 때문에 리소스 낭비가 크다.

- 위와 같은 한계를 해결하기 위해서 linked list 자료형을 활용할 수 있다. (탐색, 할당, 복사, 삭제 등의 리소스 낭비가 없다.)

- **배열은 인덱스에 따라서 값을 유지하기 때문에, <u>element가 삭제되어도 빈자리(null)가 남게 된다</u>. <u>(불필요한 메모리 차지)</u>**

- 조건문을 통해서 빈 element를 제외할 수 있으나, 조건문을 많이 사용하는 것은 좋지 않다.

#### ✏️ List (리스트)

- 리스트는 배열이 가지고 있는 인덱스라는 장점을 버리고 대신 빈틈없는 데이터의 적재 라는 장점을 취한 Data Structure   

- **삭제한 데이터를 뒤에 위치한 element로 메꾸면, <u>데이터가 순서에 따라서 빈틈없이 연속적으로 위치</u>하며 이를 <u>list(리스트)</u>** 라고 한다.

- 리스트 자료구조의 핵심은 elements 간의 순서. 따라서 리스트를 다른 말로는 시퀀스(sequence) 라고도 부른다. 즉 순서가 있는 데이터의 모임이 리스트이다.   

- 리스트에서 인덱스는 **<u>몇 번째 데이터인가</u>** 정도의 의미를 가진다. (배열-Array에서의 인덱스는 값에 대한 유일무이한 식별자)   

- 빈 element는 허용하지 않는다.   

- 순차성을 보장하지 못하기 때문에 spacial locality 보장이 되지 않아서 cash hit가 어렵다.   

- 리스트에 대한 효용은 어떤 언어를 사용하느냐에 따라서 달라진다. 특히 많은 언어가 리스트를 기본적으로 지원하기 때문에 리스트를 직접 구현하는 경우는 줄고 있다.


##### 🤦🏻‍♀️ list 자료구조의 대표 기능 (operation)

자료구조에서 가장 중요한 점은, **해당 자료구조가 어떠한 <u>기능</u>을 가지고 있느냐는 것**이다.   
List의 대표기능은 다음과 같다 :)

- 처음, 끝, 중간에 엘리먼트를 추가/삭제 하는 기능
- 리스트에 데이터가 있는지를 체크하는 기능
- 리스트의 모든 데이터에 접근할 수 있는 기능

##### 🤦🏻‍♀️ 언어별 list 지원 비교

**_"C"_**

- 리스트를 지원하지 않는다. 대신 배열을 지원한다.   
- 리스트를 사용하려면 직접 만들거나 라이브러리를 사용해야한다. (따라서 리스트에 대한 깊은 이해와 안목이 필요함)


**_"Python"_**

- 기본적으로 리스트를 제공하며, 배열은 제공하지 않는다.
- 파이썬에서는 리스트가 배열이다.
- 파이썬의 리스트는 크기가 가변적이고, 어떤 원소 타입이던 저장할 수 있다는 장점을 가진다. 대신 C의 array 보다 메모리를 더 많이 필요로 한다는 단점이 있다.

```python
numbers = [10, 20, 30, 40, 50]
numbers.pop(3) # 40 / 3번째 인덱스 값 리턴 후 삭제
for number in numbers:
	print(number) # 10, 20, 30, 50
```


**_"Java"_**

- 자바는 배열과 리스트를 모두 지원하고, 두 가지가 완전히 분리되어 있다.
- **배열은 배열의 장점이, 리스트는 리스트의 장점이 있기 때문에 개발자가 원하는대로 직접 선택가능**하다.
- java는 javascript, python에 비해서 자료구조에 대해 더 알아야 할 필요성이 있지만, 그만큼 개발자에게 더 큰 자유도가 주어진다.
- 자바는 2가지 형태의 리스트를 지원한다.
	- LinkedList / ArrayList
	- 똑같은 기능(메소드)를 가진 리스트가 2가지 존재한다.
	- 각각의 장단점이 분명하다.

```java
// 배열 - 추가, 삭제가 어렵다. 직접 구현해야한다.
int[] numbers = {10,20,30,40,50};

// 리스트 (ArrayList)
ArrayList numbers = new ArrayList();

numbers.add(10); // 추가
numbers.remove(0); // 삭제

// 리스트 (LinkedList)
LinkedList numbers = new LinkedList();

numbers.add(10); // 추가
numbers.remove(0); // 삭제
```

<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>Java - ArrayList / LinkedList</u></strong>   

- Java에서는 배열 (array) 이외에 ArrayList와 LinkedList 2종류의 리스트를 제공한다.     

- <strong>인덱스를 이용해서 데이터를 가져오는 것이 빈번하다면 내부적으로 배열을 이용하는 ArrayList가 훨씬 빠르다. 하지만 데이터의 추가/삭제가 빈번하다면 LinkedList가 훨씬 효과적이다.</strong>    

- 이와같이 처리하고자 하는 데이터에 따라서 어떤 데이터 스트럭쳐를 선택할지를 잘 판단하는 것은 대규모 시스템을 구축하는데는 필수적인 능력이다.    

- 이러한 판단을 하기 위해서는 직접 Data structure를 구현해서 사용하지 않더라도 내부적인 메커니즘을 이해할 필요가 있다.    

<img width="634" alt="Screen Shot 2022-01-05 at 5 02 04 PM" src="https://user-images.githubusercontent.com/63195670/148181935-e6b7f444-bc24-49a0-812c-8b1b9d49f54c.png">    

🏹 Array List

Array List는 배열을 이용해서 리스트를 구현한 것을 의미한다.    
- 장점 : 내부적으로 배열을 사용하기 때문에 인덱스를 이용해서 접근하는 것이 빠르다.   
- 단점 : 데이터의 추가와 삭제가 느리다.     

- 데이터의 추가 : Array List는 내부적으로 데이터를 배열에 저장한다. 배열의 특성상 데이터를 리스트의 처음이나 중간에 저장하면, 이후의 데이터들이 한칸씩 뒤로 물러나야한다.    

- 데이터의 삭제 : 삭제도 추가와 유사하게 빈자리가 생기면 빈자리를 채우기 위해서 순차적으로 한칸씩 땡겨야 한다.    

- 데이터 조회(가져오기) : 인덱스를 이용하여 데이터를 가져오고 싶을 때 Array로 구현한 리스트는 속도가 매우 빠르다. (메모리 상의 주소를 정확하게 참고해서 가져오기 때문이다.).   

🏹 Linked List

Linked List는 노드의 연결을 이용해서 리스트를 구현한 것을 의미한다.    
- 장점 : 데이터의 추가와 삭제 속도가 빠르다.   
- 단점 : 인덱스를 이용해서 접근하는 것이 Array List에 비해 상대적으로 느리다.     

- 데이터의 추가 : 추가될 엘리먼트의 이전, 이후 노드의 참조값(next)만 변경하면 되기 때문에 빠르다   

- 데이터의 삭제 : 삭제가 될 엘리먼트의 이전, 이후 노드의 참조값(next)만 변경하면 되기 때문에 빠르다.    

- 데이터 조회(가져오기) : 인덱스를 이용해서 데이터를 조회할 때 linked list는 head가 가리키는 노드부터 시작해서 순차적으로 노드를 찾아가는 과정을 거쳐야 한다. 만약 찾고자 하는 엘리먼트가 가장 끝에 있다면 모든 노드를 탐색해야 하기에 Array List에 비해 느리다.

</div>


### [2] Linked list

Linked List는 Array List와는 다르게 엘리먼트와 엘리먼트 간의 연결(link)을 이용해서 리스트를 구현한 것을 의미한다. Linked list에서 가장 중요한 것은 연결이 무엇인가를 파악하는 것과 또 연결이 아닌 것은 무엇인가를 생각해보는 것이라고 할 수 있음.

<img width="275" alt="Screen Shot 2022-01-05 at 5 30 44 PM" src="https://user-images.githubusercontent.com/63195670/148185621-18d03000-1114-4e52-9699-c4e70e3b3c11.png">

배열과는 다르게 Linked list는 그 위치가 흩어져 있기 때문에 서로 연결되어 있어야 한다. 바로 그런 점에서 연결이라는 이름을 갖게 된 것! 

Array list에서는 element라는 이름을 사용했지만 Linked list와 같이 연결된 엘리먼트들은 노드(node, 마디, 교점의 의미) 혹은 버텍스(vertex, 정점, 꼭지점의 의미)라고 부른다. 연결성이 강조된 표현이라고 생각하면 됨!

The linked list is that type of data structure where separate objects are stored sequentially. Every object stored in the data structure will have the data and a reference to the next object. The last node of the linked list has a reference to null. The first element of the linked list is known as the head of the list. There are many differences between a linked list to the other types of data structures. These are in terms of memory allocation, the internal structure of the data structure, and the operations carried on the linked list. 

Getting to an element in a linked list is a slower process compared to the arrays as the indexing in an array helps in locating the element. However, in the case of a linked list, the process has to start from the head and traverse through the whole structure until the desired element is reached. In contrast to this, the advantage of using linked lists is that the addition or deletion of elements at the beginning can be done very quickly. 

There are three types of linked lists:

#### ✏️ Single Linked List

This type of structure has the address or the reference of the next node stored in the current node. Therefore, a node which at the last has the address and reference as a NULL. 

<img width="651" alt="Screen Shot 2022-01-05 at 5 33 45 PM" src="https://user-images.githubusercontent.com/63195670/148185957-500d1c23-d225-45b1-8044-659328d28f05.png">

##### 👀 Example
A->B->C->D->E->NULL

#### ✏️ A Double Linked List

As the name suggests, each node has two references associated with it. One reference directs to the previous node while the second reference points to the next node. Traversal is possible in both directions as reference is available for the previous nodes. Also, explicit access is not required for deletion. 

##### 👀 Example
NULL<-A<->B<->C<->D<->E->NULL

#### ✏️ Linked List which is circular

The nodes in a circular linked list are connected in a way that a circle is formed. As the linked list is circular there is no end and hence no NULL. This type of linked list can follow the structure of both singly or doubly. There is no specific starting node and any node from the data can be the starting node. The reference of the last node points towards the first node. 

##### 👀 Example
A->B->C->D->E

#### ✏️ Properties of a linked list

- Access time: O(n) 
- Searching time: O(n)
- Adding element: O(1) 
- Deleting  an Element : O(1) 

### [3] Stack
The stack is another type of structure where the elements stored in the data structure follow the rule of LIFO (last in, first out) or FILO (First In Last Out). Two types of operations are associated with a stack i.e. push and pop. Push is used when an element has to be added to the collection and pop is used when the last element has to be removed from the collection. Extraction can be carried out for only the last added element.

#### ✏️ Properties of a stack are:

- Adding element: O(1)
- deleting element:  O(1)
- Accessing Time: O(n) [Worst Case]

Only one end allows inserting and deleting an element.
Examples of the stack include the removal of recursion. In scenarios where a word has to be reversed, or while using editors when the word that was last typed will be removed first (using an undo operation), stacks are used. 

### [4] Queue
Queue is the type of data structure where the elements to be stored follow the rule of First In First Out (FIFO). The particular order is followed for performing the required operations over the elements. The difference of a queue from that of a stack lies in the removal of an element, where the most recently added object is removed first in a stack. Whereas, in the case of a queue, the element that was added first is removed first.

Both the end of the data structure is used for the insertion and the removal of data. The two main operations governing the structure of the queue are enqueue, and dequeue. Enqueue refers to the process where inserting an element is allowed to the collection of data and dequeue refers to the process where removal of elements is allowed, which is the first element in the queue in this case.

#### ✏️ Properties of a queue are

- Inserting an element: O(1)
- Deleting an element: O(1)
- Accessing Time: O(n)

Example of the queue: Similar to those queues made while waiting for the bus or anywhere, the data structure too follows the same pattern. We can imagine a person waiting for the bus and standing at the first position as the person that came to the queue first. This person will be the first one who will get onto a bus, i.e. exit the queue. Queues are applied when multiple users are sharing the same resources and they have to be served on the basis of who has come first on the server. 


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

<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>In what ways are linked lists more efficient than arrays?</u></strong>   

The following points elaborate the ways in which linked lists are much more efficient than arrays:   

🏹 <strong><u>Dynamic Memory allocation</u></strong>   
The memory of a linked list is dynamically located which means that there is no need to initialize the size and it can be expanded as well as shrink anytime without implying any exterior operation.   
On the other hand, arrays are statically allocated and the size has to be initialized. Once created, the size cannot be altered.   

🏹 <strong><u>Insertion and Deletion</u></strong>    
Since a linked list is dynamically created, operations like insertion and deletion are much more convenient.   

🏹 <strong><u>No memory wastage</u></strong>    
There is no memory wastage in a linked list as all the elements are dynamically inserted. And after the deletion of an element, we can free its memory.    
</div>

<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>What are the most common operations performed in linear data structures?</u></strong>   

The common possible operations that can be performed in all linear data structures include traversing, insertion, deletion, modification, search operation, and sort operation.    
These operations are recognized by different names in different data structures. For example, the insertion and deletion operations are known as Push and Pop operations in Stack, whereas they are referred to as enqueue and dequeue operations in Queue.     
There can be some other operations as well such as merging and the empty operation to check if the data structure is empty or not.    
</div>
	
	
### 🔗 출처	
* [Data Structure 참고 사이트] (https://velog.io/@k904808/Data-Structure자료구조)
* [배열과 리스트 참고 사이트 1](https://wayhome25.github.io/cs/2017/04/17/cs-18-1/)     
* [배열과 리스트 참고 사이트 2](https://opentutorials.org/module/1335/8636)
* [Linear Data Structure 참고 사이트] (https://www.upgrad.com/blog/what-is-linear-data-structure/)
* [링크드 리스트 참고 사이트] (https://opentutorials.org/module/1335/8821)
