# mergeSort

1. 재귀를 통해 요소값이 하나인 두 배열부터 오름차순으로 정렬하며 병합해간다. 
2. 따라서 병합할 두 배열은 항상 오름차순 정렬되어 있다고 가정할 수 있다.
2. 병합 방식은 두 배열의 왼쪽값부터 차례로 비교해 가며 버퍼에 오름차순으로 정렬한다. 


```python
import sys

N = int(sys.stdin.readline())

numbers = []
buff = [0 for i in range(N)]

for _ in range(N):
    numbers.append(int(sys.stdin.readline()))

def mergeSort(arr, left, right):
    idx = left
    center = (left + right) // 2
    x = left
    y = center+1

    if(left < right):

        mergeSort(arr, left, center)
        mergeSort(arr, center+1, right)

        while x <= center and y <= right:
            if arr[x] <= arr[y]:
                buff[idx] = arr[x]
                x += 1
            else:
                buff[idx] = arr[y]
                y += 1
            idx += 1
        
        buff[idx:right+1] = arr[x:center+1] if x <= center else arr[y:right+1]
        arr[left:right+1] = buff[left:right+1]

mergeSort(numbers, 0 , N-1)

for num in numbers:
    print(num)
```
