# Range
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    // to: 마지막을 포함
    val range1 = 1 to 10
    println(range1)  // scala.collection.immutable.Range = Range 1 to 10

    // until: 마지막 미포함
    val range2 = 1 until 10
    println(range2)  // scala.collection.immutable.Range = Range 1 until 10

    // by: 건너 뛰기
    val range3 = 1 until 10 by 3
    println(range3)  // scala.collection.immutable.Range = Range 1 until 10 by 3

    // toList: List로 변경
    println(s"${range1.toList}")  // List(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

    // filter: 조건에 맞는것만 Vector 타입으로 모아서 return
    val moreThan4 = range1.filter(_ > 4)
    println(s"$moreThan4")  // Vector(5, 6, 7, 8, 9, 10)

    // map: 생략
    val doubleIt3 = range1.map((x: Int) => x * 2)
    val doubleIt2 = range1.map(x => x * 2)
    val doubleIt1 = range1.map(_ * 2)
    println(doubleIt3)  // Vector(2, 4, 6, 8, 10, 12, 14, 16, 18, 20)
    println(doubleIt2)  // Vector(2, 4, 6, 8, 10, 12, 14, 16, 18, 20)
    println(doubleIt1)  // Vector(2, 4, 6, 8, 10, 12, 14, 16, 18, 20)
  }
}
```

# 숫자 다루기
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    val num = -5
    val numAbs = num.abs  // 절댓값
    val max5or7 = numAbs.max(7)  // 5(numAbs)와 7 사이 최댓값
    val min5or7 = numAbs.min(7)  // 5(numAbs)와 7 사이 최솟값

    println(num)  // -5
    println(numAbs)  // 5
    println(max5or7)  // 7
    println(min5or7)  // 5
  }
}
```

# 문자 다루기
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    // 1. reverse: 뒤집기
    val reverse = "Scala".reverse
    println(reverse)  // "alacS"

    // 2. capitalize: 첫글자를 대문자로
    val cap = "scala".capitalize
    println(cap)  // "Scala"

    // 3. *: 반복
    val multi1 = "Scala! " * 7
    val multi2 = "Scala! ".*(7)
    println(multi1)  // "Scala! Scala! Scala! Scala! Scala! Scala! Scala!"
    println(multi2)  // "Scala! Scala! Scala! Scala! Scala! Scala! Scala!"

    // 4. toInt: 정수로 변환
    val int = "123".toInt
    println(int)  // 123
  }
}
```
