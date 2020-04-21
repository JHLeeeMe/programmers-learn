# 메서드 정의
- 마지막 값이 return 값
```scala
#!/usr/bin/env scala


object LearnScala {
  // 일반적인 메서드
  def add(x: Int, y: Int): Int = {
    return x + y  // return 키워드 생략가능 (scala doc에서는 생략하는걸 추천함)
  }

  // 메서드가 한 줄일 경우 중괄호 생략 가능
  def addWithoutBlock(x: Int, y: Int): Int = x + y

  def main(args: Array[String]): Unit = {
    println(add(1, 2))  // 3
    println(addWithoutBlock(1, 2))  // 3
  }
}
```

# 익명 함수
- 이름이 없는 함수
```scala
#!/usr/bin/env scala


object LearnScala {    
    // 메소드를 정의
    def add1(x:Int, y:Int) = x + y 
    
    // 익명함수를 add2상수에 넣음
    val add2 = (x:Int, y:Int) => x + y 
    
    // 익명함수를 정의하는 다른 방식
    val add3: (Int,Int) => Int = _ + _ 
    
    // 익명함수를 정의하는 또다른 방식(잘 사용 안함)
    val add4 = (_ + _): (Int,Int) => Int 
    
    def main(args: Array[String]): Unit = {
        // 모두 두 숫자를 더해주는 역할을 하므로 같은 결과를 출력
        println(add1(42,13)})  
        println(add2(42,13)})  
        println(add3(42,13)})  
        println(add4(42,13)})  
    }
}
```

```scala
#!/usr/bin/env scala


object LearnScala {
  // 매개변수로 받은 익명함수에 1과 2를 넣어 실행하는 메서드
  def doWithOneAndTwo(f: (Int, Int) => Int) = {
    f(1, 2)  // f(1, 2)의 결과가 return
  }

  def main(args: Array[String]): Unit = {
    // 명시적으로 타입 선언
    val call1 = doWithOneAndTwo((x: Int, y: Int) => x + y)

    // doWithOneAndTwo 메서드에서 이미 매개변수 타입을 정했으므로 생략
    val call2 = doWithOneAndTwo((x, y) => x + y)

    // _ 를 써서 더 간추림
    val call3 = doWithOneAndTwo(_ + _)

    println(call1, call2, call3)  // (3, 3, 3)
  }
}
```
