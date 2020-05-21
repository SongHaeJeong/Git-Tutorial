## Python Example

1. ```python
   [random 모듈 코드 구현 실습1 ] 
   두 사람이 주사위를 던져 더 큰 수가 나오면 이기는 게임이다
   A가 이기거나 B가 이기거나 비기는 결과가 나와야 한다
   프로그램 코드를 작성하시오
   [Sample Run]  
   A의 주사위 숫자는 2입니다.
   B의 주사위 숫자는 6입니다.
   B가 이겼습니다.
   
   
   import random
   a = random.randint(0,1)
   print(a)
   b = random.randint(0,10)
   if a > b :
       print("a가 b를 이겼습니다.")
   elif a< b :
       print("b가 a를 이겼습니다.")
   else :
       print("a와 b 비겼습니다.")
       
   
   
   ```

2. ```python
   [random 모듈 코드 구현 실습2 ]  --반복문을 빠져나오기 위해 label문과 goto문을 써야 할 수도 있습니다.
   같은 숫자가 나올 때까지 주사위 6개를 동시에 무한 반복해서 던진다.
   같은 숫자가 나올 때까지 몇 번 던졌는지, 1부터 6까지 연속된 숫자는 몇 번 나왔는지 출력하는  프로그램 코드를 작성하시오
   [Sample Run]  
   6개 주사위가 모두 동일한 숫자가 나옴 --> 2 2 2 2 2 2
   6개가 동일한 숫자가 나올 때까지 주사위를 던진 횟수 --> 10652
   6개가  동일한 숫자가 나올 때까지 1 ~6의 연속번호가 나온 횟수 --> 172
   
   
   import random
   
   
   
   dol_list =[0,0,0,0,0,0]
   same_result = 0
   diff_result = 0
   
   def samecheck():
       
       for a in range (len(dol_list)-1):
           if dol_list[a] != dol_list[a+1]:
               return False
   
       return True
   
   
   def continueCheck():
       for a in range(len(dol_list)-1):
           if dol_list[a] +1 == dol_list[a+1]:
               continue
           else:
               return False
   
       return True
   
   
   while(True):
       same_result += 1
       for a in range(0,6):
           ranNum = random.randint(1,6)
           dol_list.append(ranNum)
       
       flag = samecheck()
       if flag == True :
           break
       else :
           continueFlag = continueCheck()
           if continueFlag == True:
               diff_result += 1
               print(dol_list)        
           dol_list.clear()
   
   
   print("6개가 동일한 숫자가 나올 때까지 주사위를 던진 횟수 : " , same_result)
   print(dol_list)
   print("연속된숫자가 나올 때까지 주사위를 던진 횟수 : " , diff_result)
   
   
   
   ```

3. ```python
   다음 별 모양으로 출력하는  프로그램 코드를 작성하시오  
   [Sample Run]  
         ★ 
       ★★  
      ★★★   
    ★★★★ 
   ★★★★★ 
   
   j = 5
   for a in range(6):
       for b in range(6):
           if j <= b :
               print("★", end = " ")
           else :
              print("  ", end=" ")
       j -= 1
       print()
   
   ```

