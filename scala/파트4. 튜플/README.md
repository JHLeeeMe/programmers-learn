# Tuple
- 담고있는 엘러먼트 수에 따라 Tuple1 클래스부터 Tuple22 까지 존재.
- Tuple 값에 접근하기위해 ```_1, _2, ..., _22```메서드가 존재.
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    val t1 = new Tuple3(1, "hello", true)
    val t2 = (1, "hello", true)

    println(t1)  // (1, "hello", true)
    println(t2)  // (1, "hello", true)

    var numbers = (1, 2, 3, 4)
    val sum = numbers._1 + numbers._2 + numbers._3 + numbers._4

    println(sum)  // 10
  }
}
```

# 여러개의 값 리턴
- 튜플을 이용해서 한번에 여러 개의 값을 리턴받을 수 있으며, 그 값을 한번에 여러 변수 및 상수에 넣을 수 있다.
```scala
#!/usr/bin/env scala

object LearnScala {
  def swap(x: String, y: String): String = (y, x)

  def main(args: Array[String]): Unit = {
    val (a, b) = swap("hello", "world")

    println(a)  // "world"
    println(b)  // "hello"
    println(a, b)  // (world, hello)
  }
}
```

# 값 넣기
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    var (x, y, z, c, python, java) = (1, 2, 3, true, false, "no!")
    
    println(x, y, z, c, python, java)  // (1, 2, 3, true, false, no!)
  }
}
```
