Commit
Git에서는 생성된 각 버전을 커밋(commit)이라고 한다

add와 commit 명령어는 스테이징과 커밋을 수행한다

$ git add 파일1 파일2
#파일들을 스테이지에 추가
#새로 생성한 파일을 스테이지에 추가할 때 add명령어를 사용한다

$ git commit
#스테이지에 있는 파일들을 커밋한다

$ git commit -a
# add 명령을 생략하고 바로 커밋할 때 사용한다
# 변경된 파일과 삭제된 파일은 자동으로 스테이징되고 커밋된다
# untracked 파일을 커밋되지 않는다
# 기존 커밋 이력이 있는 파일. 즉 modified 상태의 파일의 스테이징 과정을 생략할 수 있다

$ git commit -am "commit message"
$ git commit -a -m "commit message"
# add사용하지 않고도 stating area와 working directory에 있는 모든 파일들을 메시지와 함께 commit 한다

# GitHub에서는 원격저장소를 레포지토리(Repository)라고 한다

$ git remote add origin "원격 저장소 주소"
# 로컬 저장소에 원격 저장소 주소를 알려준다

$ git push origin master
# 로컬저장소에 있는 커밋들을 push 명령어로 원격 저장소에 올린다


$ git push [-u] [원격저장소별명] [브랜치이름]
# 현재 브랜치에서 새로 생성한 커밋을 원격저장소에 업로드 한다
# -u 옵션으로 브랜치의 업스트림을 등록할 수 있다
# 한번 등록한 후에는 git push만 입력해도 된다

커밋 히스토리에서 보이는 16진수 7자리는 커밋 체크섬 혹은 커밋 아이디이다

SHA1 해시 체크섬 값을 사용하는데 잉는 전 세계에서 유일한 값을 가진다

git 커밋은 일반적으로 커밋 아이디라고 하는 영문 소문자와 숫자 조합의 40자리 SHA1 해시 체크섬 값을 가진다

해시는 무언가를 잘게 쪼개서 섞어놓은 것을 말한다

체크섬은 데이터의 정확성을 확인하기 위해서 계산한 어떤 값을 말한다

따라서 SHA1 해시 체크섬은 SHA1이라는 알고리즘을 사용해서 만들어낸 체크섬 값을 말한다

github에 push를 할 때 아이디와 비밀번호를 입력받아야 하는데 SSH Key를 사용하면 이 과정을 생략할 수 있다

SSH(Secure Shell Protocol)은 사용하고 있는 terminal과 server 간에 안전하게 아이디와 비밀번호를 유지해주는 방법이다

Server에는 Public Key를 제공하고 내 컴퓨터에는 Private Key를 생성해 넣음으로써 push를 할 때 번거롭게 아이디와 비밀번호를 입력하지 않아도 된다

github의 계정의 Setting의 SSH and GPG keys 항목에서 SSH Keys를 설정할 수 있다

push
로컬에서 C1, C2 커밋을 만들고 난 후, github에서 C3라는 커밋을 만든 다음에 다시 로컬에서 C3라는 커밋을 만든 다음 서버에 push를 하면 rejected 에러가 발생한다

이 때, force 옵션을 사용해서 강제 push를 하게 되면 서버에 있는 내용은 지워진채 채 로컬에서 push한 커밋들의 history로 대체된 것을 확인할 수 있다

git push -f

기본적으로 push를 할 때는 git push를 사용하지만 간혹 history를 rebase를 이용해서 변경한 경우에는 force 옵션을 사용해서 push한다

서버에 변경사항이 있다면 git pull 또는 git fetch 명령어를 사용해서 로컬 history를 server에 맞게 업데이트 한 다음에 내 커밋들을 rebase해서 push 하는 것이 맞다

git push를 할 때 -u 옵션을 사용하는 경우도 있다

이 때, -u는 upstream을 지칭하는 말로 upstream은 다른 사람의 GitHub의 저장소를 Fork한 경우 내 GitHub가 origin이 된다.

그리고 fork를 시도한 저장소를 upstream이라고 부른다. origin와 upstream 모두 remote 저장소아가 때문에, 보통 origin과 구분하기 위해서 upstream 이라는 명칭을 주로 사용한다


# 버전 관리를 위한 내 정보 등록

$ git config --global user.email "hello.git.Github@gmail.com"

$ git config --global user.name "Cat-Hanbit"

$ git add README.txt

$ git commit -m "사이트 설명 추가" # 버전 생성

$ git log # 지금까지 만든 커밋 확인

$ git checkout 5813bb5
# 앞자리 7자리 커밋 아이디로 이동할 수 있다

$ git checkout - # 최신 커밋으로 돌아간다

좋은 커밋 메시지의 7가지 규칙
제목과 본문을 빈 줄로 분리한다

제목은 50자 이내로 쓴다

제목을 영어로 쓸 경우 첫 글자는 대문자로 쓴다

제목에는 마침표를 넣지 않는다

제목을 영어로 쓸 경우 동사원형(현재형)으로 시작한다

본문을 72자 단위로 줄바꿈한다

어떻게 보다 무엇과 왜를 설명한다

Clone
원격 저장소의 코드와 버전을 내 컴퓨터로 내려받는 것을 클론(Clone)이라고 한다

클론을 하지 않고 [Download ZIP]으로 소스코드를 받게 되면 원격저장소와 버전 정보가 제외 된다

pull은 원격 저장소에 새로운 커밋이 있다면 그걸 내 로컬 저장소에 받아 오는 명령어

$ git clone <저장소주소> [새로운 폴더명]

저장소 주소에서 프로젝트를 복제해 온다

새로운 폴더명은 생략가능하다. 생략할 경우 프로젝트 이름과 같은 이름의 폴더가 새로 생성된다

git clone 명령어를 사용할 때 저장소 주소가 꼭 원격일 필요는 없으며 로컬 저장소도 git clone 명령어로 복제할 수 있다

$ pwd

$ cd ..

$ git clone "원격 저장소 주소"
# 에러 발생 할 수 있다
# [새로운 폴더명] 옵션을 지정하지 않으면 복제한 프로젝트 이름과 같은 폴더를 만들게 된다
# 예를들어 hello-git-cli라는 로컬 저장소와 원격 저장소가 모두 있을 때

$ git clone "원격 저장소 주소" hello-git-cli2
# hello-git-cli2이라는 폴더 안에 원격저장소 이름의 폴더 생긴다

$ ls

$ cd hello-git-cli2

$ git log -- oneline


$ git remote
# 기본적으로 원격저장소의 이름은 origin이라는 것을 확인할 수 있다

$ git remote -v
# origin일 가리키고 있는 정확한 정보를 알 수 있다
# 원격 저장소 목록 확인

$ git remote add <원격저장소 이름> <원격 저장소 주소>
# 다수의 origin을 설정할 수 있다
# 원격 저장소는 여러 개 등록할 수 있지만 같으 별명의 원격저장소는 하나만 가질 수 있다
# 통상 첫번째 원격저장소를 origin으로 지정한다


$ git remote add server "원격 저장소 주소"
# server라는 이름의 원격 저장소 주소 추가


$ git remote add upstream "원본 저장소 주소"
# 만약 fork를 한 경우, fork 한 원본 저장소를 upstream으로 지정할 수 있다
# upstream은 원본 저장소를 지칭하는 관용적인 표현이다


$ git remote -v
# 원격 저장소 목록을 살펴본다
# origni과 server가 있는 것 확인
# 여러개의 원격 저장소를 추가할 수 있다

$ git remote show

$ git remote show origin
# show 명령어 뒤에 원격저장소의 이름 적어주면 origin에 관련된 정보 자세히 볼 수 있다


업스트림(upstream)브랜치는 로컬저장소와 연결된 원격 저장소를 일컫는 단어

업스트림 브랜치 설정을 위해서 —set-upstream 또는 -u 옵션을 사용한다

그러면 origin 저장소의 [master] 브랜치가 로컬 저장소의 [master] 브랜치의 업스트림으로 지정되어 git push 명령어만으로도 에러 없이 push가 가능해 진다

대개 git bash에서 긴 명령은 대시 두 개(--) 짧은 명령은 대시 한 개로 시작하는 경우가 많다

$ git push -u origin master
# push와 동시에 업스트림 지정할 수 있다

$ git clone "원격 저장소 주소" .
# 새로운 폴더 만들지 않고 기존의 폴더 안에
# 다운 받기 위해서 한칸 뛰우고 마침표
fetch
Fetch
원격 저장소로부터 코드를 받아 병합하는 pull 명령어와 달리, 그래프만 업데이트를 한다

따라서 fetch 명령어를 사용하면 로컬 브랜치는 원래 상태에서 최근 커밋 위치를 가리키고, 원격 저장소 origin/master는 fetch 명령어를 통해서 가져온 최신 커밋을 가리킨다.

server에 새로운 커밋이 생긴 경우, 로컬에서 fetch 명령어를 사용하면 server에 있는 git history를 받아와서 나의 git history를 업데이트 한다

fetch명령어는 내가 현재 로컬에서 작업하고 있는 HEAD는 그대로 유지하면서 server에 업데이트된 history 정보만 가지고 올 때 사용한다

fetch 명령어를 사용해서 그래프를 불러와서 원격 저장소와 차이점을 파악한 다음 git merge origin/master 명령어 통해서 Merge를 하게 되면 git pull 명령어를 쓸 때와 동일한 결과를 얻을 수 있다


$ git fetch [원격저장소별명] [브랜치이름]
# 원격 저장소의 브랜치와 커밋들을 로컬저장소와 동기화 한다.
# 옵션을 생략하면 모든 원격저장소에서 모든 브랜치를 가져온다

$ git fetch
# server에 있는 history 가지고 온다

$ git fetch orign
# origin과 같은 server 이름을 명시해서 작서알 수도 있다

$ git fetch origin "브랜치 이름"
# server에 여러개의 브랜치 있다면 특정 브랜치에 해당하는 정보만 가져올 수도 있다
Pull
로컬저장소와 원격 저장소와 차이가 있을 때 pull을 사용하면 원격저장소의 커밋을 로컬저장소에 내려받을 수 있다

원격저장소에서 파일을 받아 로컬저장소에 있는 파일과 병합이 된다.

따라서 git pull 명령어를 사용한 후에는 로컬저장소의 브랜치와 원격저장소의 origin/master가 같은 커밋을 가르키게 된다



$ git pull
# 원격 저장소의 변경사항을 워킹트리에 반영한다
# git fetch + merge와 같다

$ git pull origin master

fetch 같은 경우 내가 server에 있는 history 정보를 업데이트해서 server에서 어떤 일들이 지금 발생하고 있는지 확인하고 싶은 경우 사용한다.

따라서 아래처럼 fetch 명령어를 사용하면 origin/master는 새로 추가된 커밋 C3를 가르키고 있지만 로컬의 master 브랜치에서는 C2를 가리키고 있는 것을 확인할 수 있다

$ git fetch origin


            origin/master
              ↓
C1 <-- C2 <-- C3
        ↑
      master
하지만 나의 local 버전도 server와 동이랗게 만들고 싶을 때는 pull 명령어를 사용한다

따라서 아래처럼 pull 명령어를 사용하면 server에 있는 history를 가져오면서 나의 로컬에 있는 내용과 merger를 한다

그래서 아래와 같이 C3커밋이 생긴 것과 동시에 origin/master와 로컬의 master 브랜치가 같은 C3 커밋을 갈키고 있는 것을 확인할 수 있다

$ git pull

            origin/master
              ↓
C1 <-- C2 <-- C3
              ↑
            master
단순히 server에 local에 커밋이 하나 추가된 경우에는 pull 명령어를 사용하면 fast-forward가 일어난다

하지만 server와 local에서 각각 새로운 커밋을 추가한 경우에는 pull 명령어를 사용하면 Merge conflict가 발생한다

이러한 Merge conflict은 다른 brunch 사이 또는 server와 local 사이에서 동일한 파일을 수정하는 경우 발생할 수 있다


$ git pull
# Merge conflict 발생

$ git mergetool
# conflict 해결

$ git add .

$ git merge --continue
# 새로운 커밋 메시지 만들기 위해 텍스트 에디터 열린다

$ git log
# local에서 작성한 커밋과 server에서 작성한 커밋이 병합된 새로운 커밋 확인할 수 있다


이렇게 새로운 커밋이 만들어지는 것이 싫다면 rebase를 사용할 수 있다

$ git pull --rebase
# Merge conflict 발생
# server에 가져온 커밋을, 현재 local 커밋의 위에 적용

$ git mergetool
# conflict 해결
# local의 커밋과 server의 커밋 사이에 순서를 바꿀 수도 있다

$ git add .

$ git rebase --continue
# 새로운 커밋 메시지 만들기 위해 텍스트 에디터 열린다

$ git log
# history 깔끔하게 정리된 것을 확인할 수 있다

$ git push
# server에 변경된 내용 반영
