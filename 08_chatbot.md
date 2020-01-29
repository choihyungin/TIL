# gitignore

macOS, venv, visualstudioCode, python, flask



# get ID 

telegram에서 Kawaicorgi chat 시작 후에

https://api.telegram.org/bot[API]/getUpdates

들어가서 아이디 얻기



# app.py write.html .env 생성

pip install python-decouple





# 흐름

user - telegram - webhook - flask - telegram - user

user - tele - webhook - flask - telegram - google trans - telegram - user

##### webhook 설명

https://core.telegram.org/bots/api#getting-updates



# ngrok

In desktop

https://phoby.github.io/ngrok/ 참고

```zsh
ngrok http 5000
```

http://로 시작하는 걸 복사해두기



# 주소 연결

zsh에서 ngrok 열어두고

Vscode 서버도 열어둔 상태에서

Https:// 이거 뒤에 /write 하면 정상 작동



# webhook.py

.env에서 token 불러오려면 from decouple import config

requests.get('{url}{token}/[메소드이름]')

requests.get(f'{url}{token}/setwebhook?url={ngrok_url}/{token}')

텔레그램 서버와 연동 (변수로 작동하게끔 해주는 기능이 f !)ㅌ

텔레그램에 요청이 들어오면 그걸 우리에게도 보내줘

그걸 설정하기 위해서는 텔레그램이 정해놓은 양식에 맞추서 요청을 보냄

api주소 뒤에 우리 봇의 token을 넣어주고 메소드 네임 setwebhook.

어디로 보내줬으면 좋겠는데를 담아준 ngrok (외부인도 접속 가능하게끔)



텔레그램 서버로 들어온 요청이 flask로 넘어옴

토큰에 붙여준 그 주소로 넘어옴



로컬 외부에서 접속

서버를 webhook 으로..



# 서버 배포

구글에서 python anywhere

로그인 후 web 태그로 이동

add a new web app

http://hyungin.pythonanywhere.com/

Files - directories-mysite - files에 flask_app.py

flask_app.py에 vsCode app.py 코드 복붙

다시 우측 상단 세줄 눌러서 web으로 이동해서 reload

만들었던 .env 등 파일 저기에 이동시켜주기

consoles로 이동해서 pip3 install python-decouple --user해서 decouple 설치

files - files 에 .env 생성

web - 

webhook.py에 ngrok이었던 주소 바꿔주고, 한번실행