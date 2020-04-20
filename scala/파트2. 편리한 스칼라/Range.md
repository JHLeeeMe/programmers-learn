# Create Range
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
