# TIL :smile: 

:computer: **서버의 원격 저장소** 
- origin이라고 부름.
- 주소 예: https://github.com/eunji1340/git-test.git.
- 원격 저장소는 초기에는 비어 있음(커밋 X, 브랜치 X).
- 브랜치: 커밋과 커밋을 잇는 가지.
- 명령어:
    - -u origin master: 원격 저장소에 master 브랜치를 생성하고 로컬의 master 브랜치와 연결.
    - 서버 원격 저장소가 비어 있을 때만 최초 1회 사용.
    - 이후로는 -u 옵션 불필요.

:memo: **로컬 저장소**
- 최초 커밋 시 기본 브랜치 master에 커밋됨.
- 명령어:
```bash
git remote add origin https://github.com/eunji1340/git-test.git
```
- 로컬 저장소에 원격 저장소 추가
```bash
git branch -M master
git push -u origin master
```
- 원격 저장소에 커밋 목록 업로드
```bash
git remote -v
```
- 등록된 원격 저장소 목록 확인.

:wave: **원격 저장소와 상호작용**
- 원격 저장소에서 변경사항 가져오기
```bash
git pull origin master
```
- 원격 저장소 복제
```bash
git clone <remote_repo_url>
```
- 파일 작업 예시
```bash
touch a.txt  # 파일 생성
git add .    # 스테이징
git commit -m "a"  # 커밋
git push     # 원격 저장소에 업로드
```
---
:see_no_evil: **.gitignore**
- 특정 파일/디렉토리를 Git이 추적하지 않도록 설정.
- 주의: 이미 추적 중인 파일은 .gitignore에 추가해도 적용되지 않음.
    - 추적 해제 명령
    ```bash
    git rm --cached <파일명>
    ```
- 명령어 예시
``` bash
echo "a.txt" > .gitignore  # .gitignore 생성 및 내용 추가
```
---
:pencil2: **Git 명령어 정리**
1. 스테이징에서 추적 제외하기
```bash
git add b.txt
git rm --cached b.txt
```
2. 커밋 후 추적 제외하기
```bash
git add c.txt
git commit -m "c.txt added"
git rm --cached c.txt
git add .
git commit -m "c.txt deleted"
```
- 두 개의 커밋 생성(c.txt 추가 → 삭제)
---
:car: **Git 브랜치 및 커밋 이동**
- 특정 커밋으로 이동
```bash
git checkout <커밋해시번호>
```
- 브랜치로 이동
```bash
git checkout master
```
- 커밋 로그 확인
```bash
git log --oneline
```
---
:: **Git revert**
- 특정 커밋을 취소하는 새로운 커밋을 생성
- 이전 커밋 기록은 그대로 남아 있음

**Git reset**
- 특정 커밋으로 되돌아가기. 이후 커밋은 삭제
- 옵션:
    - --soft: 삭제된 커밋의 기록이 스테이징 영역에 남음
    - --mixed: 삭제된 커밋의 기록이 작업 디렉토리에 남음 (기본값)
    - --hard: 삭제된 커밋의 기록이 아예 남지 않음
---
**Git restore**
- 작업 영역 복원
```bash
git restore <파일명>
```
- 스테이징 취소
```bash
git restore --staged <파일명>
```
---
**Git revert vs reset vs rm 비교**
- revert: 특정 커밋을 무효화하고 새로운 커밋 생성.
- reset: 특정 커밋으로 되돌리며 이후 커밋 삭제.
- rm: 파일을 추적에서 제외하고 다음 커밋에서 삭제.