# python 기본

프로그래밍 언어 3형식

데이터를 변수에 저장

조건에 맞게 반복



저장하는 것들

숫자, 글자, 참거짓



# code .

terminal에서

Code . 하면 현재 위치에서 vs code 열림

Code python_basic.py 하면 해당 파일이 같이 생김





# list

array = [1, 2, 3, 'four', 'five', 'six', True]

print(array[1:4])

print(array[:3])

print(array[-1])





# range

range(10) <- 이 자체가 하나의 객체기 때문에

list를 감싸주어야 .. list로 만날 수 있음





# random

import random

menu = ['20층', '양자강', '김밥카페', '순남시레기']
ran = random.choice(menu)

phone_book = {'20층': '010-1234-1234', '양자강': '012-345-6789',
              '김밥카페': '000-000-0000', '순남시레기': '111-111-1111'}


print(phone_book[ran])

print(random.choice(list(phone_book.values())))



# format

a = "최형인"

b = "민재"

f"제 이름은 {a} {b}입니다."



# while 문

while

n = 0

a = 0



while n < 1000:

​    if n % 3 == 0:

​        a += n

​    n += 1



print(a)





# 나누기

%, /, //





# 가상환경 셋팅

// 디렉토리에 venv 설치하기 
$ python3 -m venv venv

// 가상환경 실행하기
$ source venv/bin/activate

// 가상환경 종료하기
$ deactivate

터미널에 pip list 

python -m venv venv (여기서 m은 module) (앞 venv 가상 환경 셋팅 모듈)

(뒤 우리가 사용할..)

 source venv/bin/activate





내가 설정한 모듈들을 읽으면서 설치할 수 있게끔 (새로운 가상환경 안에서)

pip install -r requirements.txt



pip install requests

pip list (확인하기)



# requests

import requests

request = requests.get(url).text

(url) 까지를 텍스트로 변환시켜주는 .text

해당 페이지를 텍스트로 받아오는..





# bs4 설치

pip install beautifulsoup4

pip list

from bs4 import BeautifulSoup



soup = BeautifulSoup(request, 'html.parser')

위에서 저장한 변수 request(html형식)을 파이썬이 읽을 수 있게 html 형식을 parsing (=compile) 





# 실시간 환율 크롤링 해오기

import requests

from bs4 import BeautifulSoup

url = "https://finance.naver.com/sise/"



request = requests.get(url).text



soup = BeautifulSoup(request, 'html.parser')



//inspect에서 해당 Item을 copy - copy selector

kospi = soup.select_one("#KOSPI_now")

kospi_num = kospi.text

print(kospi_num)



# gitignore

http://gitignore.io/

깃헙에 파일 올릴 때 

개인적으로 발급받은 api key 등 개인적인 정보가 push 되지 않게끔..





# flask에서

if __name__ == : "__main__":

​    app.run(debug = True) 해주면

```
env FLASK_APP=hello.py flask run
```







# 웹..

### hello.py

from flask import Flask, escape, request, render_template





app = Flask(__name__)



@app.route('/')

def hello():

​    name = request.args.get("name", "World")

​    return f'Hello, {escape(name)}!'



@app.route('/hi')

def hi():

​    name = "형인"

​    return render_template('hi.html', html_name = name)



@app.route('/greeting/<string:name>/')

def greeting(name):

​    def_name = name

​    return render_template('greeting.html', html_name = def_name)



@app.route('/cube/<int:num>/')

def cube(num):

​    def_num = num**3

​    return render_template('cube.html', html_raw_num = num, html_num = def_num)





if __name__ == "__main__":

​    app.run(debug = True)



### html 들..

    <h1>{{html_raw_num}}의 3제곱은 <br> {{html_num}}입니다.</h1>



# html 안에서 for/if 문

​    <ul>

​        {% for movie in movies %}

​            {% if movie == '조커' %}

​                <li>{{movie}} || 이영화 진짜 재밌어</li>

​            {% else %}

​                <li>{{movie}}</li>

​            {% endif %}

​        {% endfor %}

​    </ul>





# flask

from flask import Flask



app = Flask(__name__)



if __name__ == ("__main__"):

​    app.run(debug=True)



원래의 flask run을 하면 변경된 것을 받아들이지 못해서

페이지 ㄲ고 다시 켜야하는데,

debug가업데이트 할때마다 새로고침만 하면 새로운 정보를 받아줌



flask 함수 작동 . name이 app





# ping pong

<body>

​    <h1>here is ping</h1>

​    <form action="/pong">

​        <input type="text">

​        <input type="submit">

​    </form>

</body>

form 데이터를 어디로 보낼 때

Input 받은 데이터를 어디로 보낸다 할때 action

action = pong으로 보내줌



​    <form action="https://search.naver.com/search.naver?">

​        <input type="text" name="query">

​        <input type="submit">

​    </form>

이렇게 하면 ? 뒤에 query=ㅇㅇㅇ가 붙어서 검색창으로 입력하게 됨





<input type="text" name="keyword">

입력받은 text가 keyword라는 이름을 가진 변수에 저장이 됨





# request

flask에서 지원해주는 request.. (from flask import request)

ping에서 keyword로 저장해서 보낸 걸 data라는 변수에 저장해서 pong.html로 보냄



ping에서 요청이 들어온..

ping사이트에서 





```zsh
➜  python git:(master) ✗ git add .
➜  python git:(master) ✗ git commit -m "Add test"
[master 449733a] Add test
 2 files changed, 20 insertions(+), 3 deletions(-)
 create mode 100644 python/test2.html
➜  python git:(master) ✗ git push origin master
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 696 bytes | 348.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/choihyungin/TIL.git
   a1cf1b6..449733a  master -> master
➜  python git:(master) ✗
```

