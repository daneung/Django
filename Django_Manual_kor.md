# **Django, 나도 사용할 수 있다!**
---
## Django의 개요
Django는 파이썬으로 작성된 **오프소스 웹 어플리케이션 프레임워크**입니다.
일반적으로 웹 브라우저 또는 웹 서버는 데이터베이스에서의 데이터 연결 및 판독을 하지 못합니다.
이러한 것을 해소하기 위해서는 웹과 데이터베이스 미들웨어를 사용하면 되지만, 현재 우리는 더욱 똑똑한 오픈 소스가 있습니다.
장고의 주된 목표는 고도의 데이터베이스 기반 웹사이트 작성에 있어서 수고를 더는 것입니다.
***

## 시작하기에 앞서...
Django는 **파이썬**으로 사용되는 오픈소스입니다.
따라서 여러분들이 이 메뉴얼을 보고 학습을 하기전에 파이썬에 대한 지식을 모르시는 분들은 공부를 하고 읽으시면 이해하시는데 훨씬 수월할 것 입니다.
***
## Django 시작하기
Django project 를 구성하는 코드를 자동 생성해야 하는데, 이 과정에서 데이터베이스 설정, Django 위한 옵션들, 어플리케이션을 위한 설정들과 같은 Django 인스턴스를 구성하는 수많은 설정들이 생성되기 때문입니다.
우선 커맨드라인에서 코드를 저장할 디렉토리로 이동한 후 다음 명령어를 실행합니다.

"django-admin startproject mysite"

Python 이나 Django 에서 사용중인 이름은 피해야 합니다. 특히, django (Django 그 자체와 충돌이 일어납니다) 나, test (Python 패키지의 이름중 하나입니다) 같은 이름은 피해야 한다는 의미입니다.

***
**최초의 소스 트리**
~~~~
mysite/
manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
~~~~

* mysite/ 디렉토리 바깥의 디렉토리는 단순히 프로젝트를 담는 공간입니다. 이 이름은 Django 와 아무 상관이 없으니, 원하는 이름으로 변경하셔도 됩니다.

* manage.py: Django 프로젝트와 다양한 방법으로 상호작용 하는 커맨드라인의 유틸리티 입니다.

* mysite/ 디렉토리 내부에는 project 를 위한 실제 Python 패키지들이 저장됩니다. 이 디렉토리 내의 이름을 이용하여, (mysite.urls 와 같은 식으로) project 어디서나 Python 패키지들을 import 할 수 있습니다.

* mysite/__init__.py: Python 으로 하여금 이 디렉토리를 패키지 처럼 다루라고 알려주는 용도의 단순한 빈 파일입니다.

* mysite/settings.py: 현재 Django project 의 환경/구성을 저장합니다. Django settings 에서 환경 설정이 어떻게 동작하는지 확인할 수 있습니다.

* mysite/urls.py: 현재 Django project 의 URL 선언을 저장합니다. Django 로 작성된 사이트의 “목차” 라고 할 수 있습니다.

* mysite/wsgi.py: 현재 project 를 서비스 하기 위한 WSGI 호환 웹 서버의 진입점 입니다.

***
당신의 Django project 가 제대로 동작하는지 확인해 봅시다. mysite 디렉토리로 이동하고, 다음 명령어를 실행하십시오.

"python manage.py runserver"

제대로 실행 됬을떄 커맨드라인의 출력

~~~~
Performing system checks...

System check identified no issues (0 silenced).

You have unapplied migrations; your app may not work properly until they are applied.
Run 'python manage.py migrate' to apply them.

February 14, 2017 - 15:50:53  # 현재 시간
Django version 1.10, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
~~~~

서버를 동작을 했으니 웹 브라우져에서  http://127.0.0.1:8000/ 를 통해 접속을 하면
“Welcome to Django”라는 텍스트가 띄워진 페이지를 볼 수 있습니다.

기본적으로 runserver 명령으로 내부 IP의 8000번 포트로 개발 서버를 띄우지만 포트를 변경 하고 싶으면 다음 명령어를 입력합니다. 만약 포트번호를 8080으로 바꾸고 싶으면

"python manage.py runserver 8080"

그리고 만약 서버 IP를 바꾸고 싶다면, 포트와 함께 전달해주면 됩니다. 네트워크 상의 다른 컴퓨터에게 내 작업물을 보여 줄때 유용합니다. 다음 명령어를 입력하시면 됩니다.

"python manage.py runserver 0.0.0.0:8000"

이제 작업을 시작하기 위한 환경(project)이 설치되었습니다. Django는 app의 기본 디렉토리 구조를 자동으로 생성할수 있는 도구를 제공합니다.

그렇다면 project와 app의 차이가 무엇일까요? app은 특정한 기능을 수행하는 웹 어플리케이션을 말합니다. proejct는 이런 특정 웹사이트를 위한 app들과 설정들을 합한것입니다. 그말은 project는 여러 개의 app을 포함 할수 있습니다.

그렇다면 이제 app을 생성해 봅시다. 간단한 설문조사 app을 만들어 봅시다. app을 생성하기 위해서는 manage.py가 존재하는 디렉토리에서 다음 명령어를 입력합니다. 

"python manage.py startapp polls"

polls라는 디렉토리가 생겼습니다

**최초의 소스 트리**

~~~~
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
~~~~
***