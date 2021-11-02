# Relationship
- 모델과 모델 사이의 관계

## Foreign Key
- 일대다 관계
- 하나의 모델과 여러 모델간의 관계를 열결해줄 때 사용된다.
- 두 model중 여러개가 연결될 model에 Foreign Key field 작성
- 예를 들어 한 명의 유저가 여러 게시글을 작성하지만 여러 유저가 하나의 게시글을 작성하지는 않는다. 이 때 게시글의 model에 Foreign Key field를 작성해준다.
```python 

    [필드명] = models.ForeignKey("[연결할 모델명]", [옵션])

```
- 옵션
  - on_delete
    - 연결되어 있는 모델이 삭제 되었을 때 해당 모델은 어떻게 할 것인지 설정
    - models.CASCADE: 연결되어 있는 모델 전부 같이 삭제된다.
    - models.PROTECT: 해당 모델을 삭제해야지 연결되어 있는 모델을 삭제할 수 있다.
    - models.SET_NULL: 
    - models.SET_DEFAULT: 

## Many To Many
- 다대다 관계
```python 

    [필드명] = models.ManyToMany("[연결할 모델명]")

```

## 객체에 접근
- Foreign Key로 연결되어 있는 모델 객체의 필드에 접근하여 사용할 수 있다.

# Query Set
- 데이터베이스에서 전달받은 모델의 객체 리스트이다.
- 데이터베이스로부터 데이터를 읽고, 필터를 걸거나 정렬을 할 수 있다.
- `[모델명].objects`: objects는 모델 manager이다.
  - `.all()`: 모델의 모든 데이터를 가지고 오고, queryset 객체를 리턴한다.
  - `.get([옵션])`: 특정 데이터를 리턴한다.

## 역참조
- 자신을 참조하고 있는 모델을 역으로 참조 해서 사용할 수 있다.
- [모델명].[역참조모델명]_set.all()
- `ForeignKey(related_name='')`: 역참조할 때 쓰이는 모델이름을 설정할 수 있다. 

## Managers
- 데이터베이스와 장고 모델의 사이에서 질의연산의 인터페이스 역할을 한다.
- 데이터베이스로부터 요소를 가지고 오게 해준다.
