# Git

>  Git은 분산형버전관리시스템(DVCS) 중 하나이다.

## 0. Git 기초 설정

* windows 환경에서는 `git for windows`로 검색하며 `git bash`를 설치한다. [다운로드 링크](https://gitforwindows.org/)

* 최초의 컴퓨터에서 git을 사용하는 경우 아래의 설정을 진행한다.

  ```bash
  $ git config --global user.email 이메일주소
  $ git config --global user.name 유저네임
  #확인
  $ git config --global -l
  ```

  * 이메일주소를 설정할 때, github에 가입된 이메일로 설정을 해야 커밋 이력이 github에 기록된다.

## 1. Git을 통한 버전관리 기본 흐름

### 1.1 Git 저장소 초기화

> 특정 폴더를 git 저장소로 활용하기 위해서 최초에 입력하는 명령어

```bash
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/TIL/.git/
(master) $
```

* `.git` 폴더가 숨긴 폴더로 생성되며, git bash에서는 `(master)`라고 표기된다.

* 상위 폴더에 init을 설정한 경우 -> git 폴더 찾아 삭제
* 반드시 git으로 활용되고 있는 폴더 아래에서 저장소를 선언하지 말자.

### 1.2 `add`

> 커밋 대상 파일들을 추가한다.

`add` 전 상황

```bash
$ git status
On branch master

No commits yet
# 트랙킹 되지 않는 파일들
# =>새로 생성된 파일이고, git으로 관리 중이지 않는 파일
Untracked files:
	# git add 파일
	# 커밋이 될 것들을 포함시키기 위해서 위의 명령어를 써라!
  (use "git add <file>..." to include in what will be committed)
        git.md
        markdown-images/
        markdown.md

nothing added to commit but untracked files present (use "git add" to track)

```

```bash
$ git add .
$ git status
On branch master

No commits yet
# 커밋될 변경사항들
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git.md
        new file:   "markdown-images/\353\213\244\354\232\264\353\241\234\353\223\234-1594185087934.jpg"
        new file:   "markdown-images/\353\213\244\354\232\264\353\241\234\353\223\234.jpg"
        new file:   markdown.md

```

* add 명령어는 아래와 같이 활용된다.

  ```bash
  $ git add . #현재 디렉토리 전부
  $ git add git.md # 특정 파일
  $ git add git.md markdown.md
  $ git ass markdown-images/ # 특정 디렉토이
  ```

  ### 1.3 `commit`

  > 이력을 확정 짓는 명령어

  ```bash
  $ git commit -m '커밋메시지'
  [master (root-commit) 6f357bf] init
   4 files changed, 2 insertions(+)
   create mode 100644 git.md
   create mode 100644 "markdown-images/\353\213\244\354\232\264\353\241\234\353\223\234-1594185087934.jpg"
   create mode 100644 "markdown-images/\353\213\244\354\232\264\353\241\234\353\223\234.jpg"
   create mode 100644 markdown.md
   
  $ git status
  On branch master
  nothing to commit, working tree clean
  # 커밋할 것도 없고, 작업한 것도 없습니다.
  ```

  #### `log`

  > 커밋 내역들을 확인할 수 있는 명령어

```bash
$ git log
commit 6f357bf01ad9ea32ff4b6b84029b66d29109c6e4 (HEAD -> master)
Author: lpyeah6367 <lpyeah6367@gmail.com>
Date:   Wed Jul 8 14:41:40 2020 +0900

    init
# 최근 n개 이력(현재1개)
$ git log -1
# 1개
$ git log --oneline
# 간략한 표현
$ git log --oneline -1
# 최근 n개 이력을 간략하게
```

