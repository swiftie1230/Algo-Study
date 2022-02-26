앞으로 10주 동안(그리고 쭉..생각하고 있음) 알고리즘 중급 스터디에 참여하게 되었는데, 여기에 각 주차 강의를 듣고 배운 내용을 정리해 보려고 한다.    
일단 1주차! 아니 2주차라고 해야 하나 🤔   


HashTable에 대해 배웠는데, 1주차에는 간략하게 개념에 대해 배웠다면, 이번 주차에는 직접 문제를 풀어주시며 실제 면접 상황과 관련된 소소한 꿀팁까지 언급해 주셨다.     

총 두문제를 풀어보았는데, 그 중 첫번째는 다음과 같다.     

# 📝 First Problem

```python
/*    
Given an integer array  nums, return  true if any value appears at least twice in the array, and return false if every element is distinct.
*/     
```

일단 input은 integer array, output은 boolean값이다.     
각종 constraints와 edge case도 있지만, 여기서는 생략하겠다.      
(앞으로 1:1 인터뷰 세션을 진행한 후, 문제 풀이들에는 하나하나 적어둘 예정..!)    

일단 brute force(slow solution)로 해결해 본다면, O(N^2)의 시간복잡도를 가지게 된다.    하나하나의 element가 array에 있는지 없는지를 확인하는 거겠지.    

그럼 이제 hashTable(Map)을 이용한 해결책을 생각해보자.    
간단하게 생각헤보면 dictionary(파이쎤)에 각 숫자가 나타나면 저장, 두 번 나타나면 true를 return, 아니면 false를 리턴하면 됨!  

brute force와 optimal 방법을 이용한 두가지 코드 모두 아래에 적어 보았다.          

```python
class Solution2:
    # Brute Force
    def findDuplicate(self, nums):
        # edge case [], [1]
        if len(nums) <= 1:
            return False

        for i in range(len(nums)-1):
            for j in range(i+1, len(nums)):
                if nums[i] == nums[j]:
                    return True
        return False

    # Using HashTable
    def findDuplicate2(self, nums):
        # edge case [], [1]
        if len(nums) <= 1:
            return False
        
        hashMap = {}

        for i in range(len(nums)):
            if nums[i] in hashMap:
                return True
            hashMap[nums[i]] = True
        
        return False
```

두번째는 다음과 같다.    

# 📝 Second Problem

```python
/*    
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
*/     
```

일단 input은 str array, output 역시 str array값이다.     

constraints로는 다음과 같이 명시되어 있었음.    
- arr possibly empty     
- 1 <= strs.length <= 104      
- 0 <= strs[i].length <= 100       

edge cases는 아래와 같다.    
- “a-z”  +, ,-.,~(X) --> question, 26 chars
- [“”], [‘’]

일단 brute force(slow solution)로 해결해 본다면, O(N^2)의 시간복잡도(double for loop => O(N^2 * (2*M)) 여기서 M은 maximum string size), O(N)의 공간 복잡도를 가지게 된다.    

그럼 이제 hashTable(Map)을 이용한 해결책을 생각해보자.     
anagram인지 비교하기 위해서는 1. length 비교 2. 정렬을 이용해 동일한지 확인 총 두가지 과정을 거치면 되겠지!     

time complexity는 O(N * (MlogM)), space complexity: O(N)이다. 
time complexity가 위와 같은 이유는 간단하다. 정렬에 필요한 시간복잡도 * 총 element 개수.    
space complexity가 O(N)인 이유는 어차피 알파벳 개수는 최대 26개이므로 element 개수에 비례할 수밖에 없기 때문!     


optimal 방법을 이용한 코드는 아래와 같다.          

```python
class Solution3:
    # Using HashTable
    def findAllAnagram(self, strArr):
        
        hashMap = {}

        for i in range(len(strArr)):
            currentStr = strArr[i]
            anagram = list(currentStr)
            anagram.sort()
            anagram = ''.join(anagram)
            # time Complexity = O(2*M + MlogM)
            if anagram in hashMap:
                hashMap[anagram].append(currentStr)
            else:
                hashMap[anagram] = [currentStr]

        result = []

        # time Complexity = O(N)
        for key, val in hashMap.items():
            result.append(val)

        return result
```

<div class="notice--primary" markdown="1">
🌝 <strong><u>여기서 잠깐!</u> : <u>다시 보며 헷갈렸거나 새로웠던 내용</u></strong>        

 1. <strong>만약 문자열을 한 글자씩 나눠 저장하고 싶다</strong>면 간단히 <strong>list로 Casting</strong> 하기만 하면 된다.        
 2. sort()는 기존 list 정렬, sorted(list이름)는 새로운 list 만들어서 정렬한 것 저장
 3. for key, val in hashMap.items(): 
 4. append()와 + 

</div>
