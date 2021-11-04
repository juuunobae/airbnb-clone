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

### admin function
- 어드민 클래스 안에 함수를 생성하고 사용할 수 있다.
- 어드민 페이지에서만 사용할 수 있다.
- 어드민 함수는 `(self, obj)` 두개의 파라미터를 받는다.
  - self: 해당 아드민 클래스를 가리킨다.
  - obj: 해당 모델 객체를 가리킨다, 데이터베이스에서의 행(row)
    - .file: obj class의 내부를 보여준다. 여러 메소드들이 내장되어 있다.

### Inline Admin class
- ForeignKey로 가리키고 있는 모델의 어드민 페이지에서 해당 모델을 보여지게 하는 것
- 두 종류의 class가 있고, 보여지는 화면이 다르다.
#### admin.TabularInline
#### admin.StackedInline
```python

  # models.py
  class Photo(core_models.TimeStampeModel):

      """Photo Models Definition"""

      room = models.ForeignKey("Room", related_name="photos", on_delete=models.CASCADE)


  # admin.py
  class PhotoInline(admin.TabularInline):

      model = models.Photo

  class RoomAdmin(admin.ModelAdmin):

    inlines = (PhotoInline,)

```
- 위의 코드로 예를 들어보면 Photo 모델이 Room 모델을 ForeignKey로 연결하고 있고, RoomAdmin 페이지에서 PhotoAdmin을 보여지게 한다.

### 설정 옵션
- admin 페이지의 구성이나 요소를 변경할 수 있다.

#### class Meta:
- 모든 모델 내에 있는 class
- verbose_name_plural = ""
  - django는 admin 페이지에 모델 객체의 이름을 보여줄 때 끝에 s를 붙혀준다.
  - 보여지는 모델 객체 이름을 복수형으로 표시한다.
  - 이 옵션을 지정하지 않으면 verbose_name에 s를 붙힌다.
- verbose_name = ""
  - django는 admin 페이지에 모델 객체의 이름을 보여줄 때 끝에 s를 붙혀준다.
  - 보여지는 모델 객체 이름을 단수형으로 표시한다.
  - 이 옵션을 지정하지 않으면 모델 클래스 이름을 소문자로 변경한다.
- ordering = ["created", "-name"]
  - 순서를 변경할 수 있다.

#### fieldSets
- 필드를 카테고리화 하여 보여준다.
```python

    fieldsets = (
        (
            "[카테고리명]",
            {
                "classes":('[옵션명]'),
                "fields": (
                    "[필드명]",
                ),
            },
        ),
        (
            "[카테고리명]",
            {
                "classes":('[옵션명]'),
                "fields": (
                    "[필드명]",
                ),
            },
        ),
    )

```

#### list_display
- 리스트에서 어떤 필드를 보여줄 지 결정

#### list_filter
- 리스트를 필터링 할 옵션들을 만든다.
- 필터박스를 만든다.
  
#### ordering
- list 정렬
- 먼저 적는 순으로 우선정렬
  
#### search_fields
- 검색바를 만들고 검색 설정을 할 수 있다.
- ForeignKey에 접근하는 방법
  - `"[연결된 모델 객체명]__[연결된 모델 객체에서 사용할 fields명]"`

#### filter_horizontal
- 다대다 관계의 필드가 보여지는 방법을 바꾼다.

## models.py
- 데이터베이스 스키마를 작성하는 파일

### model function
- 모델의 데이터들을 계산하거나 변경이 필요할 때 models class에 생성하는 사용하는 함수
- 어드민 페이지 뿐 아니라 프론트엔드에도 보여지게 할 수 있다.

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
- 속성
  - upload_to = ''
  - MEDIA_ROOT 폴더안의 어떤 폴더에 이미지를 저장할 것인지 설정

#### models.DateField(), .DateTimeField()
- DateField()
  - 날짜 필드
- DateTimeField()
  - 날짜, 시간 필드
- 속성
  - auto_now_add=True
    - model이 처음 생성될 때의 시간을 기록해준다.
  - auto_now=True
    - model이 업데이트 될 때마다 그 때의 시간을 기록해준다.

#### models.BooleanField()
- 체크박스 필드
  - True & False

#### raw_id_fields
- relationship으로 연결된 필드를 검색해서 사용할 수 있는 화면으로 바뀐다.
- 해당 필드의 데이터들이 많아졌을 때 사용하면 유용하다.

## views.py
- 앱의 로직을 넣는 파일
- 모델에서 필요한 정보를 받아와 template에서 전달하는 역할을 한다.

## urls.py
- URLConf를 생성하기 위해 생성하는 파일
## URLconfig
- urlpatterns에 URL 경로를 추가


# App 연결하기 
## Startapp
- 생성한 앱은 settings.py의 `INSTALLED_APPS`에서 추가 해주어야 한다.
```python 

    INSTALLED_APPS = [
        '[app name].apps.[class name in the apps.py]'
    ]
    # apps name = app 디렉토리의 apps.py에 있는 class 이름
    
```

## Third Party Apps
- 장고 외부 라이브러리이다.
- `settings.py`의 `THIRD_PARTY_APPS = []`에 작성하고 사용한다.
