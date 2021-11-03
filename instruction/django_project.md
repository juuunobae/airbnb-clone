# Django Project
- 모듈화된 여러 개의 앱들로 구성된다.
- 앱 단위로 모듈화하면 개발 및 유지 보수가 효율적이게 되고, 모듈화된 앱은 다른 프로젝트에서 재활용할 수도 있다.

# 프로젝트 시작하기
## django document
- 프로젝트를 생성할 폴더에서 `django-admin startproject [mysite]` 명령어 실행

## 더 좋은 방법
- 프로젝트 폴더를 생성하고 그 폴더안(개발환경)에서 `django-admin startproject config` 명령어 실행
- config 폴더가 생성된다.
```

    |-- config
        |-- __init__.py
        |-- settings.py
        |-- urls.py
        |-- wsgi.py
    |-- manage.py

```
- 생성된 파일들을 위의 구조로 바꿔준다.

# Runtime Language
- 컴파일 언어는 컴파일러가 있어서 프로그램이 시작되기 전에 에러를 잡아내주지만, 파이썬은 런타임 언어이기 때문에 프로그램이 시작되고 에러가 있으면 프로그램이 

## python pep
-  파이썬 코드를 위한 스타일 가이드

## Linter
- 코드를 보고 에러가 생길부분을 미리 감지하여 알려주고 코드의 문법을 체크한다.
- flake8 사용
- 룰 변경하기 
```json

    // settings.json

    "python.linting.flake8Args": [],

```

## Formatter
- 코드를 보기 좋게 자동으로 수정해주는 것
- black 사용

# 프로젝트를 위한 파일
- \_\_init__.py
  - 파이썬에 필요한 파일
  - 해당 디렉토리를 패키지처럼 다루라고 알려주는 용도의 빈 파일이다.
  - 해당 디렉토리의 파일을 다른 곳에서 import 해서 사용할 수 있게 해준다.
- settings.py
  - 현재 장고 프로젝트의 환경 및 구성을 저장한다.
  - application을 만드는데 필요한 것들이 담겨있는 파일
  - 미들웨어, 템플릿, 패스워드 검사, 데이터베이스 등
- urls.py
  - 장고 프로젝트의 URL 선언을 저장한다.

# django 명령어
## 관리자 계정 만들기
- `python manage.py createsuperuser`
- 
## 서버 시작하기
- `python manage.py runserver`