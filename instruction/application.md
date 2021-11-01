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

### 설정 옵션
- admin 페이지의 구성이나 요소를 변경할 수 있다.

#### fieldSets
- 필드를 카테고리화 하여 보여준다.
```python

    

```

#### list_display
- 리스트에서 어떤 필드를 보여줄 지 결정

#### list_filter
- 리스트를 필터링 할 옵션들을 만든다.
- 필터박스를 만든다.


## models.py
- 데이터베이스 스키마를 작성하는 파일

### dataField
- 데이터베이스에 필드를 추가한다.
`[필드명] = models.[필드종류]([속성])`
- 속성
  - default
    - 데이터베이스에 저장되는 기본 데이터 값
  - null
    - True & False
    - 데이터베이스에 null값을 허용할 것인가?
  - blank
    - True & False
    - form 작성 시 빈값을 허용할 것인가?

#### models.CharField
- 한줄 텍스트 필드
- 속성
  - choices
    - 값을 선택할 수 있게 해준다.
        ```python

            [데이터베이스에 저장할 값] = ''
            [데이터베이스에 저장할 값] = ''

            [Choices명] = (
                ([데이터베이스에 저장할 값], '[필드의 form에 보여질 이름]'),
                ([데이터베이스에 저장할 값], '[필드의 form에 보여질 이름]'),
            )

            models.CharField(choices=[Choices명])

        ```
  - max_langth
    - 텍스트 길이 설정

#### models.TextField
- 여러줄 텍스트 필드

#### models.ImageField
- 이미지 필드
- Pillow
  - 이미지를 처리하는 파이썬 라이브러리
  - `pipenv install pillow`

#### models.DateField(), .DateTimeField()
- DateField()
  - 날짜 필드
- DateTimeField()
  - 날짜, 시간 필드

#### models.BooleanField()
- 체크박스 필드
  - True & False

## views.py
- 앱의 로직을 넣는 파일
- 모델에서 필요한 정보를 받아와 template에서 전달하는 역할을 한다.

## urls.py
- URLConf를 생성하기 위해 생성하는 파일

# App 연결하기 
- 생성한 앱은 settings.py의 `INSTALLED_APPS`에서 추가 해주어야 한다.
```python 

    INSTALLED_APPS = [
        '[app name].apps.[class name in the apps.py]'
    ]
    # apps name = app 디렉토리의 apps.py에 있는 class 이름
    
```