## Dictionary Example

```python
[딕셔너리 코드 실습1] 딕셔너리를 활용해 음식 궁합을 출력하는  프로그램 코드를 작성하시오  
음식을 종류별로 여러 개 출력 한 후 이 중 좋아하는 음식을 입력하면 궁합에 맞는 음식을 출력한다.
목록에 없는 음식을 입력하면 '없다'는 메시지를 출력하고, '끝'을 입력하면 프로그램을 종료한다.
[Sample Run]  
[떡볶이, 짜장면, 라면, 피자, 맥주, 치킨, 삼겹살] 중 좋아하는 음식은? 치킨
<치킨> 궁합 음식은 <치킨무> 입니다.
[떡볶이, 짜장면, 라면, 피자, 맥주, 치킨, 삼겹살] 중 좋아하는 음식은? 라면
<라면> 궁합 음식은 <김치> 입니다.
[떡볶이, 짜장면, 라면, 피자, 맥주, 치킨, 삼겹살] 중 좋아하는 음식은? 짬뽕
그런 음식이 없습니다. 확인해 보세요
[떡볶이, 짜장면, 라면, 피자, 맥주, 치킨, 삼겹살] 중 좋아하는 음식은? 끝




like_food = {'떡볶이': '허니콤보' , '치킨' : '치킨무' , '라면' : '김치'}

def select(food):
    select_food = food
#     print(select_food)
    flag = False    
    for i in like_food.keys():
#         print(i)
        if i == food:
            flag = True
            break
        
    if flag == True:
        print(like_food[select_food] )
    else:
        print("그런 음식이 없습니다. 확인해 보세요")

def process():
    while(True) :
        select_food =  input("")
        if select_food == '끝':
            break
        else :
            select(select_food)


process()
```



```python
[코드 실습2] 문자열을 입력받고, 입력된 문자열을 거꾸로 출력하는 프로그램을 작성하시오 (함수로 코드 정의)
[Sample Run]  
문자열을 입력하세요: 즐거운 Python 프로그래밍
내용을 거꾸로 출력 ==> 밍래그로프 nohtyP 운거즐

def reverse_print(sen):
#     print(sen)
    s =""
    sen_len = len(sen)
    for i in sen:
        s = i + s  
    print(s)   

    
reverse_print("ㅁㄴㅇㅁㄴㅇ")
```

```python
[코드 실습3]  긴 장문에서 각 문자의 발생 빈도를 센다. 출력은 빈도수가 높은 글자부터 출력한다. 
단 한글만 빈도수를 세고 나머지 글자들은 무시한다.   (함수로 정의)
[Sample Run] 
원문 
내가 그의 이름을 불러주기 전에는 그는 다만 하나의 몸짓에 지나지 않았다.
내가 그의 이름을 불러주었을 때, 그는 내게로 와 꽃이 되었다
내가 그의 이름을 불러준 것처럼 나의 이 빛깔과 향기에 알맞은 누가 나의 이름을 불러다오.
그에게로 가서 나도 그의 꽃이 되고 싶다.
우리들은 모두 무엇이 되고 싶다.
나는 너에게 너는 나에게 잊혀지지 않는 하나의 눈짓이 되고 싶다
-------------------------------------
문자              빈도수
-------------------------------------
이                9
의                8
나                8
그                7


import re
import operator
hanguel_cnt = {}

def count_hanguel(sentence):
    for i in sentence:
        for j in i:
            if j in hanguel_cnt:
                hanguel_cnt[j] = hanguel_cnt[j] + 1
            else :
                hanguel_cnt[j] = 1
            
        
def print_hanguel():
    for i in hanguel_cnt:
        print(i[0], i[1])
        
        

insert_sentence = '내가 그의 이름을 불러주기 전에는 그는 다만 하나의 몸짓에 지니지 않았다.'
insert_sentence = re.compile('[가-힣]+').findall(insert_sentence)
# print(insert_sentence)
count_hanguel(insert_sentence)
hanguel_cnt = sorted(hanguel_cnt.items(), key = lambda x : x[1] , reverse = True)

# print(hanguel_cnt)
# print(hanguel_cnt)
print_hanguel()
```