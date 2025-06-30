# [15649 N과 M (1)](https://www.acmicpc.net/problem/15649)

기본 문제

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(1, n + 1):
        if i not in arr:
            arr.append(i)
            dfs()
            arr.pop()

n, m = map(int, input().split())
arr = []
dfs()
```

# [15650 N과 M (2)](https://www.acmicpc.net/problem/15650)

len(arr)이 0이면 통과  
아니면 i가 마지막 숫자보단 커야함  
그래야 오름차순을 만족할 수 있음

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(1, n + 1):
        if i not in arr and (len(arr) == 0 or i > arr[-1]):
            arr.append(i)
            dfs()
            arr.pop()

n, m = map(int, input().split())
arr = []
dfs()
```

# [15651 N과 M (3)](https://www.acmicpc.net/problem/15651)

같은 수를 골라도 된다는 건 if i not in arr 구문을 빼도 된다는 것

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(1, n + 1):
        arr.append(i)
        dfs()
        arr.pop()

n, m = map(int, input().split())
arr = []
dfs()
```

# [15651 N과 M (4)](https://www.acmicpc.net/problem/15652)

같은 수를 여러 번 골라도 되기에 if i not in arr은 필요 없지만  
비내림차순이어야하기 때문에 len(arr) == 0 or i >= arr[-1]이 필요하다  
15650번과 다른 점은 >= 이라는 것

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(1, n + 1):
        if len(arr) == 0 or i >= arr[-1]:
            arr.append(i)
            dfs()
            arr.pop()

n, m = map(int, input().split())
arr = []
dfs()
```

# [15654 N과 M (5)](https://www.acmicpc.net/problem/15654)

기존 1 ~ N에서 입력받는 숫자들로 순열을 만들게 바뀐 버전  
수를 입력받고 sorted로 정렬을 해준 후에  
arr.append(i)가 아닌 arr.append(data[i])를 해주면 된다

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(n):
        if data[i] not in arr:
            arr.append(data[i])
            dfs()
            arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []

dfs()
```

# [15655 N과 M (6)](https://www.acmicpc.net/problem/15655)

수를 입력받고 sorted를 한 수들로 순열을 만드는 15650번 변형 문제

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(n):
        if data[i] not in arr and (len(arr) == 0 or data[i] > arr[-1]):
            arr.append(data[i])
            dfs()
            arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []

dfs()
```

# [15656 N과 M (7)](https://www.acmicpc.net/problem/15656)

수를 입력받고 sorted를 한 수들로 순열을 만드는 15651번 변형 문제

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(n):
        arr.append(data[i])
        dfs()
        arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []

dfs()
```

# [15657 N과 M (8)](https://www.acmicpc.net/problem/15657)

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    for i in range(n):
        if len(arr) == 0 or data[i] >= arr[-1]:
            arr.append(data[i])
            dfs()
            arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []

dfs()
```

# [15663 N과 M (9)](https://www.acmicpc.net/problem/15663)

직전 값과 새로운 값을 비교하면서 중복 수열인지 확인한다

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    tmp = 0
    for i in range(n):
        if not visited[i] and tmp != data[i]:
            visited[i] = True
            arr.append(data[i])
            tmp = data[i]
            dfs()
            visited[i] = False
            arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []
visited = [False] * (n + 1)

dfs()
```

# [15664 N과 M (10)](https://www.acmicpc.net/problem/15664)

N과 M 6번 문제와 비슷하지만 같은 수가 있을 수 있으니 data[i] > arr[-1]에서  
data[i] >= arr[-1]로 바꿔야 한다

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    tmp = 0
    for i in range(n):
        if not visited[i] and tmp != data[i] and (len(arr) == 0 or data[i] >= arr[-1]):
            visited[i] = True
            arr.append(data[i])
            tmp = data[i]
            dfs()
            visited[i] = False
            arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []
visited = [False] * (n + 1)

dfs()
```

# [15665 N과 M (11)](https://www.acmicpc.net/problem/15665)

중복되는 수열을 여러 번 출력하면 안되지만 같은 수를 여러 번 골라도 되므로  
tmp != data[i]만 유지한다

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    tmp = 0
    for i in range(n):
        if tmp != data[i]:
            arr.append(data[i])
            tmp = data[i]
            dfs()
            arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []

dfs()
```

# [15666 N과 M (12)](https://www.acmicpc.net/problem/15666)

N과 M 8번과 비슷

```python
import sys
input = sys.stdin.readline

def dfs():
    if len(arr) == m:
        print(*arr)
        return

    tmp = 0
    for i in range(n):
        if tmp != data[i] and (len(arr) == 0 or data[i] >= arr[-1]):
            arr.append(data[i])
            tmp = data[i]
            dfs()
            arr.pop()

n, m = map(int, input().split())
data = sorted(list(map(int, input().split())))
arr = []

dfs()
```
