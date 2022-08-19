```python
def solution(answers):
    math1 = [1, 2, 3, 4, 5]
    math2 = [2, 1, 2, 3, 2, 4, 2, 5]
    math3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5]
    count = [0 for _ in range(3)]
    answer = []

    for i in range(len(answers)):
        if math1[i % len(math1)] == answers[i]:
            count[0] += 1
        if math2[i % len(math2)] == answers[i]:
            count[1] += 1
        if math3[i % len(math3)] == answers[i]:
            count[2] += 1

    for i in range(3):
        if count[i] == max(count):
            answer.append(i+1)
    return answer
```

