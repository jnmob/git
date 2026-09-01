# Git & GitHub 개념 정리

## 1. Git과 GitHub

### Git

Git은 내 컴퓨터에서 파일의 변경 이력을 관리하는 **버전 관리 프로그램임.**

예를 들어 수정 사항이 생기면

```
버전 1
ꜜ
버전 2
ꜜ
버전 3
```

이런 식으로 변경사항 기록이 가능

그래서 문제가 발생하면 이전 버전을 확인하거나 회귀 가능 ㅇㅇ 개지림 ㅅㅂ

### GitHub
GitHub는 Git으로 관리하는 프로젝트를 **인터넷에 저장할 수 있는 공간임.**

```
내 컴퓨터 (로컬)
ꜜ
Git
ꜜ
GitHub
```

정리하자면 :
- Git = 내 컴에서 버전 관리
- GitHub = 코드계의 클라우드 스탈~

## 2. Git의 전체 흐름

Git의 기본적인 작업 흐름은

```
vs code에서 파일 수정 (working directory)
↓
git add
↓
staging area
↓
git commit
↓
local repository
↓
git push
↓
github (remote repository)
```

### git add

**변경된 파일을 commit할 준비를 하는 명령어.**

vs code에서 파일 수정을 하고
cmd + s 를 하면 
파일 옆에 이니셜 M이 뜸
-> modified, 즉 기존 파일을 수정했다는 뜻. 

이때 git add를 조지면
파일 옆에 A가 뜨져

실제 입력

- `git add 파일이름` = 특정 파일 add
- `git add .` = 폴더안의 전체 파일 add

### staging area 

git add를 실행한 파일은 
staging area에 들어걈

쉽게 말하면 : 이번 커밋에 포함시킬 파일들의 대기실 ㅇㅇ

### git commit

add를 하고 staging area에서 대기타고있는 놈들을 **하나의 버전으로 저장하는 명령어.**
프로젝트의 특정 시점을 저장하는 것이고, 따라서 문제 발생시 과거 변경사항을 확인할 수 있음.

실제 입력

- `git commit -m'메시지'` 
    메시지 칸에는 변경사항을 간단하게 적는것이 좋음.

### local repository

로컬 레뽀리로리 - 커밋을 한 기록이 (버전들) 여기 저장됨. ```.git``` > ```Local Repository```

깃허브의 레뽀리로리 - Remote Repository, 걍 깃허브의 저장소라고 보면 됨. 

정리하자면 : 
```
commit 
↓
local repository 
↓
push 
↓
remote repository (깃헙)
```

## 3. 자주 쓰이는 Git 명령어

### git status

**현재 git 상태를 알려주는 명령어**

위의 일련의 과정중 파일들이 어느 단계에 있는지 알려줌.

예를들어 

파일을 수정 후 status -
```
Changes not staged for commit:

    modified: index.html
```
= Index.html이 수정됐지만 git add 하지 않음.

git add후 status - 
```
Changes to be committed:

    modified: index.html
```
= index.html이 커밋할 준비가 됨.

commit후 status - 
```
nothing to commit, working tree clean
```
= 커밋 후에는 변경사항 없으니까.

```
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
```

= 니 브랜치에는 커밋이 하나 있는데 깃허브에는 없다,
깃푸쉬해라 

*git status 활용*

```
modified: 1.md
modified: 2.md
```
두 파일을 수정했음. 
근데 하나만 올리고 싶은거임
`git add 1.md`

그럴때 `git status ` 치면
```
Changes to be committed:
    modified: 1.md

Changes not staged for commit:
    modified: 2.md

= 음 1.md만 커밋 대기중이구나

틱마냥 머 할때마다 
`git status` 
