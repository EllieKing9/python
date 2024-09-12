
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
