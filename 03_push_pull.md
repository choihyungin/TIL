# Push_Pull

### 1. 처음 사용하는 컴퓨터에서 파일 가져오기 `clone`

1. Github에서 복제하고 싶은 파일 주소 clone

2. ```shell
   $ git clone [파일 주소]
   ```





### 2. 원격 저장소와의 차이분만 가지고 오기 `pull`

```shell
$ git pull origin master
```



### 3. 다른 사람과 `clone & push`

- Leader
  - Github에서 settings - options - collaborators - add

- Members
  - Invitation 후 `git push origin master`
- 차이분만 가지고 오기 `pull`



### 4. 그 외

- 다른 사람과 협업 시에도 같은 방법으로 사용 (동기적 작업밖에 못함)



