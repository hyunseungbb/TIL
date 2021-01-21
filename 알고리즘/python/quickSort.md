# 퀵정렬

### Partition
- 피벗을 정한다(배열의 중앙값으로 한다)
- 피벗 왼쪽에서 피벗보다 큰 값을 찾는 커서 pl을 설정한다.
- 피벗 오른쪽에서 피벗보다 작은 값을 찾는 커서 pr을 설정한다.
- 피벗보다 큰 값을 찾을 때까지 pl을 오른쪽으로 스캔한다.
- 피벗보다 작은 값을 찾을 때까지 pr을 왼쪽으로 스캔한다.
- 양쪽에서 타켓을 찾았다면 두 값을 교환한다.
- 교환한 지점부터 위의 방법으로 스캔 및 교환을 반복한다.
- pl과 pr이 교차하면 종료\

### quicksort
그룹의 요소수가 1개가 될 때까지 반복해서 파티션하는 것이 퀵정렬이다.


```python
import sys

N = int(sys.stdin.readline())

number = []

for _ in range(N):
    number.append(int(sys.stdin.readline()))    

def quickSort(array, left, right):
    pl = left
    pr = right
    pivot = array[int((left+right)/2)]
    
    while pl <= pr:
        while array[pl] < pivot:
            pl = pl + 1
        while array[pr] > pivot: 
            pr = pr - 1
        if pl <= pr:
            array[pl], array[pr] = array[pr], array[pl]
            pl = pl + 1
            pr = pr - 1
            
    if left < pr:
        quickSort(array, left, pr)
    if right > pl:
        quickSort(array, pl, right)
        
quickSort(number, 0, N-1)

for i in number:
    print(i)
```
