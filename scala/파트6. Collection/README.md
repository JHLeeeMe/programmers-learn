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
- ```Map(key1 -> value1, key2 -> value2, ...)``` or ```Map(Tuple2, ...)```
- 기본이 ```scala.collection.immutable.Map```
- Set과 마찬가지로 Map4 이후엔 ```HashMap```
- 키 중복 x, 순서 x
```scala
#!/usr/bin/env scala


object LearnScala {
  def main(args: Array[String]): Unit = {
    // 1. Map[String, Int]
    val map1 = Map("one" -> 1, "two" -> 2, "three" -> 3)
    println(map1)  // Map(one -> 1, two -> 2, three -> 3)

    // Map[Any, Any]
    val map2 = Map(1 -> "one", "2" -> 2.0, "three" -> false)

    // 2. 중복된 키가 있으면 마지막 값 사용
    println(Map('a' -> 1, 'a' -> 2))  // Map(a -> 2)

    // 3. 키가 없으면 NoSuchElementException 발생
    // val fourExists = map1("four")  ====> exception
    // 아래는 체크방법
    println(fourExists.get("four").isDefined)  // false

    // 4. '++' 연산자로 Map을 concat가능, 키가 중복되면 마지막 값으로 결정
    val concatenated = map1 ++ map2
    println(concatenated)  // Map(three -> false, 1 -> one, two -> 2, 2 -> 2.0, one -> 1)

    // 5. find (List, Set과 같은 형태)
    val personMap = Map(("솔라",1), ("문별",2), ("휘인",3))
    
    //def findByName(name: String) = personMap.find(_._1 == name).getOrElse(("화사", 4))  // name이 있으면 튜플 리턴
    def findByName(name: String) = personMap.getOrElse(name, 4)  // name key가 value 리턴, 없으면 4 리턴

    val findSolar = findByName("솔라")  // return값은  
    val findSun = findByName("태양")    //   Int이다.

    println(findSolar, findSun)  // 1, 4
  }
}
```

# Array/List/Set/Map의 타입
- 엘러먼트들은 어떤 타입이든 사용 가능.
- 최종 타입 최상위 타입으로 결정
```scala
#!/usr/bin/env scala


object LearnScala {
  class Animal()
  class Dog() extends Animal()

  def main(args: Array[String]): Unit = {
    // Array
    // val array: Array[Dog] = Array(new Animal(), new Dog())  =====> error
    val array: Array[Animal] = Array(new Animal(), new Dog())

    // List
    val list: List[Animal] = List(new Animal(), new Dog())

    // Set
    val set: Set[Animal] = Set(new Animal(), new Dog())

    // Map
    val map: Map[String, Animal] = Map("Animal" -> new Animal(), "Dog" -> new Dog())
  }
}
```

# 변경할 수 있는(Mutable) Collection
- 스칼라는 immutable 권장, 그래서 기본이 immutable
- 필요한 경우 Mutable 사용 가능
- ArrayBuffer는 자바의 ```java.util.ArrayList```와 유사
- ListBuffer는 자바의 ```java.util.LinkedList```와 유사
- Mutable Collection을 사용할 때는 앞에 ```mutable```을 붙여야 됨.
  ```e.g. (mutable.ArrayBuffer, mutable.ListBuffer, mutable.Set, mutable.Map)```
```scala
#!/usr/bin/env scala


import scala.collection.mutable

object LearnScala {
  def main(args: Array[String]): Unit = {
    // 1. 배열로 구현되는 ArrayBuffer
    val arrayBuffer = mutable.ArrayBuffer(1, 2, 3)  // arrayBuffer: scala.collection.mutable.ArrayBuffer[Int] = ArrayBuffer(1, 2, 3)
    arrayBuffer += 4
    arrayBuffer -= 1
    arrayBuffer ++= List(5, 6, 7)
    println(arrayBuffer)  // ArrayBuffer(2, 3, 4, 5, 6, 7)

    // 2. Linked List로 구현되는 ListBuffer
    val listBuffer = mutable.ListBuffer("a", "b", "c")
    println(listBuffer)  // ListBuffer(a, b, c)

    // 3. Mutable Set
    val hashSet = mutable.Set(0.1, 0.2, 0.3)  // hashSet: scala.collection.mutable.Set[Double] = HashSet(0.3, 0.1, 0.2)
    hashSet ++= mutable.Set(5)
    println(hashSet)  // HashSet(0.3, 0.1, 0.2, 5.0)

    // 4. Mutable Map
    val hashMap = mutable.Map("one" -> 1, "two" -> 2)  // hashMap: scala.collection.mutable.Map[String, Int] = HashMap(one -> 1, two -> 2)
    hashMap ++= Map("five" -> 5, "six" -> 6)
    println(hashMap)  // HashMap(one -> 1, six -> 6, five -> 5, two -> 2)
  }
}
```

# 변경할 수 없는(Immutable) Collection에서의 var와 val
- Immutable Collection이 ```var```로 선언된 경우 ```+=```나 ```-=```를 사용가능
- collection자체는 immutable이므로 새로운 collection이 만들어져 ```var```변수에 할당되는 것
- Mutable Collection의경우는 ```+=```, ```-=```연산자가 메서드로 작동
```scala
#!/usr/bin/env scala

import scala.collection.mutable

object LearnScala {
  def main(args: Array[String]): Unit = {
    // 1. Immutable Collection이 var에 할당
    var immutableSet = Set(1, 2, 3)

    // 새로운 Set을 만들어 immutableSet에 할당
    immutableSet += 4
    //same As
    //immutableSet = immutableSet + 4
    println(immutableSet)  // Set(1, 2, 3, 4)

    // 2. Mutable Collection
    val mutableSet = mutable.Set(1, 2, 3)
    mutableSet += 4
    //same As
    // mutable.+=(4)
    println(mutableSet)  // HashSet(1, 2, 3, 4)
  }
}
```
