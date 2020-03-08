## [GIT] Git 명령어

```
git status : 깃 상태 확인
git add : Staging Area에 올림
git reset : 특정한 파일을 Staging Area에서 내릴 때 사용
git commit -m "" : Local Repository에 추가
git push : Remote Repository에 추가
git checkout -- 파일명 : 원래 상태로 소스코드를 돌릴 수 있음
git commit --amend : commit 메세지를 수정할 수 있음
git pull : 깃 저장소에 파일 받기
```



#### Commit 내역 수정하기

```
git log : 커밋(commit) 내용 확인 가능 (log 그만 보고 싶을 떄 q 입력)
git reset --hard "commit hash 값" : commit이 이루어 진 이후는 모두 지움 (--hard 모두 지움)
git push -f : 깃헙 저장소와 로컬 저장소가 다르기 떄문에 -f로 강제로 변경해야됨

--- commit message --- 변경하기
git commit --amend 입력 -> 수정모드 a 입력 -> commit message 수정 -> esc -> :wq!(수정된 내용 저장 후 나옴)

```

#### Git Rebase 명령으로 특정 커밋 수정/삭제

<img src ="https://user-images.githubusercontent.com/59730002/76063092-5b6b1b80-5fca-11ea-8757-11b8a93f7278.PNG">

```
git rebase -i HEAD~3 : 최근 세 개의 커밋메세지 확인 가능
원하는 Command 명령어 선택 후 wq! 
나와서 수정
```



