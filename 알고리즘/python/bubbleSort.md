## bubbleSort

- 인접한 두 요소값을 비교해나가는 정렬 방식으로, O($n^2$)의 시간복잡도를 가진다.


```python
N = int(input())

numbers = []

for _ in range(N) :
    numbers.append(int(input()))

for i in range(len(numbers)) :
    for j in range(len(numbers)):
        if numbers[i] < numbers[j]:
            numbers[i], numbers[j] = numbers[j], numbers[i]
            
for n in numbers :
    print(n)
```
