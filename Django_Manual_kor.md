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
다음으로 Django에서 기본적으로 지원해주는 다음 app들을 지원해 줍니다.

~~~~
INSTALLED_APPS = [
'django.contrib.admin', 관리자 사이트
'django.contrib.auth',  인증 시스템
'django.contrib.contenttypes', 컴텐츠 타입을 위한 프레임 워크
'django.contrib.sessions',  세션 프레임워크
'django.contrib.messages',  메세징 프레임워크
'django.contrib.staticfiles',  정적 파일을 관리하는 프레임 워크
]
~~~~

위의 기본적으로 지원해주는 app들은 기본적으로 하나 이상의 데이터베이스 테이블을 사용합니다. 그래서 테이블을 미리 만들어 주어야 합니다. 다음 명령을 실행해주세요
~~~~
python manage.py migrate
~~~~
migrate 명령은 INSTALLED_APPS의 설정을 탐색하여, DBMS 설정과 app에 사용되는 데이터베이스 테이블을 생성합니다. 어떤 내용이 생성됬는디 확인하고 싶다면 데이터 베이스 클라이언트로 접속하여 확인 할수 있습니다.

만약 기본적으로 제공되는 app들 중 사용하기 싫은 app이 있으시다면 주석처리 해주시거나 삭제하시고 migrate명령을 해주시면 삭제된 app을 제외하고 migrate명령이 실행 될 겁니다.

***
이제 모델을 만들어 봅시다. Django는 모델을 한곳에서 관리할 수 있도록 지원해줍니다.

우리가 만드는 단순한 설문조사(poll) 앱을 위해 Question 과 Choice 라는 두개의 모델을 만들어 보겠습니다. Question 은 질문(question) 과 발행일(publication date) 을 위한 두개의 필드를 가집니다. Choice 는 선택지(choice) 와 표(vote) 계산을 위한 두개의 필드를 가집니다. 각 Choice 모델은 Question 모델과 연관(associated) 됩니다.

**경로 : polls/models.py**

~~~~
from django.db import models

class Question(models.Model):
question_text = models.CharField(max_length=200)
pub_date = models.DateTimeField('date published')


class Choice(models.Model):
question = models.ForeignKey(Question, on_delete=models.CASCADE)
choice_text = models.CharField(max_length=200)
votes = models.IntegerField(default=0)
~~~~

각 모델은 django.db.models.Model 이라는 클래스의 서브클래스로 표현됩니다.
각 모델은 여러 개의 클래스 변수를 가지고 있으면, 각각의 클래스 변수들은 모델의 데이터베이스 필드를 나타냅니다.

데이터베이스의 필드들은 Field 클래스의 인스턴스로 표현됩니다. 각 옵션들을 부여 할수 있는데 이것을 이용하여 최대길이(max_length) 지정,  default로 기본값 지정, 첫번째 인수를 전달하여 사람이 이해하기 쉬운 이름을 지정 할수도 있습니다.
ForeignKey 를 사용한 관계설정에 대해 설명하겠습니다. 이 예제에서는 각각의 Choice 가 하나의 Question 에 관계된다는 것을 Django 에게 알려줍니다. Django 는 다-대-일(many-to-one), 다-대-다(many-to-many), 일-대-일(one-to-one) 과 같은 모든 일반 데이터베이스의 관계들를 지원합니다.
그리고 이 필드의 이름들은 데이터 베이스에서 속성명으로 사용됩니다.

CharField : 문자 필드
DateTimeField : 날짜시간 필드

app 을 현재의 project 에 포함시키기 위해서는, app 의 구성 클래스에 대한 참조를 INSTALLED_APPS 설정에 추가시켜야 합니다. 다음과 같이 코드를 작성해 주세요

**경로 : mysite/settings.py**

~~~~
INSTALLED_APPS = [
'django.contrib.admin',
'django.contrib.auth',
'django.contrib.contenttypes',
'django.contrib.sessions',아
'django.contrib.staticfiles',
'polls',   # 이부분의 app의 이름을 추가하여 준다.
]
~~~~

그후 다음 명령어를 실행해 주세요
~~~~
"python manage.py makemigrations polls"
~~~~

그러면 명령창에 이렇게 띄워질 것입니다.

~~~~
Migrations for 'polls':
polls/migrations/0001_initial.py:
- Create model Choice
- Create model Question
- Add field question to choice
~~~~

makemigrations 을 실행시킴으로서, 당신이 모델을 변경시킨 사실과(이 경우에는 새로운 모델을 만들었습니다) 이 변경사항을 migration 으로 저장시키고 싶다는 것을 Django 에게 알려줍니다. migrations는 Django가 모델의 변경사항을 저장하는 방법으로 파일로 존재합니다.
polls/migrations/0001_initial.py 파일을 보면 새롭게 저장된 모델에 대한 migrations를 볼수 있습니다. 파일로 볼수 있고 명령어를 치지 않고 그냥 그 파일에서 수동으로 수정할 수도 있습니다.

***
이제 다음 명령으로 데이터베이스에 모델과 관련된 테이블을 생성해봅시다.
~~~~
python manage.py migrate
~~~~
migrate는 아직 적용되지 않은 migration들을 실행합니다. migration은 매우 기능이 강력하여 project를 개발할때 직접 데이터베이스에 손대지 않고도 모델을 변경하게 해줍니다.

