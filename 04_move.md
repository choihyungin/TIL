# 이동

### 1. 폴더 B를 폴더 A 안으로 이동

```shell
# 현재 상황은 폴더A도 git, 폴더 B도 git
$ mv [폴더 B]/[폴더 A]

#폴더 B로 들어간 상태에서
ls -a 				#.git이 있는 것을 알 수 있음 (git으로 관리 중이라는 의미)
rm -r .git 		#.git 제거 (git 관리를 끝냈기 때문에 정말 폴더 A 안에 속하게 됨)
```
