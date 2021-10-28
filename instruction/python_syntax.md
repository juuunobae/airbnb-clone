# arguments
## *args
- 여러개의 인자를 받는다.
- 넘어온 인자를 받아 배열로 만든다.

```python
    def plus(*args):
    result = 0
    for number in args:
        result += number
    print(result)

    plus(1,2,3,4,5,6,7,8,9,10)
```

# keyword arguments
## **kwargs
- 인자를 키워드가 있는 값을 받는다.
- 넘어온 인자를 받아 딕셔너리로 만든다.

```python
    def plus(**kwargs):
    print(kwargs)

    plus(a=1, b=2, c=3)
```

# Object Oriented Programming
## class
- 설계도 같은 것
- class를 생성하면 __init__ method가 자동으로 샐행된다.

```python
    class Car():

    def __init__(self, *args, **kwargs):
        self.wheels = 4
        self.doors = 4
        self.windows = 4
        self.seat = 4
        self.color = kwargs.get('color', 'black')
        self.price = kwargs.get('price', '2000')

    def start(self):
        print(self.doors)
        print('I started')

    def __str__(self):
        return f'Car with {self.doors}'
```
> class에서 method를 생성하면 파이썬 자체에서 파리미터로 self를 부여한다.</br>
> 이 self는 해당 method를 호출하는 instance 자신을 가리키는 것</br>
> javascript의 this 같은 것

## instance
- class를 기반으로 만든 결과물
- instance를 호출하면 class의 __str__ method를 호출해 해당 instance의 정보를 문자열로 반환한다.
- 필요에 의해 __str__을 오버라이딩하여 사용할 수 있다.

```python

    genesis_g80 = Car(color='red', price=3000)
    print(genesis_g80.color, genesis_g80.price)
```

# Extending Classes
```python
    class Convertible(Car):

    # __init__ 확장 시키기
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        # super는 부모클래스 가리킨다(여기서는 Car 클래스가 된다.)
        # 부모 클래스의 __init__ method를 호출해 부모클래스에 정의 되어 있는 변수들을 사용하고, 확장할 수 있다.
        # 인자를 넣어주어야 한다.
        self.time = kwargs.get('time', 10)

    def take_off(self):
        return 'taking off'

    def __str__(self):
        return f'Car with no roof'

    bmw_i8 = Convertible()
    print(bmw_i8)
    print(bmw_i8.take_off())
    print(bmw_i8.color)

```