# GIT

## 1. 버전관리

`shift + ins` : 붙여넣기

`ctrl + ins` : 복사

```bash
$ git init . : 현재 디렉토리를 git에게 버전관리를 시킨다.(repository를 초기화한다) master가 생김
$ ls -al : 하위 디렉토리 확인
$ cd : 디렉토리 변경
$ cd .. : 상위 디렉토리로 이동
$ cd {하위 디렉토리명} : 하위 디렉토리로 이동
$ mkdir {디렉토리명} : 새로운 하위 디렉토리 생성
$ nano {파일명} : 파일 생성 or 이미 생성된 파일 열기
$ cat {파일명} : 파일의 내용 출력
$ git status : 디렉토리 상태
$ git add {파일명} : staging area에 추가한다.
$ git add . : 해당 디렉토리의 모든 수정된 파일을 staging area에 추가
$ git commit : staging area에 있는 파일이 repository로 간다. 에디터가 뜸 
나가기 : :wq 
저장하지 않고 나가기 : q!
$ git commit -m "내용" : 에디터가 안뜨고 내용을 적어서 commit 할 수 있다.
$ git commit -am "내용" : add와 commit을 동시에 한다. (add가 한 번 이상 된 파일만 가능)
$ git log : show version
$ git log --stat : 해당 버전에 어떤 파일이 몇 줄 추가되거나 수정되었는지 알려준다.
$ git log -p : 버전별로 무엇이 추가되었는지 알려준다.
$ git diff : 마지막 버전과 워킹 트리의 차이점을 보여준다.
$ git checkout {해당 coommit 주소} : 해당 버전으로 돌아간다.
$ git checkout master : 가장 최근 상태로 돌아간다.
$ touch hello2.txt : 파일 새로 생성
$ git reset --hard : 워킹 트리를 리셋한다. 마지막 버전으로
$ git reset --hard {commit id} : 해당 버전으로 리셋된다.
reset은 협업하기 전 버전까지만 사용해야한다.
$ git revert {해당 버전 주소(commit id)} : 해당 버전 이전의 버전으로 돌아간다.
역순으로 revert 하지 않으면 충돌이 일어나게 된다.
$ git commit --amend : commit 수정 가능
$ rm -rf .git : master 사라짐 폴더 삭제(조심!)
```

### branch

```bash
$ git branch : branch 확인
$ git branch {branch명} : 현재 버전에 대한 branch 추가
$ git log --all --graph --oneline : branch log 그림으로 확인할 수 있다.
```

### merge

```bash
* 먼저 병합을 할 두 branch master와 o2 가 있다. o2를 master에 병합하는 경우.
$ git checkout master : master branch로 돌아간다.
$ git merge 'o2': merge branch o2 생성된다. -> master에 o2를 합친 branch 생성
#*만약 같은 위치에 수정된 내용이 merge되려고 하는 경우 conflict 발생
#<<<<<<< HEAD
#master 
#======= (구분자)
#o2 (이 부분만 수정 해주면 merge 해준다는 의미)
#>>>>>>> o2
#(수정 후 저장)
$ git add {파일이름}
$ git commit -> merge branch 생성
```



### reset vs checkout

> checkout

- head를 제어한다.

- head는 branch를 가리킬 수도 있고 commit 자체를 가리킬 수도 있다.
- branch 자체는 변하지 않기 때문에 change의 기능을 한다.



> reset

- head가 branch를 가리키고 있는 동안에는 branch를 제어한다.

- commit을 가리키는 branch가 바뀌기 때문에 commit에 접근할 수 없게 된다.



## 2. 백업

> git hosting

> 원격저장소 연결

```bash
$ git remote add origin {원격저장소 주소} : local repository를 origin이라는 이름의 remote repository에 연결한다.
$ git remote -v : 원격저장소 주소 출력
$ git push -u origin : 원격저장소에 로컬저장소 파일 백업/다음부터는 git push만 해도 된다.
$ git clone {주소} : 현재 디렉토리에 원격 저장소의 clone 생성  
$ git pull
```

## 3. 협업

> pull vs fetch

```bash
git pull = git fetch + git merge FETCH_HEAD
```

- 신중하게 원격 저장소의 파일을 가져오고 싶을 때 fetch를 사용한다.

```bash
git fetch # 원격 저장소만 업데이트 한다. remote branch만 가져올 때 사용
# .git/FETCH_HEAD 폴더 생상
git merge FETCH_HEAD #가장 최근 fetch 내용을 merge한다.
```