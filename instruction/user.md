# Custom User
- 장고에서 User를 기본으로 제공해주지만 따라 User를 더 확장하거나 변경해서 사용할 수 있다.

## User app
- 장고는 유저 앱이 미리 주어져있다.
- 장고에서 제공하는 유저 모델이 아닌 커스텀 유저 모델을 사용하기 위해 `AUTH_USER_MODEL` 값을 설정해주어야 한다.
```python

    # settings.py

    AUTH_USER_MODEL = 'myapp.MyUser'

```

## Models
- 장고에서 기본으로 제공하는 User를 확장하기 위해 AbstractUser를 상속받는다.
```python

    # models.py

    from django.contrib.auth.models import AbstractUser
    from django.db import models

    # Create your models here.


    class User(AbstractUser):
        pass
    
```
  - `from django.contrib.auth.models import AbstractUser`
    - 기존의 admin user 테이블에 있던 열들을 전부 유지한 채 새로운 열을 추가 할 수 있다.

## Admin
- Custom user admin 등록해서 사용
- 장고에서 기본으로 제공하는 user admin을 사용하기 위해 UserAdmin을 상속받는다.
```python

    from django.contrib import admin
    from django.contrib.auth.admin import UserAdmin
    from . import models

    # Register your models here.

    @admin.register(models.User)
    class CustomUserAdmin(UserAdmin)
        
        fields = UserAdmin.fieldsets
    
```
    - CustomUserAdmin으로 해당 user model을 사용하고 컨트롤할 수 있다.
    - `@admin.register(models.User)`가 admin class 위에 있어야 한다.
- `UserAdmin.fieldsets`
  - 장고에서 기본으로 제공하는 user 필드를 불러온다.