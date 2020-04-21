# 클래스
- 파라미터 부분이 생성자

### Person1.scala
- ```fname```, ```lname``` 이라는 private 상수가 생김 (getter, setter 안생김)
```scala
#!/usr/bin/env scala


// 단순 클래스
class Person1(fname: String, lname: String)
```

### Person2.scala
- ```greet```메서드 정의
```scala
#!/usr/bin/env scala


class Person2(fname: String, lname: String) {
  // public한 메서드
  def greet = s"${lname}${fname}님 안녕하세요!"
}
```

### Person3.scala
- public한 val(read only) 필드
```scala
#!/usr/bin/env scala


class Person3(fname: String, lname: String) {
  // public한 val(read only) 필드
  val fullName = s"${lname}${fname}"

  // public한 메서드
  def greet = s"${lname}${fname}님 안녕하세요!"
}
```

### Person4.scala
- 생성자에 ```var``` or ```val```키워드를 명시하면 자동으로
- ```val```: getter
- ```var```: getter, setter
- 메서드가 생성된다.
```scala
#!/usr/bin/env scala


class Person4(val fname: String, var lname: String)
```

### LearnScala.scala
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
  }
}
```

# getter와 setter
- 스칼라는 private이 아닌 모든 ```var``` 멤버에 getter, setter를 자동으로 정의함
- 직접 정의
```scala
#!/usr/bin/env scala


class Person() {
  private var _age = 0
  var name = ""

  // Getter
  def age = _age

  // Setter
  def age_=(value: Int): Unit = {
    _age = value
  }
}
```
