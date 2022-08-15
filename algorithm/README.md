## 스택, 큐, 덱

-   스택 : 배열의 맨뒤가 입구이며, 출구이다.
-   큐 : 배열의 맨앞이 출구이며, 맨뒤가 입구이다
-   덱 : 배열의 맨앞뒤 전부 출구이며, 입구이다

## 소수

### 에라스토테네스의 체

이 알고리즘은은 특정 범위에 존재하는 소수를 구하는 알고리즘이다.

```python
n = 100
array = [True]*n
answer = []

for i in range(n):
    if array[i] == True:
        answer.append(i)
    for j in range(i*2,n,i):
        array[j] = False

print(answer)
```

### 소수 판별

소수는 약수가 1과 자기자신 뿐인 수를 말한다

#### 맨땅에 해딩 O(N)

2부터 N-1까지 계속 나누어서 약수가 있는지 검사를한다

```python
n = 23
for i in range(2,n-1):
    if n%i == 0:
        print('소수가 아닙니다!')
        break
print('소수가 맞습니다!')
```

#### 논리적으로 판별하기 O(N/2)

소수가 아닐 경우 약수는 최대 N/2 이다  
그렇기에 N-1 => N2 로 시간을 줄일수 있다

-   24의 약수

`1` `2` `3` `4` `6` `8` `12` `24`

-   18의 약수

`1` `2` `3` `6` `9` `18`

```python
n = 23
for i in range(2,n/2):
    if n%i == 0:
        print('소수가 아닙니다!')
        break
print('소수가 맞습니다!')
```

#### 수학으로 판별 O(루트 N)

약수는 일정한 규칙이 존재하는데 24일 경우
A(2,3,4), B(12,8,6)를 곱했을 때 24가 나오는거다

해당 부분에서 A영역과 B영역의 중점이 루트N 이다  
하지만 루트N은 소수점까지 존재하기 때문에  
코드를 작성할땐 루트N 이 아닌 i \* i 로 작성해준다

-   24의 약수

`2*12 = 24` `3*8 = 24` `4*6 = 24`

-   18의 약수

`2*9=18` `3*6=18`

```python
def prime(n):
    if n < 2:
        return False
    i = 2
    while i*i <= n:
        if n%i == 0:
            return False
        i+=1
    return True

if prime(23):
    print('소수가 맞습니다!')
else:
    print('소수가 아닙니다!')
```
