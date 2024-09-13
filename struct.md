
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


