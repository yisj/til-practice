0115/ 0116
# 원격 저장소 = git에 대하여
코드와 버전 관리 이력을 **온라인(서버)** 의 특정 위치에 저장하여 여러 개발자가 협업하고 코드 공유하는 **저장 공간**

ex) GitLab-보안이 중요한 회사, GitHub-전체공유, Bitbucket-검색예정

- 서버(원격)과 로컬(내 컴퓨터)를 동기화
- `push`
    - 로컬이 최신이라 서버에 전송
- `pull`
    - 서버가 최신이라 로컬에 전송
- `clone`
    - 다른 컴에서 작업하려 할 때 복제하기
> ## Git 명령어 모음집(목차랑 같은 순서로)
|명령어|내용|
|-|-|
|`pwd`|현재 디렉토리 출력, 위치 확인|
|`ls -l`|폴더, 파일 목록 확인|
|`mkdir 폴더명`|폴더생성|
|`cd ..`|상위 폴더로 이동|
|`cd ~/Desktop`|데스크톱폴더로|
|`touch 파일명.확장`|파일 생성|
|`rm 파일명`|파일 삭제|
|`start 파일명`|확장자대로 열기|
|`code 파일명`|vscode로 열기|
|``||
|``||
|``||
|``||

|`git status`|변경 사항 확인(스테이징과 커밋)|
|`git log --grahp --oneline --decorate --all`|커밋해시테그 파일명 메세지|
|`git remote -v`|원격저장소 목록|
|`git init`|현재 dir 기준으로 git저장소 생성|
|`git add "파일명"`|스테이징|
|`git add .`|수정된 모든 파일 스테이징|
|`git commit -m "수정메세지"`|스테이징 -> 저장소 영구 저장, |
|`git push`|서버에|
|`git pull`|로컬에|
|`git clone`|서버 복제|
|`git config --global user.name "jiwoo Lee"`|브랜치 이름 수정. 로컬에서 깃을 쓸 때 이메일과 유저 이름 필요|
|`echo ||

## 💃동기화하기
### 1. 최초로 로컬을 서버와 연동할 때
#### `git remote add origin https://github.com/LeeJiwoo982/git-test.git`
- `git remote`
    - 로컬에 서버 추가
- `origin`
    - 서버의 별칭
    - 대부분 orgin으로 함. 다른거 하지마
    - 변경은 가능
- `remote_repo_URL`
    - 서버 url
    - 팀장으로 처음 만들면 보이고, 팀원이면 팀장이 알려ㅔ줄 것
#### `git branch -M master`
- 메인 브랜치 이름은 마스터로 하겠다.
#### `git push -u origin master`
- 서버에 커밋 목록 업로드
- '깃아 푸시를 해줘. 오리진이란 이름의 서버에 마스터란 이름의 브랜치를'
- 서버가 비어잇는 경우에 한 번만
- 팀장이 처음 서버만들면 팀원은 `git clone`으로 서버 복제하여 사용

- 최초 푸시할 때 깃헙에서 확인 브라우저 창 열림. 푸시할 권한이 있는지
- 터미널에 푸시 성공 확인
- 서버에서 커밋됐는지 확인

- `git remote -v`
    등록된 서버 목록 확인


### 2. gitignore

- 이미 커밋이 된 상태면 .gitignore 적용이 단됨

git rm - -cached 로 git 캐시에서 삭제 필

cat  파일내용 출력

touch ~

git add .

echo “~” >> .gitignore

cat .gitignore

git status

git rm - -cached ~

git status

- HEAD 가장 최근 커밋
- master, origin/master : 브랜치, 커밋을 가르키는 포인터 역할

머지

마스터와 갈라진 브랜치를 합치는 

git checkout [브랜치/ 해시번호] 

해시 커밋으로 돌아가기 가

본인이름의 리파짓하고  readme. 만들면 바로 보

리버트

재설정

커밋을 취소하고 새롭게

부득이할 때 사용

엥간하면 사용하지 말기

커밋은 절대 변화는 안됨 새거 추가인거

### `git revert`

- 특정 커밋을 무효화하는 새로운 커밋을 만듦
- 무효화 되었지만 이전 커밋 그대로 남아있음
- `git checkout [해시번호]`  : 이전 커밋으로 돌아가기
- `ls -l`: 파일 목록 확인
- `git checkout master` : 마스터의 최근 커밋으로 돌아가기

### `git reset --soft <해시번호>`

- 워킹 디렉토리 그대로
- 삭제: 스테이지 영역 남아있음
- 커밋 기록 삭제
- 데이터베이스에는 남아있다.

### `git reset --mixed` <>

- 작업 영역 그대로 삭제아님
- 스테이지에 없음 추적 안됨
- 커밋기록 삭제
- 

### `git reset - -hard <>`

- 작업영역 삭제
- 스테이지 삭제 추적 안됨
- 커밋 기록 삭제
- 햣

### `git restroe <파일명>`

- 이미 커밋된 파일이 있는 경우
- 해당 파일 수정했는데, 수정한게 마음에 안들어, 커밋된 파일로 복원하고 싶을 때
- 커밋에 든 파일을 복사, 작업영역에 있는 파일 덮어쓰기
- 작업중인 내용도 건들여버려서 스테이징만 건들일 때는 `--staged` 붙이기 필수

## `unstage` 하고플 때

스테이징에서 워킹으로 내리고 싶을 때

= add하고 취소하고 싶을때

### `git rm - -cached`

커밋 없을 때

### `git restore - -staged`

커밋있어도 괜춘

스테이징에서 워킹으로

## 고려사항

working
staging
commit