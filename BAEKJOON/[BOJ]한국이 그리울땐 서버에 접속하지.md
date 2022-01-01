```python
'''
as*df는 *를 기준으로 as는 tmp[0]에, df는 tmp[1]
패턴이 a*a고, 파일 이름이 a이면 패턴과 일치하는 것 아님. 패턴과 파일 이름 문자열 길이 확인 해야함
'''
N = int(input())
tmp = input().split('*')   # 패턴

for i in range(N):   # N번 반복해서 입력받기
    string = input()    # 파일 이름
    N = len(string)     # 파일 이름 길이를 변수 N에 저장
    if len(tmp[0])+len(tmp[1]) > len(string): # 파일 이름의 길이가 패턴 길이보다 작으면
        print('NE')     # NE 출력
    # 앞 문자와 맨끝 문자가 패턴과 일치하는지 확인
    elif string[0:len(tmp[0])] == tmp[0] and string[N-len(tmp[1]):N] == tmp[1]:
        print('DA')
    else:    # 일치하지 않으면
        print('NE')
```