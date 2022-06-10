**문제**

> k개의 로프를 사용하여 중량이 w인 물체를 들어올릴 때, 각각의 로프에는 모두 고르게 w/k 만큼의 중량이 걸리게 된다.
>
> 각 로프들에 대한 정보가 주어졌을 때, 이 로프들을 이용하여 들어올릴 수 있는 물체의 최대 중량을 구해내는 프로그램을 작성하시오. 모든 로프를 사용해야 할 필요는 없으며, 임의로 몇 개의 로프를 골라서 사용해도 된다.

</br>

**해결방법**

1. 최대 중량을 초과하면 로프는 끊어진다.

2. 그리디 (탐욕 알고리즘)

3. 최대 중량이 큰 순서대로 로프를 정렬한다.

4. 최대 중량이 큰 순서대로 우선순위를 곱해주면 된다.

   | 100  |  80  |  55  |  40  |  20  |
   | :--: | :--: | :--: | :--: | :--: |

   100 * 1 = 100

   80*2 = 160

   55*3 = 165

   40*4 = 160

   20*5 = 100

   답 : 165

   55씩 로프를 나눠서 들어올릴 경우 최대 중량이 100, 80, 55인 로프 3개를 이용해서 165까지 들어올릴 수 있다.

    </br>

```python
N = int(input())
max_weight = 0
rope_array = []

for i in range(N):
    rope = int(input())
    rope_array.append(rope)

rope_array.sort(reverse=True)

for i in range(N):
    rope_array[i] = rope_array[i] * (i+1)

for i in range(N):
    if rope_array[i] > max_weight:
        max_weight = rope_array[i]

print(max_weight)
```

