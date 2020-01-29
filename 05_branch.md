# Branch



### 1. 생성 및 확인

```shell
$ git branch [branch_name]		#새로운 branch 형성
$ git branch									#master와 branch들 확인
$ git checkout [branch_name]	#branch 이동
```





### 2. 이동

```shell
$ git checkout [branch_name] #branch 이동
$ git checkout -b "branch_name" #branch 만들면서 이동
```

- (branch가 바뀌면) head라고 하는 pointer가 움직임
- 한 branch에서 무언가를 만들면 다른 branch에서는 보이지 않음





### 3. 병합

```shell
# 병합할 곳 (더 큰 곳)으로 이동을 한 후 병합될 곳 (작은 곳) 
$ git checkout [먹을 branch]
$ git merge [먹힐 branch]
```

#### 1) Merge Scenario

- Fast Forward Merge
  - merge 시점에 한 쪽 branch에만 commit들이 쌓여있을 때
- Auto Merge
  - merge 시점에 양 쪽 branch에 commit들이 쌓여있지만 conflict가 없는 경우
- Merge Conflict
  - merge 시점에 양 쪽 branch에 commit들이 쌓여있고 conflict가 있는 경우
  - Conflict: 한 파일 내에 상충하는 내용이 있을 경우
  - Pull request / 





### 4. 그래프

```shell
$ git log --oneline --graph #그래프로 상황을 보여줌
```





### 5. 삭제

```shell
$ git branch -d [branch_name]
```

