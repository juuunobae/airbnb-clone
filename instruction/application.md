# Application
- project를 구성하는 특정한 기능을 제공하는 패키지이다. 
- 하나의 디렉토리가 하나의 앱이라고 생각하면 된다.
- 독립되어 쓸 수 있는 모듈이다.
- app을 통합하여 하나의 project를 만든다.
  
# App 생성하기
- app 이름은 항상 복수형이여야 한다.
- `django-admin startapp [app_name]` 
- app을 생성했을 때 해당 디렉토리에 생성되는 파일들의 이름은 절대 변경하면 안된다.

# App 구성 파일
## admin.py
- 관리자 페이지에 보여지게 될 화면의 구성을 설정하는 파일
## models.py
- 데이터베이스 스키마를 작성하는 파일
## views.py
- 앱의 로직을 넣는 파일
- 모델에서 필요한 정보를 받아와 template에서 전달하는 역할을 한다.
## urls.py
- URLConf를 생성하기 위해 생성하는 파일