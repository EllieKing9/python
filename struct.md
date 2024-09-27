
```
파이선의 배열에는 실제 메모리 공간 주소인 레퍼런스 값을 가지고 있다.
```

배열
```
정적 배열
동적 배열
```

동적 배열 내
```
append operation (확장 연산)
O(1)~O(n)

amortized analysis (분할 상환 분석)
O(X/n)

n번의 새로운 데이터 저장 O(n)
n번의 데이터 복사 이동, m개의 마지막에 옮긴 데이터
n과 m의 관계는 2m-1, 2m-1 < 2n, = O(2n)

O(n + 2n) = O(3n) = O(n)
1번의 연산 O(n)/n = O(1)

insert operation (삽입 연산)
O(n)
```

링크드 리스트
```
class Node:
  def __init__(self, data):
    self.data = data
    self.next = None

# 데이터 2, 3, 5, 7, 11 을 가지는 노드들 생성
head_node = Node(2)
node_1 = Node(3)
node_2 = Node(5)
node_3 = Node(7)
tail_node = Node(11)

head_node.next = node_1
node_1.next = node_2
node_2.next = node_3
node_3.next = tail_node

#노드들 출력
iterator = head_node
while iterator is not None:
  print(iterator.data)
  iterator = iterator.next
```
```
clase linkedList:
  def __init__(self):
    self.head = None
    self.tail = None

  def append(self, data):
    new_node = Node(data)
    if self.head is None:
      self.head = new_node
      self.tail = new_node
    else:
      self.tail.next = new_node
      self.tail = new_node

my_list = linkedList()

my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)
my_list.append(11)

iterator = my_list.head
while iterator is not None:
  print(iterator.data)
  iterator = iterator.next
```

```
class Node:
    def __init__ (self, data):
        self.data = data
        self.next = None
        
class LinkedList:
    def __init__ (self):
        self.head = None
        self.tail = None
        
    def append (self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
            
    def __str__ (self):
        res_str = "|"
        
        iterator = self.head
        while iterator is not None:
            res_str += f" {iterator.data} |"
            iterator = iterator.next
            
        return res_str
            
my_list = LinkedList()
my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)
my_list.append(11)
print(my_list)
```

링크드 리스트 탐색
```
class Node:
    def __init__ (self, data):
        self.data = data
        self.next = None
        self.id = -1
        
class LinkedList:
    def __init__ (self):
        self.head = None
        self.tail = None
        self.index = -1
        
    def find_node_at (self, index):
        iterator = self.head
        
        for _ in range(index):
            iterator = iterator.next
        
        return iterator
        
    def append (self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
            
        self.index += 1
        self.tail.id = self.index
            
    def __str__ (self):
        res_str = "|"
        
        iterator = self.head
        while iterator is not None:
            # res_str += f" {iterator.data} |"
            res_str += f" {iterator.data}"
            res_str += f"({iterator.id}) |"
            iterator = iterator.next
            
        return res_str
            
my_list = LinkedList()
my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)
my_list.append(11)
print(my_list)

print(my_list.find_node_at(3).data)
```

```
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, data):
        self.data = data  # 실제 노드가 저장하는 데이터
        self.next = None  # 다음 노드에 대한 레퍼런스

class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
        self.head = None  # 링크드 리스트의 가장 앞 노드
        self.tail = None  # 링크드 리스트의 가장 뒤 노드

    def find_node_with_data(self, data):
        """링크드 리스트에서 탐색 연산 메소드. 단, 해당 노드가 없으면 None을 리턴한다"""
        # 여기에 코드를 작성하세요
        iterator = self.head
        while iterator is not None:
            if iterator.data is data:
                return iterator
            else:
                iterator = iterator.next

    def append(self, data):
        """링크드 리스트 추가 연산 메소드"""
        new_node = Node(data)
        
        # 링크드 리스트가 비어 있으면 새로운 노드가 링크드 리스트의 처음이자 마지막 노드다
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        # 링크드 리스트가 비어 있지 않으면
        else:
            self.tail.next = new_node  # 가장 마지막 노드 뒤에 새로운 노드를 추가하고
            self.tail = new_node  # 마지막 노드를 추가한 노드로 바꿔준다

    def __str__(self):
        """링크드  리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = "|"

        # 링크드  리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드  리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += " {} |".format(iterator.data)
            iterator = iterator.next # 다음 노드로 넘어간다

        return res_str
    
    

# 새로운 링크드 리스트 생성
linked_list = LinkedList()

# 여러 데이터를 링크드 리스트 마지막에 추가
linked_list.append(2)
linked_list.append(3)
linked_list.append(5)
linked_list.append(7)
linked_list.append(11)

# print(linked_list)

# 데이터 2를 갖는 노드 탐색
node_with_2 = linked_list.find_node_with_data(2)

if not node_with_2 is None:
    print(node_with_2.data)
else:
    print("2를 갖는 노드는 없습니다")

# 데이터 11을 갖는 노드 탐색
node_with_11 = linked_list.find_node_with_data(11)

if not node_with_11 is None:
    print(node_with_11.data)
else:
    print("11을 갖는 노드는 없습니다")

# 데이터 6 갖는 노드 탐색
node_with_6 = linked_list.find_node_with_data(6)

if not node_with_6 is None:
    print(node_with_6.data)
else:
    print("6을 갖는 노드는 없습니다")
```

링크드 리스트 삽입
```
class Node:
    def __init__ (self, data):
        self.data = data
        self.next = None
        self.id = -1
        
class LinkedList:
    def __init__ (self):
        self.head = None
        self.tail = None
        self.index = -1
        
    def find_node_at (self, index):
        iterator = self.head
        
        for _ in range(index):
            iterator = iterator.next
        
        return iterator
        
    def append (self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
            
        self.index += 1
        self.tail.id = self.index
    
    def insert_after (self, previous_node, data):
        new_node = Node(data)
    
        if previous_node is self.tail:
            self.tail.next = new_node
            self.tail = new_node
        else:
            new_node.next = previous_node.next
            previous_node.next = new_node
            
        self.index = -1
        
        iterator = self.head
        while iterator is not None:
            self.index += 1
            iterator.id = self.index 
            iterator = iterator.next
            
    def __str__ (self):
        res_str = "|"
        
        iterator = self.head
        while iterator is not None:
            # res_str += f" {iterator.data} |"
            res_str += f" {iterator.data}"
            res_str += f"({iterator.id}) |"
            iterator = iterator.next
            
        return res_str

my_list = LinkedList()
my_list.append(2)
my_list.append(3)
my_list.append(5)
my_list.append(7)

print(my_list)

previous_node = my_list.find_node_at(2)
my_list.insert_after(previous_node, 9)

print(my_list)
```

해시 테이블
```
key - value 데이터
- direct access table
- 해시테이블, 해시함수, 충돌과 chaining
-- 탐색 O(1+1+n), 삽입 O(1+1+n+1), 삭제 O(1+1+n+1)
```

```
class Node:
    """링크드 리스트의 노드 클래스"""
    def __init__(self, key, value):
        self.key = key
        self.value = value
        self.next = None  # 다음 노드에 대한 레퍼런스
        self.prev = None  # 전 노드에 대한 레퍼런스


class LinkedList:
    """링크드 리스트 클래스"""
    def __init__(self):
        self.head = None  # 링크드 리스트의 가장 앞 노드
        self.tail = None  # 링크드 리스트의 가장 뒤 노드
        

    def find_node_with_key(self, key):
        """링크드 리스트에서 주어진 데이터를 갖고있는 노드를 리턴한다. 단, 해당 노드가 없으면 None을 리턴한다"""
        iterator = self.head   # 링크드 리스트를 돌기 위해 필요한 노드 변수

        while iterator is not None:
            if iterator.key == key:
                return iterator

            iterator = iterator.next

        return None


    def append(self, key, value):
        """링크드 리스트 추가 연산 메소드"""
        new_node = Node(key, value)

        # 빈 링크드 리스트라면 head와 tail을 새로 만든 노드로 지정
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        # 이미 노드가 있으면
        else:
            self.tail.next = new_node  # 마지막 노드의 다음 노드로 추가
            new_node.prev = self.tail
            self.tail = new_node  # 마지막 노드 업데이


    def delete(self, node_to_delete):
        """더블리 링크드 리스트 삭제 연산 메소드"""

        # 링크드 리스트에서 마지막 남은 데이터를 삭제할 때
        if node_to_delete is self.head and node_to_delete is self.tail:
            self.tail = None
            self.head = None

        # 링크드 리스트 가장 앞 데이터 삭제할 때
        elif node_to_delete is self.head:
            self.head = self.head.next
            self.head.prev = None

        # 링크드 리스트 가장 뒤 데이터 삭제할 떄
        elif node_to_delete is self.tail:
            self.tail = self.tail.prev
            self.tail.next = None

        # 두 노드 사이에 있는 데이터 삭제할 때
        else:
            node_to_delete.prev.next = node_to_delete.next
            node_to_delete.next.prev = node_to_delete.prev

        return node_to_delete.value


    def __str__(self):
        """링크드 리스트를 문자열로 표현해서 리턴하는 메소드"""
        res_str = ""

        # 링크드 리스트 안에 모든 노드를 돌기 위한 변수. 일단 가장 앞 노드로 정의한다.
        iterator = self.head

        # 링크드 리스트 끝까지 돈다
        while iterator is not None:
            # 각 노드의 데이터를 리턴하는 문자열에 더해준다
            res_str += "{}: {}\n".format(iterator.key, iterator.value)
            iterator = iterator.next  # 다음 노드로 넘어간다

        return res_str
```
```
from HDLL import LinkedList  # 해시 테이블에서 사용할 링크드 리스트 임포트

class HashTable:
    """해시 테이블 클래스"""
    
    def __init__(self, capacity):
        self._capacity = capacity  # 파이썬 리스트 수용 크기 저장
        self._table = [LinkedList() for _ in range(self._capacity)]  # 파이썬 리스트 인덱스에 반 링크드 리스트 저장

    def _hash_function(self, key):
        """
        주어진 key에 나누기 방법을 사용해서 해시된 값을 리턴하는 메소드
        주의: key는 파이썬 불변 타입이여야 한다.
        """
        return hash(key) % self._capacity


    def look_up_value(self, key):
        """
        주어진 key에 해당하는 데이터를 리턴하는 메소드
        """
        # 코드를 쓰세요
        index = self._hash_function(key)
        iterator = self._table[index].find_node_with_key(key)
        return iterator.value
        
    def insert(self, key, value):
        """
        새로운 key - value 쌍을 삽입시켜주는 메소드
        이미 해당 key에 저장된 데이터가 있으면 해당 key에 해당하는 데이터를 바꿔준다
        """
        # 코드를 쓰세요
        index = self._hash_function(key)
        iterator = self._table[index].find_node_with_key(key)
        if iterator is not None:
            iterator.value = value
        else:
            self._table[index].append(key, value)

            
    def __str__(self):
        """해시 테이블 문자열 메소드"""
        res_str = ""

        for linked_list in self._table:
            res_str += str(linked_list)

        return res_str[:-1]

    
 
test_scores = HashTable(50)  # 시험 점수를 담을 해시 테이블 인스턴스 생성

# 여러 학생들 이름과 시험 점수 삽입
test_scores.insert("현승", 85)
test_scores.insert("영훈", 90)
test_scores.insert("동욱", 87)
test_scores.insert("지웅", 99)
test_scores.insert("신의", 88)
test_scores.insert("규식", 97)
test_scores.insert("태호", 90)

print(test_scores)

# key인 이름으로 특정 학생 시험 점수 검색
print(test_scores.look_up_value("현승"))
print(test_scores.look_up_value("태호"))
print(test_scores.look_up_value("영훈"))

# 학생들 시험 점수 수정
test_scores.insert("현승", 10)
test_scores.insert("태호", 20)
test_scores.insert("영훈", 30)

print(test_scores)
```

```
from HDLL import LinkedList  # 해시 테이블에서 사용할 링크드 리스트 임포트

class HashTable:
    def __init__(self, capacity):
        self._capacity = capacity  # 파이썬 리스트 수용 크기 저장
        self._table = [LinkedList() for _ in range(self._capacity)]  # 파이썬 리스트 인덱스에 반 링크드 리스트 저장

    def _hash_function(self, key):
        """
        주어진 key에 나누기 방법을 사용해서 해시된 값을 리턴하는 메소드
        주의: key는 파이썬 불변 타입이여야 한다.
        """
        return hash(key) % self._capacity


    def _get_linked_list_for_key(self, key):
        """주어진 key에 대응하는 인덱스에 저장된 링크드 리스트를 리턴하는 메소드"""
        hashed_index = self._hash_function(key)

        return self._table[hashed_index]


    def _look_up_node(self, key):
        """파라미터로 받은 key를 갖고 있는 노드를 리턴하는 메소드"""
        linked_list = self._get_linked_list_for_key(key)
        return linked_list.find_node_with_key(key)


    def look_up_value(self, key):
        """
        주어진 key에 해당하는 데이터를 리턴하는 메소드
        """
        return self._look_up_node(key).value


    def insert(self, key, value):
        """
        새로운 key - value 쌍을 삽입시켜주는 메소드
        이미 해당 key에 저장된 데이터가 있으면 해당 key에 해당하는 데이터를 바꿔준다
        """
        existing_node = self._look_up_node(key)  # 이미 저장된 key인지 확인한다

        if existing_node is not None:
            existing_node.value = value  # 이미 저장된 key면 데이터만 바꿔주고
        else:
            # 없는 key면 링크드 리스트에 새롭게 삽입시켜준다
            linked_list = self._get_linked_list_for_key(key)
            linked_list.append(key, value)

    def delete_by_key(self, key):
        """주어진 key에 해당하는 key - value 쌍을 삭제하는 메소드"""
        # 코드를 쓰세요
        node = self._look_up_node(key)
        if node is not None:
            # linked_list = self._get_linked_list_for_key(key)
            # linked_list.delete(node)
            self._get_linked_list_for_key(key).delete(node)

        return

    def __str__(self):
        """해시 테이블 문자열 메소드"""
        res_str = ""

        for linked_list in self._table:
            res_str += str(linked_list)

        return res_str[:-1]
    
 

test_scores = HashTable(50) # 시험 점수를 담을 해시 테이블 인스턴스 생성

# 여러 학생들 이름과 시험 점수 삽입
test_scores.insert("현승", 85)
test_scores.insert("영훈", 90)
test_scores.insert("동욱", 87)
test_scores.insert("지웅", 99)
test_scores.insert("신의", 88)
test_scores.insert("규식", 97)
test_scores.insert("태호", 90)

# 학생들 시험 점수 삭제
test_scores.delete_by_key("태호")
test_scores.delete_by_key("지웅")
test_scores.delete_by_key("신의")
test_scores.delete_by_key("현승")
test_scores.delete_by_key("규식")

print(test_scores)
```

OPen Addressing
```

```

추상 자료형
```
리스트
trending = []
trending.insert(0, "연애인 A씨")
print(trending)
trending[0] = "누구"
print(trending)
print("연애인 A씨" in trending)
del trending[0]
print(trending)

큐 (FIFO)
from collections import deque
queue = deque()
queue.append("태호")
queue.append("현승")
queue.append("두광")
print(queue)
print("2번쨰 자료: " + queue[2])
print(queue.popleft())
print(queue)


from collections import deque

class CustomerComplaint:
    """고객 센터 문의를 나타내는 클래스"""
    def __init__(self, name, email, content):
        self.name = name
        self.email = email
        self.content = content

        
class CustomerServiceCenter:
    """고조선 호텔 서비스 센터 클래스"""
    def __init__(self):
        self.queue = deque()  # 대기 중인 문의를 저장할 큐 생성

        
    def process_complaint(self):
        """접수된 고객 센터 문의 내용 처리하는 메소드"""
        # 여기에 코드를 작성하세요
        if not self.queue:
            print("더 이상 대기 중인 문의가 없습니다!")
        else:
            complaint = self.queue.popleft()
            print("{}님의 {} 문의 내용 접수 되었습니다. 담당자가 배정되면 {}로 연락드리겠습니다!".format(complaint.name, complaint.content, complaint.email))

    def add_complaint(self, name, email, content):
        """새로운 문의를 큐에 추가 시켜주는 메소드"""
        # 여기에 코드를 작성하세요
        complaint = CustomerComplaint(name, email, content)
        self.queue.append(complaint)


# 고객 문의 센터 인스턴스 생성
center = CustomerServiceCenter()

# 문의 접수한다
center.add_complaint("강영훈", "younghoon@codeit.com", "음식이 너무 맛이 없어요")

# 문의를 처리한다
center.process_complaint()
center.process_complaint()

# 문의 세 개를 더 접수한다
center.add_complaint("이윤수", "yoonsoo@codeit.kr", "에어컨이 안 들어와요...")
center.add_complaint("손동욱", "dongwook@codeit.us", "결제가 제대로 안 되는 거 같군요")
center.add_complaint("김현승", "hyunseung@codeit.ca", "방을 교체해주세요")

# 문의를 처리한다
center.process_complaint()
center.process_complaint()
```
```
스택 (LIFO)
from collections import deque

def parentheses_checker(string):
    """주어진 문자열 인풋의 모든 괄호가 짝이 있는지 확인해주는 메소드"""


    print(f"테스트하는 문자열: {string}")
    stack = deque() # 사용할 스택 정의

    for i in range(len(string)):
        if string[i] == "(":
            stack.append(i)
        elif string[i] == ")":
            if stack:
                stack.pop()
            else:
                print(f"문자열 {i} 번째 위치에 있는 닫는 괄호에 맞는 열리는 괄호가 없습니다")
                
    while stack:        
        print(f"문자열 {stack.pop()} 번째 위치에 있는 괄호가 닫히지 않았습니다")

case1 = "(1+2)*(3+5)"
case2 = "((3*12)/(41-31))"
case3 = "((1+4)-(3*12)/3"
case4 = "(12-3)*(56/3))"
case5 = ")1+14)/3"
case6 = "(3+15(*3"

parentheses_checker(case1)
parentheses_checker(case2)
parentheses_checker(case3)
parentheses_checker(case4)
parentheses_checker(case5)
parentheses_checker(case6)
```
```
딕셔너리(Dictionary)
key - value 데이터 쌍

grades = {}
grades["현승"] = 80
grades["태호"] = 60
print(grades)
print(grades["태호"])
grades.pop("태호")
print(grades)
```
```
세트
classes = set()

classes.add("자료구조")
classes.add("알고리즘")
print(classes)
print("컴퓨터개론" in classes)
print("자료구조" in classes)
classes.remove("알고리즘")
print(classes)
```

```
리스트 (동적 배열)
연산	예시	시간 복잡도
접근	list_1[0], list_1[0] = 5	O(1)
추가	list_1.append(2) O(1)(분할 상환)
맨 뒤 삭제	list_1.pop() O(1)(분할 상환)
길이 확인	len(list_1)	O(1)
삽입	list_1.insert(3, "성태호")	O(n)
삭제	del list_1[0], list_1.pop(3)	O(n)
탐색	"이재하" in list_1	O(n)

deque (더블리 링크드 리스트)
연산	예시	시간 복잡도
맨 앞 삭제	deque_1.popleft()	O(1)
맨 앞 삽입	deque_1.appendleft("김신의")	O(1)
맨 뒤 삭제	deque_1.pop()	O(1)
맨 뒤 삽입	deque_1.append("이규식")	O(1)
길이 확인	len(deque_1)	O(1)

딕셔너리 (해시 테이블)
연산	예시	시간 복잡도
탐색	dict_1["성태호"]	O(1)(평균)
삽입	dict_1["강영훈"] = 100	O(1)(평균)
삭제	del dict_1["강영훈"], dict_1.pop("강영훈")	O(1)(평균)
길이 확인	len(dict_1)	O(1)

세트 (해시 테이블)
연산	예시	시간 복잡도
탐색	"최지웅" in set_1	O(1)(평균)
삽입	set_1.add("손동욱")	O(1)(평균)
삭제	set_1.remove("김현승"), set_1.pop("김현승")	O(1)(평균)
길이 확인	len(set_1)	O(1)
```

이진트리
```
class Node:
    def __init__ (self, data):
        self.data = data
        self.left_child = None
        self.right_child = None
        
root_node = Node(2)
node_B = Node(3)
node_C = Node(5)
node_D = Node(7)
node_E = Node(11)

root_node.left_child = node_B
root_node.right_child = node_C

node_B.left_child = node_D
node_B.right_child = node_E

print(root_node.left_child.data)

def get_parent_index(complete_binary_tree, index):
    """배열로 구현한 완전 이진 트리에서 index번째 노드의 부모 노드의 인덱스를 리턴하는 함수"""
    # 여기에 코드를 작성하세요
    # index = int(index / 2)
    index = index // 2
    # if index > 0 and index < len(complete_binary_tree):
    if 0 < index < len(complete_binary_tree):    
        return index
    else:
        return None

def get_left_child_index(complete_binary_tree, index):
    """배열로 구현한 완전 이진 트리에서 index번째 노드의 왼쪽 자식 노드의 인덱스를 리턴하는 함수"""
    # 여기에 코드를 작성하세요
    index = index * 2 
    if index > 0 and index < len(complete_binary_tree):
        return index
    else:
        return None

def get_right_child_index(complete_binary_tree, index):
    """배열로 구현한 완전 이진 트리에서 index번째 노드의 오른쪽 자식 노드의 인덱스를 리턴하는 함수"""
    # 여기에 코드를 작성하세요
    index = (index * 2) + 1
    if index > 0 and index < len(complete_binary_tree):
        return index
    else:
        return None

# 테스트 코드
root_node_index = 1 # root 노드

tree = [None, 1, 5, 12, 11, 9, 10, 14, 2, 10]  # 과제 이미지에 있는 완전 이진 트리

# root 노드의 왼쪽과 오른쪽 자식 노드의 인덱스를 받아온다
left_child_index = get_left_child_index(tree, root_node_index)
right_child_index = get_right_child_index(tree,root_node_index)

print(tree[left_child_index])
print(tree[right_child_index])

# 9번째 노드의 부모 노드의 인덱스를 받아온다
parent_index = get_parent_index(tree, 9)

print(tree[parent_index])

# 부모나 자식 노드들이 없는 경우들
parent_index = get_parent_index(tree, 1)  # root 노드의 부모 노드의 인덱스를 받아온다
print(parent_index)

left_child_index = get_left_child_index(tree, 6)  # 6번째 노드의 왼쪽 자식 노드의 인덱스를 받아온다
print(left_child_index)

right_child_index = get_right_child_index(tree, 8)  # 8번째 노드의 오른쪽 자식 노드의 인덱스를 받아온다
print(right_child_index)
```

트리 순회
```

```





