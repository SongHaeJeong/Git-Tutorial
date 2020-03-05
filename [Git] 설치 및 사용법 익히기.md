### [Git] 설치 및 사용법 익히기

##### 

##### GitHub

- GitHub은 각종 소스코드를 오픈 소스로 누구에게나 공개한다는 가정하에 무료로 프로젝트 파일 업로드 가능
- 세계적으로 가장 큰 Git 저장소



##### 회원가입 후 repository 생성

<img>https://user-images.githubusercontent.com/59730002/75991472-d9cbad00-5f39-11ea-9abb-41d881c8144a.PNG<img>

.gitignore : 설정 파일들을 올리지 않기 위해 설정해주는 파일



#### Git 설치

- https://git-scm.com/download/win 사이트에 접속하여 Window 버전 설치

- Git 설치 후 명령 프롬프트에서 환경설정 진행

  - git config --global user.name 이름
  - git config --global user.email 이메일계정 

- C 폴더에 Git이름으로 폴더 생성

  - cd C:\GIt (Git 폴더로 이동)

- git clone 명령을 이용해서 생성한 Repository 접근

  - git clone https://github.com/SongHaeJeong/Git-Tutorial.git
  - clone은 쉽게 말해서 다운로드라고 생각

-  Git 폴더에 들어가면 .git이 생성 된 것 확인 

  - 보이지 않을 경우 확장명 숨기기 체크 해제
  - Local Repository - 우리 컴퓨터
  - GitHub Repository - remote Repository

- ```
  cd Git-Tutorial
  git add 파일명
  git commit -m "파일 추가"
  git push 
  ```

  

  

  

  

  

  

  









   