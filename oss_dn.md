첫 번째 뷰를 작성해볼까요.

**경로 : polls/view.py**

다음 코드를 작성해봅시다.

~~~~
from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
~~~~

Django에서 가장 간단한 형태의 view입니다. view를 호출하려면 이와 연결된 URL이 있어야 하는데, 이를 URLconf가 사용되는데 polls 디렉토리에서 URLconf를 생성하려면, urls.py라는 파일을 생성해야 합니다. 

**경로 : polls/urls.py**

~~~~
from django.conf.urls import url

from . import views

urlpatterns = [
    url(r'^$', views.index, name='index'),
]
~~~~

다음단계에서는 project 최상단의 URLconf에서 polls.urls 모듈을 바라보게 설정합니다.
mysite/urls.py 파일을 열고, django.conf.urls.include 를 추가합니다. 그리고 다음과 같이 코드를 추가해주세요. 

**경로 : mysite/urls.py**

~~~~
from django.conf.urls import include, url
from django.contrib import admin

urlpatterns = [
    url(r'^polls/', include('polls.urls')),
    url(r'^admin/', admin.site.urls),
]
~~~~

include() 함수는 URLconf를 참조할 수 있도록 도와줍니다. 위의 코드는 쉽게 말하면 project안에 app의 urls.py에 접근할 수 있도록 도와주는 역활을 합니다.

***
데이터베이스를 설정해봅시다. 
Django의 기본적인 SQLite로 사용하도록 구성되어 있습니다. 데이터베이스를 처음 경험한다면 그냥 그대로 사용하시고 나는 다른 데이터베이스를 사용하고 싶으시다면 별도로 DBMS를 설치하시고 아래와 같이 코드를 작성해주시면 됩니다.

~~~~
'django.db.backends.sqlite3',       SQLite
'django.db.backends.postgresql',    PostgreSQL
'django.db.backends.mysql',         MySQL
'django.db.backends.oracle'.        Oracle
~~~~

**경로 :  mysite/settings.py**

기본 코드
~~~~
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}

~~~~

DBMS를 PostgreSQL로 바꾸고 싶다면 아래와 같이 코드를 작성해주세요

~~~~
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': '데이터베이스의 이름',
        'USER': '데이터베이스 계정',
        'PASSWORD': '계정 비밀번호',
        'HOST': '127.0.0.1',
        'PORT': '',
    }
}
~~~~