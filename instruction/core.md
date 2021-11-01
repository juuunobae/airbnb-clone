# 재사용 파일
- 여러 application에서 공통으로 사용되는 데이터 필드들을 한 곳에 작성한 후 확장한다.
- Abstract model이라고 한다.

# Database
- abstract model은 확장하려고 만든 것이기 때문에 데이터베이스에 등록하지 않아도 된다.
```python

    class AbstractModel(models.Model):

        class Meta:
            abstract = True

```
- `Meta` 클래스에 `abstract = True`를 작성해주면 해당 model은 데이터베이스에 추가 되지 않는다.