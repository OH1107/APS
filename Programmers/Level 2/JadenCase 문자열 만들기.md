###### 문제 설명

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

##### 제한 조건

- s는 길이 1 이상인 문자열입니다.
- s는 알파벳과 공백문자(" ")로 이루어져 있습니다.
- 첫 문자가 영문이 아닐때에는 이어지는 영문은 소문자로 씁니다. ( 첫번째 입출력 예 참고 )

##### 입출력 예

| s                       |         return          |
| ----------------------- | :---------------------: |
| "3people unFollowed me" | "3people Unfollowed Me" |
| "for the last week"     |   "For The Last Week"   |

---

```python
def solution(s):
    answer = ''
    tmp = ''
    
    for c in s:
        if c == ' ':
            if tmp:
                answer += tmp.capitalize()
                tmp = ''
                
            answer += c
            
        elif c != ' ':
            tmp += c
    
    answer += tmp.capitalize()
    
    return answer
```

- `s`를 문자 하나하나 순회
  - ` ' '`(공백)을 만났을 경우 바로 `answer`에 추가하고 글자를 모아둔 `tmp` 변수 확인
    - `tmp` 변수에 값이 있다면 `answer`에 문제에 맞게 변환하고 추가, 그 후 빈 문자열로 초기화
  - `' '`(공백)이 아닌 문자를 만났다면 `tmp`에 누적
  - 마지막 `tmp` 변수에 합쳐지지 못하고 남은 단어가 있으면 추가하고 리턴