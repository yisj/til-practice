# til-practice

## 작업 순서
1. `git clone https://github.com/yisj/til-practice.git`
2. `cd til-practice`
3. `git branch sj` : 브랜치 만들기
4. `git checkout sj` : 브랜치 master에서 sj로 전환
5. `touch 이승재.md`
6. 자유 주제(오늘 배운 내용, 공유하고 싶은 내용)으로 마크다운 문서 완성하기
7. `git add 이승재.md`
8. `git commit -m "submit"` : 로컬 sj 브랜치에만 있는 커밋
9. `git push -u origin sj` : 원격 저장소에 origin/sj 브랜치를 만들고, 로컬 sj 브랜치를 원격 sj 브랜치에 푸시
