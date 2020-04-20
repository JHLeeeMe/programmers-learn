# 반복문
- 스칼라는 ```while```, ```for``` 제공
0 부터 10 까지의 합을 구해보자.
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    // 1. while
    var i, sum = 0
    while (i < 11) {
      sum += i
      i += 1
    }
    println(sum)  // 55

    // 2. for
    sum = 0
    for (i <- 0 to 10) {
      sum += i
    }
    println(sum)  // 55

    // 3. 가장 스칼라스러운 코드
    sum = (0 to 10).sum

    println(sum)  // 55
  }
}
```
# 중첩된 for
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    for (a <- 1 to 3) {
      for (b <- 10 to 12) {
        println(a, b)
      }
    }

    // same As
    //for (a <- 1 to 3; b <- 10 to 12) {
    //  println(a, b)
    //}

    // same As
    //for {
    //  a <- 1 to 3
    //  b <- 10 to 12
    //} println(a, b)

    for {
      a <- 1 to 3
      b <- 10 to 12
    } yield { 
      (a, b) 
    }
  }
}

-----------------------------------------------
Output:

(1,10)
(1,11)
(1,12)
(2,10)
(2,11)
(2,12)
(3,10)
(3,11)
(3,12)

Vector((1,10), (1,11), (1,12), (2,10), (2,11), (2,12), (3,10), (3,11), (3,12))
```

# if
- Java나 C와 거의 같다.
- if문도 수식이므로 삼항 연산자를 대신할 수 있다.
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    if (true)
      println("괄호를 생략할 수 있다.")

    if (1 + 1 == 2) 
      println("물론")
      println("여러 줄도 마찬가지")

    // 삼항 연산자대신 이렇게 쓸 수 있음.
    if (true) println("Hi") else println("else....................")
  }
}
```
