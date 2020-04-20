# Array
- ```Array(e1, e2, ...)```
- ```Mutable```
- 자바의 배열과 대응하는 개념
- java: ```int[]``` == scala: ```Array[Int]```
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    // 1. Array[Int]
    val array1 = Array(1, 2, 3)  // array1: Array[Int] = Array(1, 2, 3)

    // 2. Array[Any]
    val array2 = Array("a", 2, true)  // array2: Array[Any] = Array("a", 2, true)

    // 3. 배열의 값 읽고 쓰기
    val itemAtIndex0 = array1(0)
    array1(0) = 4

    println(itemAtIndex0)  // 1
    array1  // array1: Array[Int] = Array(4, 2, 3)

    // 값으로 index찾기
    println(array2.indexOf("a"))  // 0

    val a = Array(1, 2, 3)
    val b = List(4, 5, 6)
    // 4. '++' 연산자: 앞의 데이터형으로 이어붙임 
    a ++ b  // Array(1, 2, 3, 4, 5, 6)
    
    //    '+:' 연산자: 뒤의 데이터의 첫번째 값에 앞의 데이터를 넣고 뒤의 데이터형으로 감싸서 리턴
    a +: b  // List(Array(1, 2, 3), 4, 5, 6)

    //    ':+' 연산자: 앞의 데이터의 마지막 값에 뒤의 데이터를 넣고 앞의 데이터형으로 감싸서 리턴
    a :+ b  // Array(1, 2, 3, List(4, 5, 6)

    // 5. 다른 값만 가져오기 (diff)
    val diffArray = Array(1, 2, 3, 4).diff(Array(2, 3))
    println(diffArray)  // Array(1, 4)

    val personArray = Array(("솔라", 1), ("문별", 2), ("휘인", 3))
    // 6. find
    // 조건에 맞으면 검색 중단, getOrElse는 일치하는 값이 없을 경우 넘겨줄 기본 값
    // getOrElse가 없으면 기본값은 None
    def findByName(name: String): (String, Int) = personArray.find(_._1 == name).getOrElse(("화사", 4))

    val findSolar = findByName("솔라")
    val findSun = findByName("태양")

    println(findSolar)  // ("솔라", 1)
    println(findSun)  // ("화사", 4)
    
  }
}
```

# List
- ```List(e1, e2, ...)```
- 기본이 ```scala.collection.immutable.List```
- 기본이 ```Linked list```
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    // List[Any] (기본 리스트, Immutable)
    val list = List("a", 1, true)

    // 1. 값을 읽어올 수는 있지만
    val firstItem = list(0)
    // 변경 x
    // list(0) = "b"
    println(firstItem)  // "a"

    // 2. 배열과 연산자 사용은 같음
    val concatenated = 0 +: list ++ list :+ 1000
    println(concatenated)  // List(0, a, 1, true, a, 1, true, 1000)

    // Nil 은 빈 리스트이다. List()
    // 아래는 Int타입을 이어 List에 담는 예 (Int에는 +: 메서드가 없으므로 Nil을 붙여주어야 함)
    // 1 +: 2  ===> error: value +: is not a member of Int
    // 1 +: true  ===> error: value +: is not a member of Boolean
    val test = 1 +: 2 +: 3 +: Nil  
    println(test)  // List(1, 2, 3)

    // 3. diff
    val diffList = List(1, 2, 3, 4) diff List(2, 3)
    println(diffList)  // List(1, 4)

    // 4. 배열의 find와 같은 동작
    val personList = List(("솔라",1), ("문별",2), ("휘인",3))
    
    def findByName(name: String) = personList.find(_._1 == name).getOrElse(("화사", 4))

    val findSolar = findByName("솔라")
    val findSun = findByName("태양")

    println(findSolar, findSun)  // (솔라, 1), (화사, 4)
  }
}
```

# Set
- ```Set(e1, e2, ...)```
- 기본이 ```scala.collection.immutable.Set```
- 엘러먼트의 수에 따라 Set1, Set2, Set3, Set4
- 4를 초과시 ```HashSet```으로 구현됨
- 집합과 대응되는 개념, 같은 값 추가시 기존 값을 덮어씀.
- 순서 보장x
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    // 1. 중복 x 
    val set1 = Set(1, 2, 2, 3, 3, 3)
    println(set1)  // Set(1, 2, 3)

    // 2. 값이 있는지 체크
    val oneExists = set1(1)
    val fourExists = set1(4)
    println(oneExists, fourExists)  // true, false

    val set2 = Set("a", 2)
    // 3. set을 이어붙이면 중복된 내용이 덮어써진 새로운 Set 생성
    val concatenated = set1 ++ set2
    println(concatenated)  // Set(1, 2, 3, "a")

    // 4. diff
    val diffSet = Set(1, 2, 3, 4) diff Set(2, 3)
    println(diffSet)  // Set(1, 4)

    // 5. find (역시나 똑같이 작동)
    val personList = Set(("솔라",1), ("문별",2), ("휘인",3))
    
    def findByName(name: String) = personList.find(_._1 == name).getOrElse(("화사", 4))

    val findSolar = findByName("솔라")  // return값은  
    val findSun = findByName("태양")    //   Tuple2[String, Int]이다.

    println(findSolar._1, findSun_2)  // "솔라", 4
  }
}
```

# Map

# Array/List/Set/Map의 타입

# 변경할 수 있는(Mutable) Collection

# 변경할 수 없는(Immutable) Collection에서의 var와 val

