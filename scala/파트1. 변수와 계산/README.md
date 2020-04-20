# 연산자
- ```+```메서드 호출
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    println( 1 + 2 )  // 3
    println( (1).+(2) )  // 3
    println( 1.+(2) )  // 3
  }
}
```

# 변수와 상수
- 변수: ```var```
- 상수: ```val```
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    var x = 1 + 2
    x = 3 * 4
    println(x)  // 12

    val y = 1 + 2
    println(y)  // 3

    // 한 번에 여러개의 변수 선언 가능
    var a, b, c = 5
    println(a)  // 5
    println(b)  // 5
    println(c)  // 5
  }
}
```

# 변수 출력
- println
- printf
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    var x = 10
    var y = 1

    // 1. println
    println(x + " is bigger than " + y)  // "10 is bigger than 1"

    // 2. 문자열 앞에 s를 쓰면 $를 쓰고 변수이름을 바로 쓸 수 있음.(like bash script)
    println(s"$x is bigger than $y")  // "10 is bigger than 1"

    // 3. 수식 입력 가능 ${ }
    println(s"$x + $y = ${x+y}")  // "10 + 1 = 11"

    // 4. printf
    // java.lang.* 자동으로 import
    printf("Pi is %f", Math.PI)
  }
}
```
