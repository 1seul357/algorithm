**문제**

> 좋은 패스워드를 만드는것은 어려운 일이다. 가장 이상적인 해결법은 '발음이 가능한' 패스워드를 만드는 것으로 적당히 외우기 쉬우면서도 안전하게 계정을 지킬 수 있다. 회사 FnordCom은 그런 패스워드 생성기를 만들려고 계획중이다. 당신은 그 회사 품질 관리 부서의 직원으로 생성기를 테스트해보고 생성되는 패스워드의 품질을 평가하여야 한다. 높은 품질을 가진 비밀번호의 조건은 다음과 같다.
>
> 1. 모음(a,e,i,o,u) 하나를 반드시 포함하여야 한다.
> 2. 모음이 3개 혹은 자음이 3개 연속으로 오면 안 된다.
> 3. 같은 글자가 연속적으로 두번 오면 안되나, ee 와 oo는 허용한다.
>
> 이 규칙은 완벽하지 않다;우리에게 친숙하거나 발음이 쉬운 단어 중에서도 품질이 낮게 평가되는 경우가 많이 있다.

</br>

**해결방법**

- 단순 구현 문제. 조건문만 잘 체크하면 된다.
- 모음 포함하는지, 모음 혹은 자음이 3개 연속으로 오지 않는지, 같은 글자가 두번 연속으로 오는지 if 문을 통해 확인하고, 조건문에 부합하지 않으면 break를 통해 반복문을 종료한다.

</br>

**소스코드**

```python
check = ["a", "e", "i", "o", "u"]

while True:
    tmp = input()
    flag = 0                    // 모음 3개 오는지 확인
    che = 0                     // 자음 3개 오는지 확인
    repeat_check = 1    // 자음 혹은 모음이 연속적으로 3개 왔을 경우 반복문을 종료하기 위한 변수
    vowel = 0                   // 단어에 모음이 하나라도 있는지 확인
    if tmp == "end":
        break
    for i in range(len(tmp)):		// 같은 글자 2개 이상 연속적으로 오는지 확인
        if i != 0:
            if tmp[i] == tmp[i-1]:
                if tmp[i] == "e" or tmp[i] == "o":
                    repeat_check = 1
                else:
                    repeat_check = 0
                    break
    for str in tmp:    // 단어에 모음 포함되어 있는지, 모음 혹은 자음 3개 연속적으로 오는지 확인
        if str in check:
            vowel = 1
            che = 0
            if flag >= 2:
                repeat_check = 0
                break
            else:
                flag += 1
        else:
            flag = 0
            if che >= 2:
                repeat_check = 0
                break
            else:
                che += 1
                
    if repeat_check == 1 & vowel == 1:
        print("<" + tmp + ">" + " is acceptable.")
    else:
        print("<" + tmp + ">" + " is not acceptable.")
```

