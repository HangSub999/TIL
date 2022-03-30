# 3일차

## node,hexo
- node -v (노드 버전 확인)
- npm -v (버전체크)
- npm remove -g hexo-cli (지웠다 깔기)
- npm install -g hexo-cli (핵소 글로벌 설정)
- hexo init (폴더이름) —핵소폴더 인잇
- npm install (남은 자료 다운)
- hexo new post “아무 단어”
- hexo server
- **git switch**
- git branch -D
- **git merge**

## git flow 사용법
- git flow init( 기존 git 저장소 내에서 초기화 하며 git-flow의 사용을 시작한다)
- git flow feature start  (별명) - ( ‘develop’에 기반한 새기능 브랜치를 생성하고 그 브랜치로 전환 합니다.
- git flow feature finish (파일명) - (위에서 만든 브랜치를 develop에 병합(merge)합니다.
    - 기능 브랜치를 삭제합니다.
    - de velop 브랜치로 전환 됩니다.
- git flow release start v0.0.1 (릴리스 시작이며 develop 브랜치로부터 release브랜치를 생성합니다.
- git push -u origin develop( develop 최초 푸시 할 경우 -u 해줘야 함)
- git checkou main (메인으로 이동)
- git push origin main( main 푸쉬)
