# 250116 til-practice :punch: 

### git의 구조
#### 1. 서버의 원격 저장소 (origin)
* **github에서 만든다.**
    - 처음엔 비어있는 상태임 (커밋도 없고, 브랜치도 없음)
* **git push -u origin master**
        
    * origin 서버에 master라는 이름의 브랜치를 생성하여, 로컬의 master 브랜치를 서버의 master 브랜치와 연결하겠다는 뜻.
        
    * 그러므로 ==서버의 원격 저장소가 비어있는 경우, 한 번만== 할 수 있다.
        
    * 팀장이 제일 처음 원격 저장소를 만들면면, 나머지 팀원들은 git clone을 통해 원격 저장소를 복제하여 사용해야 함
        
    * `-u` 는 로컬의 브랜치를 서버 브랜치에 연결하는 행위.


#### 2. 로컬 저장소
- 최초의 커밋을 하면 기본 브랜치 master 에 커밋된다. (그니까 자동 생성되겠지?)
- master 브랜치에 커밋이 쌓여 있음

---

### 이미 진행된 파일 수정하기
#### 1. unstage 하고 싶을 때
→ git add 만 한 상태일 때, 취소하고 싶을 때
* **git restore**
    커밋에서 복사해서 작업 영역 내용 덮어쓰기(복원)
* **git restore --staged**
     스테이지 영역에서만 삭제, 작업 영역은 그대로
* **git rm**
     스테이징 영역과 작업 영역 둘 다에서 삭제됨
* **git rm --cached**
     stage 영역에서 제외하면서, 그다음 삭제하는 커밋을 만들게 됨
        
    

#### 2. Commit 을 되돌리고 싶을 때
이전 커밋(가장 최근 커밋 x)을 무효화하는 새로운 커밋을 만듦

이전 커밋을 삭제하는 것이 아니라, 무효화 시키는 커밋을 새로 만드는 것임. 때문에 이전 커밋은 남아있다. checkout 해보면 다 나옴

* **`git reset [옵션] <commit id>`**
    
    특정 commit으로 되돌아가기.
    되돌아간 commit 이후의 commit은 모두 삭제
    
    
    1. `git reset --soft <해시번호>`
        - 작업 영역 그대로 : ls -l로 확인 가능
        - 삭제된 것은 stage 영역에 올라가 있음 : git status
        - 커밋 기록은 삭제됨(그러나 사실 데이터베이스에는 남아있음) : git log --oneline
        
    2. `git reset --mixed <해시번호>`
        - 작업 영역 그대로(삭제 x)
        - stage 영역에 없음(추적 안됨)
        - 커밋 기록이 삭제됨
        
    3. `git reset --hard <해시번호>`
        - 작업 영역에서도 삭제
        - stage 영역에 없음
        - 커밋 기록 삭제