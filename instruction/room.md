# Data Field 작성
- 값이 정해져 있는 데이터필드를 작성할 때 두 가지 방법이 있다.

## choices
- choices 방법으로 작성하면 만약 나중에 그 값이 변경될 때나 추가될 때 프로그래머만이 값을 변경할 수 있다.

## relationship
- relationship 방법으로 작성하면 프로그래머가 아닌 관리자나 다른 사람도 쉽게 값을 변경하거나 추가할 수 있다.
- 해당 필드의 모델을 새로 생성해 필요한 모델과 연결해준다.
  - models.ForeignKey(), models.ManyToMany()