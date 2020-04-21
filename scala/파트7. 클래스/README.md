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
    // ① 단순한 클래스
    val p1 = new Person1("중기", "송")
    //p1.fname과 p1.lname의 값을 외부에서 가져올 수 없습니다.        
        
    // ② 메소드를 가지는 클래스
    val p2 = new Person2("혜교", "송")
    // 이 경우에도 p2.fname과 p2.lname의 값을 외부에서 가져올 수는 없습니다.
    // 정의된 greet 메소드를 출력합니다.
    println(s"② ${p2.greet}")          
       
    // ③ public한 read only(val) fullname을 가지는 클래스
    val p3 = new Person3("구", "진")
    println(s"③ ${p3.fullName}님께 인사합니다. ${p3.greet}")        
      
    // ④ val fname과 var lname을 가지는 클래스
    val p4 = new Person4("지원", "Kim") {  
        override def toString = s"$lname$fname"
    }  
    // val로 선언된 p4.fname과 var로 선언된 p4.lname을 외부에서 읽을 수 있음
    println(s"④ ${p4.lname}${p4.fname}") 
      
    // ⑤ Person4클래스를 이용해서 객체를 생성하지만, 해당 객체의 toString메소드만 오버라이드
    val p5 = new Person4("시진", "유") {  
        override def toString = s"$lname$fname"
    }  
    println(s"⑤ $p5") // 오버라이드된 toString형태로 출력
  }
}

-------------------------------------------------------------------------
Output:

② 송혜교님 안녕하세요!
③ 진구님께 인사합니다. 진구님 안녕하세요!
④ Kim지원
⑤ 유시진
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
