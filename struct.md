
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
